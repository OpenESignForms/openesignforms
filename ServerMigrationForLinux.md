#### Table of contents ####


# Introduction #

These are notes we maintain about server migrations under CentOS Linux. In general, we use migrations to a new server when we need a more powerful server to support ever increasing usage, or to do an operating system upgrade. We generally take that opportunity to also update the database, Java and Tomcat versions, though such components are often upgraded in place as well.

**NOTE: If you are not upgrading any application components, you only need to rebuild the server and configure the `root` level systems on the new server and then just copy over all files in the `esignforms` user account.**

# Create the new server #

Create a new server, generally using the latest version of CentOS (or Red Hat) Linux.

If the new server will use a new IP address when completed, be sure to remember to set the DNS PTR records for the new IP address to point to the server name, and then update the DNS A record after the migration is complete.

If the new server will be able to reuse the original IP address, you generally have to migrate using a new IP address, but when completed, shut down the original server and then reboot your new server using the original IP address (no DNS changes are required).

  1. Create the new server using the latest CentOS release. Note the IP address for use in data transfers, as well as root password, to make transfers using `scp` and `rsync` easier. Once the migration is complete, root logins and password-based logins are generally disabled.
  1. You may want to check the new server IP address to ensure it's not on any anti-SPAM lists if you are using a third-party data center.
  1. Follow the [basic Linux installation instructions](Installation#General_Linux_X64_server_setup_information.md) for the initial `root` steps, but generally don't limit SSH access until the migration is completed. Note that you will use the same hostname as the original server. You may also want to take this opportunity to use new passwords for the `root` and `esignforms` (your deployment user account).

# Pre-migration configuration for `root` #

Login to the old server as `root` to copy over files to the new server.

  1. `rsync -avz -e ssh bin esignforms mycrontab root@NEWIPADDR:.`
  1. Yozons-specific `/usr/local/bin/sp` (`chmod 755`) script for `ps`
  1. Yozons-specific `/etc/esfprofile` (`chmod 640`, `chown root.esignforms`) for offsite backup operations.
  1. Add `. /etc/esfprofile` to `.bash_profile`
  1. Add `rm -f ~/.bash_history` to `.bash_logout`
  1. Update `/etc/postfix/main.cf` to include the same entries for `mydomain`, `inet_interfaces`, `mynetworks_style`, `home_mailbox` and `virtual_alias_maps`.
  1. `rsync -avz -e ssh /etc/postfix/virtual_alias root@NEWIPADDR:/etc/postfix/`
  1. Update `/etc/dovecot/dovecot.conf` for `mail_location` and `mail_access_groups`.
  1. For each deployment, create the user account and password to handle in-bound email processing: `useradd DEPLOYNAME` and `passwd DEPLOYNAME`.
  1. Setup `/etc/sysconfig/iptables` like the old server, perhaps changing for the new IP address.

# Pre-migration configuration for `esignforms` #

Login to the old server as `esignforms` to copy over files to the new server.

  1. `rsync -avz -e ssh bashrc bin gpg.howto java mycrontab profile .s3cfg s3cmd.howto s3cmd-VER .ssh tomcat wkhtmltopdf_VER esignforms@NEWIPADDR:.`
  1. Add `. /etc/esfprofile`, `. ~/profile` and `. ~/bashrc` to `.bash_profile`
  1. Add `rm -f ~/.bash_history` to `.bash_logout`
  1. `mkdir backups`, `mkdir backups/fullbackup` and `mkdir backups/tomcat`
  1. `rsync -avz -e ssh postgresql --exclude 'postgresql/data92' esignforms@NEWIPADDR:.`
  1. `rsync -avz -e ssh deployments --exclude 'deployments/*/archive' --exclude 'deployments/*/current' esignforms@NEWIPADDR:.`

# Migrate latest database backups on old server #

Login to the old server as `esignforms`.

Stop the application with `yostop all`.

Turn off cron jobs: `crontab -r`  (do this for the `root` too)

Put the 'system down' configuration into place: `setWebappsDown`

Restart the now-down application: `yostart all`.  The database will be available for backups and the web apps will all report that the service is currently down.

Backup all deployment databases: `~/postgresql/bin/quickbackup`

Sync the backups you'd like to move to the new server using something like this:

  * `rsync -avz -e ssh --include='*/' --include='*.quickdump.YYYYMMDD.gz' --exclude='*' deployments esignforms@NEWIPADDR:.`

Stop the database on the old system: `yostop db`

# Restore databases on the new server #

Login to the new server as `esignforms`.

Ensure the database is running; if not: `yostart db`

  * Recreate the database for all deployments: `~/postgresql/ddl/recreate_db_only` passing in the parameters dbname and dbpassword: i.e. `./recreate_db_only testdb testdbuserpassword`
  * For each deployment, restore the database backup and run `analyze` on each database: `gunzip -c ~/deployments/DBNAME/archive/db/DBNAME.quickdump.YYYYMMDD.gz | pg_restore -v -d DBNAME`
  * Generally not required for a simple migraton, but for each deployment, run `~/postgresql/ddl/table_grants DBNAME` to ensure the correct permissions on tables and large objects.
  * For each deployment, run analyze on the new DB:
```
    psql DBNAME
    analyze;
    \q
```

# Activate new server #

Update your DNS for the new IP address.

While logged in as `esignforms`:
  1. Ensure the normal web.xml is in place: `setWebappsUp`
  1. Start Tomcat: `yostart web`
  1. Activate cron jobs: `crontab mycrontab`

While logged in as `root`:

  1. Activate the cron scripts: `crontab mycrontab`
  1. Install the init script: ./esignforms install
  1. Complete any remaining items not done earlier from the [basic Linux installation instructions](Installation#General_Linux_X64_server_setup_information.md).
This guide is a work in progress! Please visit https://code.google.com/p/openesignforms/wiki/InstallationUsingVaadin7 for full instructions.

# Introduction #

This guide walks you step-by-step to setting up the programming environment for developing Open eSignForms. Updated for Java 8.

This guide assumes you will be developing on a Microsoft Windows operating system.


# Setup the Environment #

## Apache Tomcat ##

  * We recommend using the latest stable version of Tomcat 7. We are using 7.0.53 for this guide.

  1. Download the windows zip file (not the installer) and extract it to a folder on your computer
## Eclipse IDE ##
  * We recommend using Eclipse IDE although these instructions should work for other IDE systems (eg. Netbeans) as well.
    1. [Download and Install Eclipse IDE for Java EE Developers](https://www.eclipse.org/downloads/). We are using Eclipse Kepler version 4.3.2 (the latest available at this time of writing).
    1. Unzip all files to C:\Program Files

### Configure the IDE ###

**Launch the software from the install directory
  1. C:\Program Files\eclipse\eclipse.exe
  1. Set Workspace to C:\project
  1. Check the box _use this as the default and do not ask again_**

## Java 8 ##
  * Install the latest version of the Java SE Development kit.
    1. Download Java SE Development Kit 8 (JDK 8) from Oracle's website.
    1. Download Java Cryptography Extension (JCE) Unlimited Strength Jurisdiction Policy Files
    1. Extract the two jar files into C:\Program Files\Java\jdk1.8.0\jre\lib\security folder, overwriting the files presently there.
    1. Extract the two jar files into C:\Program Files\Java\jre8\lib\security. Overwriting the files presently there.

### Install IvyDE plugin ###

  1. In Eclipse, Click the Help > Install New Software... menu
  1. In the box Work With: type _http://www.apache.org/dist/ant/ivyde/updatesite_ and click the **Add** button
  1. Give it the name _Apache Ivy Update Site_ and click **OK**.
  1. Select everything except the Apache IvyDE Resolve Visualizer and click **Next**
  1. Accept the license, click **Next** followed by **Finish** to complete the installation. (click OK if you receive a warning about installing unsigned software)
  1. Do NOT restart when prompted as we will install Vaadin next

### Install Vaadin ###
  * We will install the latest stable version, Vaadin 7 for the purpose of this guide.

  1. Click the Help > Install New Software... menu
  1. In the box Work With: type http://vaadin.com/eclipse
  1. Give it the name _Vaadin Update Site_ and click **OK**
  1. Select the **Vaadin Plug-in for Eclipse** and click Next
  1. Review the package and accept the license agreement by clicking Next and then Finish
  1. Restart the IDE when prompted after the installation is completed

## Cygwin ##

  * Perform a fresh install by running the setup program.
    1. When prompted, choose a download source "Install from Internet"
    1. We recommend leaving the default install directory **C:\cygwin64** if you are installing on a 64-bit system.
    1. Change the local package directory to **C:\packages**
    1. Choose a download site (we recommend staying away from .jp domain names or similar unless you live in that country)
    1. Click next on the select packages screen
    1. Let the install process resolve any dependencies and click **Next**

## PostgreSQL ##

  * Download the graphical installer
    1. Leave the default install drectory as C:\Program Files\PostgreSQL\9.3
    1. Leave the default data directory as C:\Program Files\PostgreSQL\9.3\data
    1. If you will only be developing Open eSignForms go ahead and type **esignforms** as the postgres database superuser password.
    1. Leave the default of **5432** as the port number the server should listen on
    1. Leave the default locale as **[locale](Default.md)**
    1. **Uncheck** the checkbox to "launch Stack Builder at exit".

# Check Out the Code #

![http://i58.tinypic.com/10ok6eh.jpg](http://i58.tinypic.com/10ok6eh.jpg)
![http://i60.tinypic.com/344cr55.jpg](http://i60.tinypic.com/344cr55.jpg)
![http://i62.tinypic.com/2i8dsts.jpg](http://i62.tinypic.com/2i8dsts.jpg)
# _Open eSignForms™_ by Yozons
[Open eSignForms™](https://open.esignforms.com) is the **_first free and open source_**, web contracting software application (on-premise) and SaaS (hosted). Yozons was the first to create an entirely web-based e-signature platform (no need for digital certificates, plugins, etc.) with its _Signed & Secured™_ service released in June 2001, with GE Capital as its first major customer just a few months later.

Open eSignForms can help your school, non-profit, medical facility, or business **go green by improving on your paperless activities**. Just use any of our free forms to help with secure document delivery with external parties and e-docs to storing files and scanned paperwork (fully encrypted) for your own secure access from anywhere in the world.

## License
### Open Source GNU AGPL
Versions up to 19.3.23 are licensed under the *GNU Affero General Public License ([AGPL](http://www.gnu.org/licenses/agpl.html))*.

** [References to third-party licenses used by Open eSignForms](https://open.esignforms.com/thirdPartySoftware.jsp).

### Commercial license
If the GNU AGPL does not work for you or you need a more current version of Open eSignForms (aka Yozons eSignForms), [commercial licenses](https://www.yozons.com/#pricing) are available that include legal protections, technical support, release management and optional hosting services on our reliable and secure global network of servers. Of course you are free to deploy on your own server as you see fit, regardless of license type, as we are one of the few vendors to offer an on-premise solution in addition to SaaS.  Open eSignForms is not suitable for military use, or for any high-security, high-risk, life-or-death purposes.

_**NON-PROFITS:** Yozons offers a free bump up in your preferred license size so you get more for less!_

## Background
Open eSignForms (most recently known as Yozons eSignForms) is driven by Yozons™, a long-time (since 2000) leader in web-based electronic signature software and web contracting for enterprises (including customers in the Fortune 500 down to one-person companies), giving you access to your contracts from any web-enabled device from anywhere in the world. The code is being built on over a decade of expertise garnered developing hundreds of previous electronic signature systems that are still in active use today with new customers daily. 

## Building blocks

It is developed using Java (and requires at least Java 8 as of version 16.10.8), with the user interface developed using Vaadin 7 on top of Google Web Toolkit (GWT). Of course, it's always changing, so refer to the [version history page](https://open.esignforms.com/demo/versionHistory.jsp) for details.  The last version released under the AGPL and running on Vaadin 7 is 19.3.23.

We normally deploy on Linux, but it runs fine under Windows (though our experience on Windows is mostly with developer PCs/laptops, not production servers). We even have deployed it on Windows Azure and Amazon EC3 instances.

## Standards based

Open eSignForms strives to use standardized technologies to achieve a high quality product without vendor lock-in.  Common technologies used include:
  * XML Digital Signatures, X.509 public keys, PKCS#8 private keys, SHA-512 with 4096-bit RSA keypairs
  * Documents are maintained in HTML format, with PDF exports.
  * 256-bit AES for data and document encryption, BCrypt for password hashing
  * HTTP, TLS/SSL, SMTP, IMAP, NTP, DNS
  * Java (JDK 12, JCE, JDBC, JSP/Servlets, JavaMail), HTML/XHTML, XML/DOM, CSS, JavaScript/JSON
  * SQL database
  * Linux and Windows
  * Full transaction exporting for long-term storage outside of the application.

## Yozons
[Yozons](https://www.yozons.com) invented the commonly used server-centric digital signature solutions so many electronic signature providers now use. Before, digital signatures were all based on users controlling a private key used to create them. In order to handle this in a large environment, a PKI was constructed to handle all of public keys that were needed to verify those digital signatures. Even PGP used this method, albeit without a centralized PKI. The web still uses this model for SSL (https), at least for most sites that don't want browser warnings popping up about unknown or expired digital certificates. Regardless, users needed encryption software to generate and validate, and users were responsible for keeping their private keys secure to only them, while distributing their public keys to others who had to have access to them to verify the digital signatures. The [Yozons invention](https://www.yozons.com/Patents/) got rid of all of that complexity and instead let the server do all of the key generation, key storage and encryption for its users.

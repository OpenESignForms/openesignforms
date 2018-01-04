# _Open eSignForms™_ by Yozons
[Open eSignForms™](https://open.esignforms.com) is the **_first free and open source_**, web contracting software application (on-premise) and SaaS (hosted). Yozons was the first to create an entirely web-based e-signature platform (no need for digital certificates, plugins, etc.) with its _Signed & Secured™_ service released in June 2001, with GE Capital as its first major customer just a few months later.

Open eSignForms can help your school, non-profit, medical facility, or business **go green by improving on your paperless activities**. Just use any of our free forms to help with secure document delivery with external parties and e-docs to storing files and scanned paperwork (fully encrypted) for your own secure access from anywhere in the world.

## License
### Open Source GNU AGPL
It is licensed under the *GNU Affero General Public License ([AGPL](http://www.gnu.org/licenses/agpl.html))*.

Versions may be [downloaded from here](https://drive.google.com/folderview?id=0B8C9MszRjx_yTnhna0N5VjkwRlU&usp=sharing).

** [References to third-party licenses used by Open eSignForms](http://open.esignforms.com/thirdPartySoftware.jsp).

### Commercial license
If the GNU AGPL does not work for you, [commercial licenses](http://www.yozons.com/Open-eSignForms/pricing.jsp) are available that include legal protections, technical support, release management and optional hosting services on our reliable and secure global network of servers. Of course you are free to deploy on your own server as you see fit, regardless of license type, as we are one of the few vendors to offer an on-premise solution in addition to SaaS.  Open eSignForms is not suitable for military use, or for any high-security, high-risk, life-or-death purposes.

_**NON-PROFITS:** Yozons offers a free bump up in your preferred license size so you get more for less!_

### Why does Yozons offer Open eSignForms as open source software (OSS)?
  * Open source code protects your investment should the product be discontinued, or the copyright owner goes out of business, etc. The code simply cannot be taken away on legal whims, product direction changes, the financial instability of the vendor, or if the vendor is acquired by a less interested entity.
  * Far too many people and companies are just "takers." These folks build their systems on top of open source software, often using lots of, if not mostly, open source software, but then keep their software private. Yozons prides itself on being a giver and supporter of the world-wide freedom community!
  * Open source code is inherently more reliable and trustworthy because more people can review the code for bugs, low quality, and backdoors, and those reviewers can report and/or fix any such issues themselves.
  * Open source code is inherently easier to check for intellectual property concerns because more people can review the code for the misuse of third-party licensed code, patents, copyright infringement, etc.
  * Opens source code lets you modify the code to suit your highly customized needs when the base platform cannot meet those needs.
  * Open source code leverages the power of others to debug and enhance the platform by providing their code so that all users benefit.

## Background
Open eSignForms is driven by Yozons™, a long-time (since 2000) leader in web-based electronic signature software and web contracting for enterprises (including customers in the Fortune 500 down to one-person companies), giving you access to your contracts from any web-enabled device from anywhere in the world. The code is being built on over a decade of expertise garnered developing hundreds of previous electronic signature systems that are still in active use today with new customers daily. 

## Help keep Open eSignForms world-class
All patches and code suggestions (via forums, emails and the like) that are accepted as part of Open eSignForms will become part of the common code base under the Yozons copyright so that all people can benefit unless your communications clearly label it as "Not a Contribution." All more substantial software and work contributed by a third party committer will be invited to electronically sign a [Contributor License Agreement (CLA)](http://open.esignforms.com/OpeneSignFormsIndividualCLA.html). This allows you to own any code you write and contribute, while ensuring that others are properly protected by granting them unfettered usage rights.

Let's ensure Open eSignForms has all of the features needed to satisfy myriad e-document and e-signing needs. Can open source really be better than those offered by DocuSign, Adobe Sign and eSignLive, to name a few proprietary, closed source alternatives?

## Building blocks

It is developed using Java 8 (and requires at least Java 8 as of version 16.10.8), with the user interface developed using Vaadin 7 on top of Google Web Toolkit (GWT). Of course, it's always changing, so refer to the [version history page](http://open.esignforms.com/demo/versionHistory.jsp) for details.

We normally deploy on Linux, but it runs fine under Windows (though our experience on Windows is mostly with developer PCs/laptops, not production servers). We even have deployed it on Windows Azure and Amazon EC3 instances.

## Standards based

Open eSignForms strives to use standardized technologies to achieve a high quality product without vendor lock-in.  Common technologies used include:
  * XML Digital Signatures, X.509 public keys, PKCS#8 private keys, SHA-512 with 4096-bit RSA keypairs
  * Documents are maintained in HTML format, with PDF exports.
  * 256-bit AES for data and document encryption, BCrypt for password hashing
  * HTTP, TLS/SSL, SMTP, IMAP, NTP, DNS
  * Java (JDK 8, JCE, JDBC, JSP/Servlets, JavaMail), HTML/XHTML, XML/DOM, CSS, JavaScript/JSON
  * SQL database
  * Linux and Windows
  * Full transaction exporting for long-term storage outside of the application.

## Yozons
[Yozons](http://www.yozons.com) invented the commonly used server-centric digital signature solutions so many electronic signature providers now use. Before, digital signatures were all based on users controlling a private key used to create them. In order to handle this in a large environment, a PKI was constructed to handle all of public keys that were needed to verify those digital signatures. Even PGP used this method, albeit without a centralized PKI. The web still uses this model for SSL (https), at least for most sites that don't want browser warnings popping up about unknown or expired digital certificates. Regardless, users needed encryption software to generate and validate, and users were responsible for keeping their private keys secure to only them, while distributing their public keys to others who had to have access to them to verify the digital signatures. The [Yozons invention](http://www.yozons.com/patents.jsp) got rid of all of that complexity and instead let the server do all of the key generation, key storage and encryption for its users.

## Demo
Check out the [online demo](https://open.esignforms.com/demo/). Unfortunately, a few lame adolescent types have made the demo mostly just a view-only system in terms of configuration, but you can certainly run the demo transactions and reports.

Just login using the values below, except without the spaces between the letters:

  U: ``` d e m o @ y o z o n s . c o m ```<br>
  P: ``` d e m o 2 0 1 8 ```


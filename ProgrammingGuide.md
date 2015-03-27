<table width='100%'><tr>
<td width='50%'><a href='http://open.esignforms.com'><img src='http://open.esignforms.com/images/OpenESignFormsLogo.gif' /></a></td>
<td width='50%' align='right'><a href='http://www.yozons.com'><img src='http://www.yozons.com/images/logoSmall.gif' /></a></td>
</tr></table>

<h1>Point & Click Programming Guide</h1>

**How-To Guides**
  * [Concepts, Tips & Tricks](HowToGuides.md) (Read first)
  * [User's Guide](UserGuide.md) (Read first)
  * [System Administrator's Guide](SystemAdminGuide.md)
  * **[Point & Click Programming Guide](ProgrammingGuide.md)** (this guide)
  * [Reports and Transaction Setup Guide](ReportsAndTransactionSetup.md)
  * [Point & Click Programming Integration API Guide](ProgrammingGuide_Integration_API.md)
  * [Point & Click Programming Tutorial](ProgrammingTutorial.md)

##### Table of contents #####


# Introduction #

All customization and programming of documents, workflows and emails is done through the web-based interface. **No programmers are needed.** For those who prefer to have professional help, though, Yozons has partnered with other companies that offer professional services to handle all of your needs, or perhaps to get you started so that you can then just make new versions as necessary going forward.

The joy, power and control of Open eSignForm's Point & Click Programming is unique. Those who have outgrown the limitations of mass-marketed, one-size-fits-all alternatives will be favorably impressed by our alternative. The most "tricky" part when building a document is to use notation like `'${firstName}'` in your document where you want an input field to enter someone's first name. Check out our [Programming Tutorial](ProgrammingTutorial.md) for a step-by-step learning approach.

Open eSignForms is based on over 10 years of developing hand-coded (in Java and JSP), custom electronic signature and electronic contracting solutions for thousands of customers across a wide range of verticals. It all started with GE Capital, then Schwab, Enterprise, Citrix, Pitney Bowes, several colleges and universities, and eventually a large number of financing companies, sales departments, HR departments, consulting and other small businesses.

Even Yozons found it hard to keep a large group of dedicated, talented software professionals who could meet the growing demand for our custom-built solutions, and we charge $125 to $250 per hour. The only solution was to stop training yet another programmer, and instead focus on making customized solutions a do-it-yourself option, with no programming experience required.

_Programming is much easier if you have a Full HD or better monitor to give you adequate "screen real estate" to edit the document, fields, etc._

<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

# Programming overview ![http://open.esignforms.com/images/HowToGuidesWiki/programmingIcon.png](http://open.esignforms.com/images/HowToGuidesWiki/programmingIcon.png) #

All programming is done by opening the Programming menu item, which includes links to the [Libraries](#Libraries.md), [Packages](#Packages.md), [Transaction Templates](#Transaction_Templates.md) and [Report Templates](#Report_Templates.md).

The general idea is that you create a library to hold all of your documents, images/logos, email templates, configurable properties and the like. If you have multiple independent companies or departments sharing the same system, you may want to have each work in their own libraries.

Then, once you have your documents ready, you create a package template that defines one or more documents that you want to process together. The package also specifies custom processing rules as well as defines the data fields from your documents that you allow to be included in custom reports.

Then, once your package is ready, you can create one or more transaction templates that will use the package. This gives you the opportunity to create multiple transactions using the same package, but with each specifying a distinct "branding library" that can override images/logos and property values, and each with distinct permissions.

And finally, you can build custom reports that specify which data fields to include for easy tracking, searching and control of transactions, as well as make available for download in Excel or CSV format.

<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

## Making a change to your document ##

This is a rough overview of the steps of modifying a working document, such as to fix typos, add more text, etc.  This also applies to images/logos, emails, and the like, but the changes are done to those objects, not the document objects.

  * Put yourself in **TEST: Development** mode using the selection list in the upper left corner. This ensure any transactions you start or reports you run will show only test transactions, not production ones.
  * Under Programming->Libraries choose the Library your documents are in.
  * Click on the Documents item to list your documents.
  * Click on the document to change.
  * Click on **Create next Test version** to make a new version that is not in production. Click **Save**.
  * Click on the page to update and make your changes and click **Save**.  Test as needed while in the document editor.
  * Run a test transaction -- not needed for simple typo fixes probably. If the tests are good, return to the document and then click the **Make Test version Production** to put it back into production.
  * Put yourself in **TEST: Like Production** mode, and test it again to ensure it's working as you want as this will create a test transaction using only production-level components.  If testing is good, then you are done and can just put yourself back in **PRODUCTION: Live** mode.  If there's an issue, you probably want to return to that document and click **Revert to Test** so it's not longer in production (and the prior version will be back in production until your fixes are done).

<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

# Libraries ![http://open.esignforms.com/images/HowToGuidesWiki/librariesIcon.png](http://open.esignforms.com/images/HowToGuidesWiki/librariesIcon.png) #

When you click on **Programming->Libraries** from the menu, you will see a list of libraries that are available to you.

Libraries provide a handy way to bundle documents and related configuration together across various projects, departments or even partner companies. A library may also play the role of a "branding library" as defined in a Transaction Template, which allows for "brand" overriding of selected components. The brand override works on all library components, except for documents, provided they have the same name.

Click on a library to view or configure it. To create a new library, you must select a template library or an existing library you have permission to access and click the **Create new empty library** button.

(_Note: To program the **contents** of a library, open the **[Programming->Libraries](#Library_programming.md)** arrow to reveal each library you are allowed to view or program and then click on the desired library to access its components._)

There is one special library, **ESF/Library/Template**, that provides a minimal, common set of documents, logos, emails and properties for a working system "out of the box." It includes platform-specific emails, too, such as those related to password issues and the default notification to a party to access a transaction. In general, you will not make any changes to this library.

Configuring a library is straightforward:

![http://open.esignforms.com/images/HowToGuidesWiki/libraryEdit.png](http://open.esignforms.com/images/HowToGuidesWiki/libraryEdit.png)

  * For an actively used library, ensure it is **Enabled**. You can mark it as **Disabled** if the library is no longer going to be used.
  * The **[PathName](HowToGuides#EsfNames_and_PathNames.md)** should identify the purpose or group that will control its contents.
  * The **Description** is a short phrase that describes the purpose of the library.
  * The **Default document style** is the [document style](#Document_styles.md) that new documents you create in the library will use. This helps ensure your documents have a common look. The **ESF/Library/Template** contains a default **ESF\_DefaultDocumentStyle** that can be used for a modern, fresh, easy to read look.
  * The **Comments** can be used to maintain notes regarding the library.
  * The **Permissions to access this library** are the standard List, View Details, Create, Update and Delete. Just select which groups should be allowed to do those operations. Note that this also applies to all of the components defined in the library, as they do not have independent permissions.  That is, all components in a library share the permissions defined for the library itself.

Click the **Create new empty library** to create a new, empty library. Currently, there is no "create like" for a library as we do not want to encourage putting the same documents in multiple libraries to avoid confusion.

Click the **[Export config](#Library_export_config.md)** button to download the configuration for one or more components defined in the library as an XML file. This file is suitable to be imported in another library, whether in the same deployment or in another.

Click the **[Import config](#Library_import_config.md)** button to upload the configuration previously exported and then select which components to add to the library.

<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

## Library export config ##

Click on the **Export config** button in a library to select which components you'd like to export (download to your computer):

![http://open.esignforms.com/images/HowToGuidesWiki/libraryExport.png](http://open.esignforms.com/images/HowToGuidesWiki/libraryExport.png)

By default, no components are automatically selected for export.

  * Select **Production only** to list only those components that are configured at the Production level.  Or select **Test version if present** to include components that may also be at the Test level, so that if you export, you will get the latest version regardless of it being at the Production or Test level.
  * Click on any number of **[Documents](#Documents.md)** to select the documents to export, including all configured fields, parties and images.
  * Click on any number of **[Button message sets](#Button_message_sets.md)** to select the button message sets to export.
  * Click on any number of **[Document styles](#Document_styles.md)** to select the document styles to export.
  * Click on any number of **[Drop downs](#Drop_downs.md)** to select the drop down lists to export.
  * Click on any number of **[Email templates](#Email_templates.md)** to select the email templates to export.
  * Click on any number of **[Files](#Files.md)** to select the files to export.
  * Click on any number of **[Image/logo](#Images_and_Logos.md)** to select the image files to export.
  * Click on any number of **[Property sets](#Property_sets.md)** to select the property sets to export.

Once you have selected the items to include in the exported file, click on the **Download/export selected configuration** button to save the XML data file containing the specified configuration to your computer.

<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

## Library import config ##

Click on the **Import config** button in a library to select a previously exported file to upload:

![http://open.esignforms.com/images/HowToGuidesWiki/libraryImportUploadFile.png](http://open.esignforms.com/images/HowToGuidesWiki/libraryImportUploadFile.png)

Once you have selected the file, click on the **Upload to import library configuration** button to upload the configuration from a previous export. Note that nothing is actually added to the library at this step.

You will be presented with the components that were contained in the file:

![http://open.esignforms.com/images/HowToGuidesWiki/libraryImportSelectComponents.png](http://open.esignforms.com/images/HowToGuidesWiki/libraryImportSelectComponents.png)

By default, all components are automatically selected for import. Unselect any components you do not want to import into the library at this time.

Check the **Overwrite existing Test versions?** box to allow any existing test versions of components with the same name to be overwritten. If you uncheck this box and your library already has a Test version component of the same name, the imported version will be skipped and not loaded into your library.

Note that all components will automatically be at the Test level (nothing is imported as Production-ready). If you already have a Production component with the same name, a new Test version will be created. Use the **Overwrite existing Test versions?** checkbox to control the behavior should your library already have a Test version of the same component.

Click the **Import selected objects into library** button once you are ready to import the configuration into your library.

# Library programming ![http://open.esignforms.com/images/HowToGuidesWiki/programmingLibraryIcon.png](http://open.esignforms.com/images/HowToGuidesWiki/programmingLibraryIcon.png) #

Click on one of the libraries listed when you open the **Programming->Libraries** arrow to access the contents of that library.

You will be presented with a page that lists all of the component types available:

![http://open.esignforms.com/images/HowToGuidesWiki/programmingLibrary.png](http://open.esignforms.com/images/HowToGuidesWiki/programmingLibrary.png)

Each component, except for documents, can be overridden using a "branding library" defined in a transaction template. For example, if you define an email or image logo in a library and a document in that library references them, by default it will find those components by name using the library where the document is defined. But if you also redefine those components using the same name in a different library, you can specify that library as a branding library in a transaction template so that at run-time, those transactions will reference those redefined components instead of the original. This allows a given document to carry different branding information without having to create duplicate documents and packages that only differ by the brand to be used.

Click on one of the following to program that type of component:

  * **[Documents](#Documents.md)** defines all documents (forms) and package+disclosure pages.
  * **[Button message sets](#Button_message_sets.md)** defines the button labels and related messages you want to use. The default button message set is defined in the **ESF/Library/Template**'s **ESF\_DefaultButtonMessage**.
  * **[Document styles](#Document_styles.md)** defines any special document styles you want to use besides the **ESF/Library/Template**'s default **ESF\_DefaultDocumentStyle**.
  * **[Drop downs](#Drop_downs.md)** define drop down lists, also known as select boxes, so your forms can allow a user to choose from a set of options. You can override drop downs in a branding library to change the values available.
  * **[Emails](#Email_templates.md)** define the emails that will be sent, such as emails inviting parties to complete documents or notifications sent to others when transactions are completed, customers have signed, etc. You can define both a regular text email as well as an optional HTML-version of that email should the recipient's email client allow the display of HTML email. You can override emails in a branding library to change the contents of emails.
  * **[Files](#Files.md)** define PDF, Word, HTML or other files that are linked in your documents for users to download "as is."
  * **[Images/Logos](#Images_and_Logos.md)** define the images and logos that you display in your documents. You may also define images that are document-specific in the document editor. While you may reference images from anywhere on the Web in your documents, it is not recommended as the URL for such images may change over time, or the image at that URL may change and cause layout or content issues in the future.  You can override images/logos in a branding library to use alternative images and logos.
  * **[Property sets](#Property_sets.md)** define small data elements that you can externalize from a document, such as company name, address, contact phone, fax numbers, etc. If you externalize these values, you can just change the property sets if their values change. You can override property sets in a branding library to change such values. It also supports using a different value when in Test or Test Like Production mode.
  * **[Fields](#Fields.md)** define commonly used fields in multiple documents so that you can choose them when creating a new field in a document and avoid having to reconfigure its options. It also helps keep common fields consistently named to lessen confusion (was it first\_name or FirstName or Name\_First?). This is not commonly used.
  * **[Parties](#Parties.md)** define commonly used parties in multiple documents so that your party names are consistent across documents. Also, if a given party name belongs to a group of users (like "Accounting" or "Payroll"), you can specify a **To Do Group** name that associates a [Group](SystemAdminGuide#Groups.md) of users who will be allowed to act in the party's role. You can override parties in a branding library to specify a different group of users to act as this party.
  * **Tips** just displays the programming tips page that is displayed when you first open a library for programming.

<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

## Documents ![http://open.esignforms.com/images/HowToGuidesWiki/documentsIcon.png](http://open.esignforms.com/images/HowToGuidesWiki/documentsIcon.png) ##

Click on **Documents** to show all documents in the selected library.

Creating documents is the focus of programming on Open eSignForms. Everything begins with a document.  Here's a document list along with the versions associated with the selected document (Selected document CustomDocumentForSignature, Version 2 in Test mode):

![http://open.esignforms.com/images/HowToGuidesWiki/documentVersionList.png](http://open.esignforms.com/images/HowToGuidesWiki/documentVersionList.png)

In the left side list are all of the documents, showing the current Production and Test versions, when present.  To filter the list of documents:
  * Enter part of the **Document EsfName** to search by name. It defaults to a "contains" search, but you can prefix with "^" for a "starts with" search. You can also specify to see only **Enabled** or **Disabled** documents.  Click the **Filtered** button to get a filtered list, or click **Show all** to list all documents.

Click on a document to view it along with all of its versions.

On the right side list are all of the versions of the selected document. Document versions are either Test (most recent if present), Production (most recent if no test version), or Old (prior Production versions).  By default, when you select a document, the most recent version will be selected. Only a Test version is available to be changed.

To create a new document and test version from scratch, click the **Create new** button.

When a document is selected, the document and version forms are displayed below:

![http://open.esignforms.com/images/HowToGuidesWiki/documentVersionEdit.png](http://open.esignforms.com/images/HowToGuidesWiki/documentVersionEdit.png)

**On the left side** is information about the document, regardless of version:
  * Click **Enabled** for the document to be actively available, or click **Disabled** to keep that document from appearing in other lists of active documents.
  * The **HTML file name spec** sets the file name for this document when it's exported or attached to an email. It can be a simple name like `Contract.html` or may contain field and property specifications so it's customized, such as `Contract for ${firstName} ${lastName}.html`.
  * The **[EsfName](HowToGuides#EsfNames_and_PathNames.md)** is the document's unique name in the library. Once you create a production version, you will no longer be able to change this name.
  * The **Display name** is the name shown to parties when they view this document.
  * The **Description** is a short description the document.
  * Use **Comments** to track any information you want regarding this document.

Click the **Save** button to save any changes to the document and currently selected version.

Click the **Cancel** button to discard any changes made and revert to view-only mode. You can click the **Edit** button to return to edit mode.

Click the **Create new like** button to create a new document, like the currently selected document and version. In general, you want to create a new VERSION of a document when you are making changes to an existing document such that the new version will be used in place of the older versions going forward.  You may want to create a new document LIKE an existing one if BOTH documents will be used at the same time, such as creating a state-specific version of an otherwise standard document.

**On the right side** is information about the selected version:
  * It includes a list of pages in the document. Many multi-page documents are implemented as a 1-page document because they are "web pages," meaning that the document can be very long with simple scrolling.  Click on a page to bring up the page editor. If there is more than one page, a **Delete** button will appear to allow you to delete a page. Click the **Add page** button to add a new blank page. You may drag and drop pages to re-order them. Multi-page documents are presented with all "Edit" or "Edit and review" pages first, and then once all pages are filled, a final review is shown that is composed of "Review" and "Edit and Review" pages concatenated together. Most people use multiple pages to implement a simple wizard so users can fill out a document in parts, and then review the complete document when it's all done.
  * The **Document style** is the [document style](#Document_styles.md) to be used for this document. We recommend you use as few different document styles as possible to keep a consistent look, and the built-in **ESF\_DefaultDocumentStyle** is a nice, modern look.
  * The **Orientation** specifies the intended page orientation as Portrait (taller than wide) or Landscape (wider than tall). Portrait is the default. It is currently only used for PDF generation as browsers have no such limitation/concern. If you select multiple documents to combine into a single PDF, if any document is defined as Landscape, then all documents in that PDF will be landscape.
  * The **E-Sign record location** specifies where the electronic signature process record will appear if the document is signed. Choose "Final own page" to put it on the last page, by itself (so if printed, it will appear on its own page). Choose "End of document" to just put it at the end of the document without inserting a page break; this is useful if your last page has space to include this extra information. Choose "Do not show" to suppress it entirely (not recommended).

If you are working on a Test version, click the **Make Test version Production** after you have tested the document and shown that it works as expected. You must make it Production in order to use it in production-level transactions. Click the **Delete** button to delete the Test version. If there is no Production version, this will also delete the Document definition as well as the version.

If you have selected a Production version and there is no existing Test version, click on the **Create next Test version** to create the next version of the document. While generally not recommended, if you need to make a quick tweak to a Production version (and no Test version exists), click on the **Revert to Test** button to put the current Production version back to Test mode, and if there is a previous Old version, it will become the Production version again. This should only be done if you are sure there are no users as they could receive run-time errors (if on reverting there is no new Production version) or version mismatches (since the prior Old version will be used as the new Production version). If you must revert, make your changes quickly and then put it back into production to reduce the chance of such errors occurring.

Click the **Test** button to view the document in the standalone document tester.

<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

### Document page editor ###

From the document version form, if you click on a page, the document page editor is displayed:

![http://open.esignforms.com/images/HowToGuidesWiki/documentPageEditor.png](http://open.esignforms.com/images/HowToGuidesWiki/documentPageEditor.png)

We use the [CKEditor](http://docs.cksource.com/CKEditor_3.x/Users_Guide) component for WYSIWYG document layout, which is shown on the left side.  The right side contains the list of Fields, Parties and Images defined within the document page.

_We recommend that you layout only line-by-line, and run the **Test** button to see how it renders frequently when you are learning the system. This will help you understand just what is happening and make it easier to detect problems as you add the next line._

On the left side editor:
  * The **Page [EsfName](HowToGuides#EsfNames_and_PathNames.md)** is the unique page name in this document.
  * The **Edit/Review mode** specifies how a given page will be used. By default, it's for both "edit" mode, which means parties can fill it out, and "review" mode, which is shown as the final step before submitting a completed document. Choose "Edit and review" if the page is to be filled out and included in the final review. Choose "Edit only" if it's just for collecting data, such as in wizard, but won't be used in the final review. Choose "Reivew only" if it's just for the final review and will otherwise not have any input required.
  * The **Assign new fields so party can update** drop down lists all defined parties for the document, or "-none-", so that as you are building a new document, if you select the party who will fill out the respective fields, when you click **Save**, all new fields will automatically be associated with that party. Don't worry if you forget as you can assign which fields each party can update by clicking on the Party in the right side list.
  * The **Add new** button ![http://open.esignforms.com/images/HowToGuidesWiki/addNewOptionButton.png](http://open.esignforms.com/images/HowToGuidesWiki/addNewOptionButton.png) will let you manually create a new field, party, file, image or drop down.
  * The **View default CSS** list may be useful to more advanced programmers who understand CSS (cascading style sheets). The styles shown when you click on the link are provided for all pages, so you can use these style class names as necessary. It may also be useful if you need to override any in your document (just redefine via the 'Source' mode and add `!important` to ensure your style class is used).
  * The (i) info button has various tips and useful information (cheatsheet) for defining fields in your document.

See below for [CKEditor tips](#CKEditor_tips.md).

Click the **Save** button to save changes to the page, fields, parties or images. You can also use CTRL-S in the editor to save.

Click the **Close** button to close the page editor.

Click the **Test**  button to test the page in the document-only tester, which shows you your document as it will appear for any of the defined parties.

Click the **Customize logic** button to add document-specific actions and data validations. It is very similar to the [customize logic configuration for a package](#Customize_logic.md) except that it only operates on the specified document and thus should generally only contain rules that are always true when using the document regardless of how it's packaged.

<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

### CKEditor tips ###

To use one of the editor's styles, highlight existing text to change, then click the **Styles** drop down and choose a new style.

To use one of the editor's text styles, highlight existing text to change, then click the second drop down and choose the appropriate look as shown in the drop down.

Most of the editor icons have a tooltip if you hover over it.

Select bold, italics, underlined, strike-through, subscript, superscript or remove formatting.

Select colored text or colored background for text (like a highlighting marker).

Click the **Font** drop down to change the font on the selected text.

Click the **Size** drop down to change the font size on the selected text.

Click one of the text alignment buttons for: left justified, centered, right justified, fully justified (both left and right justified).

Click the cut, copy, paste, paste as plain text or paste as Word to paste whatever is in your clipboard. If you are copying from a Word document, we recommend using the 'Paste as Word' button.

Click the Find or Find & Replace to look for text in the editor.

Click the arrows to undo or redo changes.

Click the numbered/ordered list or unordered list to make the highlighted text into a list.

Click the Outdent or Indent buttons to decrease or increase the paragraph indentation, and use the DIV button to add a <div> tag.<br>
<br>
Click the Table icon to add a table. This is a common tool for dealing with column data in your forms. If you drag the size of the table or its columns, the sizes will be fixed as you specify it in the editor.  But you can also set their sizes to percentage widths and the layout will expand and contract with the browser size.<br>
<br>
Click the Insert Horizontal Line button to add a line across the page.<br>
<br>
Click the Insert Page Break button to force a page break when the user prints the document from their browser.<br>
<br>
Click the Insert Special Character button to add one of the listed characters.<br>
<br>
Click the Image button to insert an image defined in the document, the document's library or from the ESF/Library/Template.<br>
<br>
Click the Link button to make a hyperlink. Click on the Browse button to make a link to a file you have uploaded in the document's library. Click the Unlink button to remove a hyperlink from selected text.<br>
<br>
Click the Source button, for advanced users, who want to see the HTML generated. You may enter HTML directly in this mode and then click it again to return to the WYSIWYG mode. In Source mode, you can also add javascript or style sections as necessary.<br>
<br>
Click the Show Blocks button to display the page in terms of blocks, indicating the type of tags used to create them.<br>
<br>
<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

<h3>Fields</h3>

On the right side is the <b>Fields</b> tab and list of fields:<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/fieldInDocumentList.png' />

This shows all fields defined in the document using the <code>${ }</code> notation. It shows the number of references as well as the field's type.<br>
<br>
Click on a field to change its configuration:<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/fieldEditorGeneral.png' />

By default, new fields are given the <b>General</b> type, meaning they are standard text input fields:<br>
<ul><li><b><a href='HowToGuides#EsfNames_and_PathNames.md'>EsfName</a></b> specifies the field's name, which must be unique in the document.<br>
</li><li>Use the <b>Set from library</b> drop down to select any pre-defined fields from the library. Note that using this will update all fields on the form.<br>
</li><li>Use the <b>Type</b> drop down to choose the correct type for this field:<br>
<ul><li><b>General</b> is a text input field for entering a single value, like a name.<br>
</li><li><b>Checkbox</b> is a traditional checkbox field, either checked or not.<br>
</li><li><b>Credit card #</b> is a text input field that expects a legal credit card number. This type currently supports Visa, MasterCard, American Express, Discover numbers.<br>
</li><li><b>Date</b> is a text input field that includes a calendar selector or lets the user enter the date directly.<br>
</li><li><b>Date+time</b> is a text input field that includes a calendar selector or lets the user enter the date directly, followed by drop downs to select the hour, minute, seconds and timezone.<br>
</li><li><b>Decimal</b> is a text input field that expects a valid decimal number, like 123.4. It differs from the Money type only in that it doesn't show a currency symbol.<br>
</li><li><b>Drop down list</b> lets you choose a drop down list defined in your library so that parties can select a valid value from the list.<br>
</li><li><b>Email address</b> is a text input field that expects a valid email address.<br>
</li><li><b>File confirm click</b> is a special way to select a file from the document or library that will track whether parties have clicked on the link to view/download it if the field is required for the party. You can also set this field to another File EsfName at runtime if the required file is not known when configured. For a given party, you may use one of the "Blank" condition checks to see if an optional file confirm click field has been clicked or not.<br>
</li><li><b>File upload</b> is a special field that allows files to be attached (or removed) when in edit mode, or listed and viewed when in display mode. When assigned to a party, that party will be able to upload/remove files. You can specify a <b>Limit # files</b> value to restrict the number of files that can be uploaded. All parties are required, by default, to click on these files before continuing. (See the custom logic action <a href='#Change_File_field_access_action.md'>Change File field access</a> to change this behavior for parties who are not uploading if you'd like to block their ability to view/download, or to make it optional that they view/download the files.) The value of this field is the number of files uploaded so you can use a standard number-based comparison to check how many files have been uploaded.<br>
</li><li><b>HTML editor</b> puts a CKEditor field in your document, allowing the party to enter rich text, or paste from Word, etc. We recommend you only provide this feature to parties who are part of your company.<br>
</li><li><b>Integer</b> is a text field that expects an integer/counting number value, such as -5 or 20. Decimal points are not allowed. This type also supposed an <b>Extra options</b> value to specify whether to show normal integers like 1, 2, 3, or to show the value as an ordinal number, like 1st, 2nd, 3rd.<br>
</li><li><b>Money</b> is a text input field that expects a valid amount of money to be entered, like 15.25 or $20. It differs from the Decimal type in that it displays a currency symbol rather than just the number.<br>
</li><li><b>Phone</b> is a text input field that expects a valid phone number. You can specify what the default country is for phone number so it can be properly interpreted and formatted.<br>
</li><li><b>Radio button</b> is a traditional radio button that is typically defined with other values and are put in a group so that only one of the radio buttons in the group can be selected at a time.<br>
</li><li><b>Radio button group</b> is a non-visual field type that actually holds the value of the selected radio button defined as part of the group.<br>
</li><li><b>Signature</b> is a text field stylized for the purpose of having the party type their name to indicate they are signing. It will also trigger the additional of the electronic signature process record for the party who signs.<br>
</li><li><b>SignatureDate</b> is a non-entry field associated with a Signature field by having the same name as the Signature field, but with "Date" added. So if you define a signature field as "CustomerSignature" you can have a date field added and automatically assigned with the actual signing date by defining a SignatureDate field named "CustomerSignatureDate" ("CustomerSignature" with "Date" added at the end).<br>
</li><li><b>SSN</b> is a text field suitable for the entry of US-based social security numbers. It can also be used to format as an employer identification number (EIN).<br>
</li><li><b>Text area</b> is a multi-line text field that allows for greater input by a user. It is generally used to enter plain text comments, additional contract terms, descriptions, free form mailing addresses, etc.<br>
</li><li><b>Zip code</b> is a text field suitable for the entry of US-based zip codes, either 5 or 9 digits.<br>
</li></ul></li><li>Use the <b>Align</b> drop down to change the alignment of the field. "Inherit" is commoly used.<br>
</li><li>Check the <b>Required</b> checkbox if the field is required.<br>
</li><li>Click the <b>Security options</b> list to add special options such as whether the field should support "Auto complete" or not (meaning that if the user has entered similar data elsewhere, the browser will offer up alternative choices, and if not checked, the browser will not offer suggestions); "Mask in data snapshot" is for sensitive data that you may store in your forms, but if the data is exported it must be masked; and "Copy value on tran clone" specifying whether this field's value can be copied if a new transaction is created from an existing transaction (for example, signature fields generally should not be copied since the new transaction should not assume they have typed to sign).<br>
</li><li>Enter the <b>Minimum length</b> this field may have in number of characters.<br>
</li><li>Enter the <b>Maximum length</b> this may have in number of characters.<br>
</li><li>Enter the <b>Width</b> and <b>Units</b> to specify how big the field should be. If your fields are defined in a table column, you may want to choose 100% to have it fill the available space. Or choose "Auto" in the Units (Width value is hidden) to have the field sized according to its natural size, which is useful for fields like checkboxes, drop downs, radio buttons, etc.<br>
</li><li>Check the <b>Resize display</b> field if you want the field to display in its natural size when in view/display mode (not in input/edit mode).<br>
</li><li>Check <b>Top</b>, <b>Bottom</b>, <b>Left</b> and/or <b>Right</b> to include borders around the field.<br>
</li><li>The <b>Initial value</b> specifies a fixed value or a field specification, like <code>${transaction:firstName}</code>, which is used to set the field's initial value when the transaction is started. Furthermore, the system will attempt to set the value again whenever a party retrieves a document and no value has yet been set so you can set it to a value from a prior document or even the current document. You generally cannot reference other fields in the document (since the order they are initialized is not defined), but you can set it to values posted when the transaction was started by an external process or a document field from a prior document or the current document when you know it's reference value is set. If the initial value field specification cannot be found and the <b>Display if empty value</b> option is enabled, then the field will be left blank rather than set to the missing field name.<br>
</li><li>The <b>Display if empty value</b> specifies a fixed value or a field specification, which is displayed for this field when the value is blank (null, spaces, empty string, etc.) To activate this, you need to check the box to its left.<br>
</li><li>The <b>Auto POST</b> checkbox allows you to submit all data on the form to the server when it's value changes. This is generally only done when linking two drop boxes such that the second drop box list is set dynamically based on the value of the first drop down list.<br>
</li><li>The <b>Dynamic drop down list name spec</b> appears for drop down list fields so that the actual drop down list used can be based on the value of other fields.<br>
</li><li>The <b>User tooltip</b> allows you to enter a tooltip that will display when the party hovers the mouse over the field on the document.<br>
</li><li>The <b>Input prompt</b> allows you to set a short tip that will appear inside the field when it's in input mode. Once any data is entered into the field, the input prompt will disappear. It is often used for a simple tip (and it is not recommended to be used in place of a label), such as put 'mm/dd/yyyy' in a date selection field, for example, or '(999) 555-5555' for a phone field, etc. Note that field has no value set until something is entered into the field and the input prompt disappears.<br>
</li><li>The <b>Input format</b> specifies the expected format for input into the field.<br>
</li><li>The <b>Display format</b> specifies the format to use when displaying the field (not in input/edit mode).</li></ul>

Each field can also be displayed with its label, automatically. By defining the label that goes with the field, when there is a data validation error, the field and label can be highlighted to help the party know what is wrong.  We recommend laying out your forms with the label in the "Above left" position to create a professional, consistent look that is clear to your users (although for checkbox and radio buttons, we recommend "Right").<br>
<br>
<ul><li>Select the <b>Label position</b> to use when allowing the label to be automatically shown with the field.  Select "None" to prevent the label from automatically appearing with the field. We recommend you do put the label somewhere nearby, though, using the syntax <code>${label:fieldName}</code>.<br>
</li><li>Check <b>Show input only</b> if the label should only be shown when the field is open for input (edit mode). This is mostly useful for a field inside a paragraph of text where the label is useful as a field prompt, but once populated the label no longer is necessary.<br>
</li><li>For <b>Label to show</b> enter the value to show as the field's label.<br>
</li><li>Choose the <b>Separator</b> drop down to define the separation of the label and the field as "None" (no separator), "Colon :" (put a colon and space between), or "Space" (put a space between).<br>
</li><li>Choose the <b>Size</b> of the label as "Small" (use a smaller font, which is typical when using a label position of "Above Left") or "Normal" (use the same font size for the label).</li></ul>

Click the <b>Ok</b> button to save your changes to the field template.<br>
<br>
Click the <b>Cancel</b> button to discard the changes made to the field template.<br>
<br>
Click the <b>Create new like</b> button to create a new field like this one. Note that you will want to update your document to reference the new field using <code>${ }</code> notation.<br>
<br>
Click the <b>Delete</b> button to delete the field. Note that you must also remove the associated <code>${ }</code> specification in the document because when you save the document page, all undefined fields will be re-created as a General type field.<br>
<br>
<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

<h3>Parties to document</h3>

On the right side is the <b>Parties</b> tab and list of parties who work on this document:<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/partyInDocumentList.png' />

This shows all parties defined in the document. You only need to define parties who are expected to fill out portions of the document.  You do not need to specify any parties who will only view the document.  You can drag to reorder the parties listed so that they appear in the expected order that the document will be completed.<br>
<br>
Use the special party ESF_reports_template to define special access for updating this document via the reports when the report is configured to allow such updating.<br>
<br>
Click on a party to change its configuration:<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/partyEditor.png' />

<ul><li><b><a href='HowToGuides#EsfNames_and_PathNames.md'>EsfName</a></b> is the unique name of a party to this document who is expected to enter data or sign.<br>
</li><li>Choose from the <b>Set name from library</b> drop down to select a pre-defined party in your library. This only changes the EsfName and Display name fields, but keeps them consistent across your documents. Consistent names will make it easier to configure packages when you add multiple documents in.<br>
</li><li>The <b>Display name</b> is the name of this party when displayed on a document or otherwise describing the party's step or role.<br>
</li><li>Select fields from <b>Fields party can view</b> and click the <b>>></b> button to convert them into <b>Fields party can update</b>.  The fields listed on the right side are the fields the party will be allowed to type into.  Use the <b><<</b> button to remove the selected fields from the update column if the party should not be allowed to update them.<br>
</li><li>Select fields from <b>Required fields party can update</b> and click the <b>>></b> button to make those fields defined with the <b>Required</b> checkbox optional for this party. Often a required field may not be known by an early party (like the person who starts the transaction and then sends it along for processing by another party), so while the field truly is required, it may be considered optional for another party.  Use the <b><<</b> button to remove the optional nature of that field for the party so it's required as defined in the field template.</li></ul>

Click the <b>Ok</b> button to save your changes to the party.<br>
<br>
Click the <b>Cancel</b> button to discard the changes made to the party.<br>
<br>
Click the <b>Create new like</b> button to create a new party like this one.<br>
<br>
Click the <b>Delete</b> button to delete the party.<br>
<br>
<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

<h3>Files linked in document</h3>

On the right side is the <b>Files</b> tab and list of files linked to in this document:<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/fileInDocumentList.png' />

This shows all files defined in the document. For files like HR policies that will likely appear in more than one document, we recommend you define those in the library. But many files are tied specifically to a single document, and this is the place to add those files.<br>
<br>
Click on a file to change its configuration:<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/fileEditor.png' />

<ul><li><b><a href='HowToGuides#EsfNames_and_PathNames.md'>EsfName</a></b> is the unique name of an file in this document.<br>
</li><li><b>Display name</b> is the auto-generated text shown in the link to this file.<br>
</li><li><b>Description</b> is a short description of the file.<br>
</li><li><b>Comments</b> is any other information you want to maintain about the file.</li></ul>

If the file has already been specified, click the <b>Replace file...</b> button to select a different file to use. When you first create a new file, use the <b>Set file</b> button to select the file to upload.<br>
<br>
Click on the <b>File link (view/download)</b> link to download the file.<br>
<br>
Click the <b>Ok</b> button to save your changes to the file.<br>
<br>
Click the <b>Cancel</b> button to discard the changes made to the file.<br>
<br>
Click the <b>Delete</b> button to delete the file.<br>
<br>
<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

<h3>Images in document</h3>

On the right side is the <b>Images</b> tab and list of images that are used only in this document:<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/imageInDocumentList.png' />

This shows all images defined in the document. For images like logos that will likely appear in more than one document, we recommend you define those in the library. But some images are tied specifically to a single document, and this is the place to add those images.<br>
<br>
Click on an image to change its configuration:<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/imageEditor.png' />

<ul><li><b><a href='HowToGuides#EsfNames_and_PathNames.md'>EsfName</a></b> is the unique name of an image in this document.<br>
</li><li>Check <b>Embed image in HTML</b> to include the image data directly in the HTML web page using a 'data URI'.  If not checked, the image will be served using a separate link/URL and request. Normally, this should not be checked, but it may be desirable when using image field overlays so the base document image is included in digitally signed HTML.<br>
</li><li><b>Description</b> is a short description of the image.<br>
</li><li><b>Comments</b> is any other information you want to maintain about the image.</li></ul>

If the image has already been specified, click the <b>Replace image file</b> button to select a different image to use. When you first create a new image, use the <b>Set image file</b> button to select the image to upload.<br>
<br>
Click on the <b>View full image</b> link to display the image "as is".<br>
<br>
<i>Note that the thumbnail image may appear to have a black background when the original images uses a transparent background.</i>

For images that have fields defined on top of them, select from the <b>Field in document</b> left-side list and move to the <b>Fields that overlay this image</b> right-side list.  If fields are defined to overlay the image, a <b><a href='#Position_overlay_fields.md'>Position overlay fields...</a></b> button will appear to allow you to set the top, left, width and height values relative to the image where the fields will be positioned.<br>
<br>
Click the <b>Ok</b> button to save your changes to the image.<br>
<br>
Click the <b>Cancel</b> button to discard the changes made to the image.<br>
<br>
Click the <b>Delete</b> button to delete the image.<br>
<br>
<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

<h3>Position overlay fields</h3>

If you have specified that some fields overlay your image, you will then have to specify the position (left and top) and size (width and height) on the image where the field is to be placed.<br>
<br>
Note that only fields can overlay the image. If you need to position property values or the like, you will need to set a field to the value.<br>
<br>
We recommend setting a label for field templates that overlay an image even if you don't show the label because it will be used in error messages for missing/invalid input.<br>
<br>
The top left corner of the image is considered to be a top position 0, left position 0.  The bottom right corner of the image essentially has a top position of the image's height, and the left position of the image's width.<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/imageOverlayFieldPosition.png' />

<ul><li>The <b>Field EsfName</b> is displayed to remind you which field is being positioned.<br>
</li><li>The <b>Display mode</b> is generally "Field" for a standard field overlay (similar to using ${field:XXXX} in the HTML document editor), or "Display only" to just show the field's value (similar to using ${out:XXXX}). You may also select "Field+Label" to position the field and it's label, but this is generally rare for image overlays.<br>
</li><li>Choose the <b>Background color</b> to use for the overlay field. By default, it'll just place the value on top of the image, which is the most typical need.  But you may select a color, such as "White", to make the field stand out more if the image underneath the field would otherwise make it hard to read.<br>
</li><li>Specify the <b>Left offset (px)</b> to specify how far in pixels from the left edge of the image where your field's upper left corner will be in.<br>
</li><li>Specify the <b>Top offset (px)</b> to specify how far in pixels from the top edge of the image where your field's upper left corner will be in.<br>
</li><li>Specify the <b>Width (px)</b> to specify how wide in pixels the field will occupy. Note that if you left, center or right align the field, it will be within this specified width.  Radio buttons and checkboxes do not support width or height.<br>
</li><li>Specify the <b>Height (px)</b> to specify how tall/high in pixels the field will occupy. You will find most text fits nicely in 20 or 22 pixel height. Radio buttons and checkboxes do not support width or height.</li></ul>

Note that the width and height create a "box" where the field will be placed.  If width specified is wider than than the field will naturally display, you likely want to change the field template to use 100% width so it fills the entire box's width.<br>
<br>
Click <b>Ok</b> to save your change, <b>Cancel</b> to abandon the change, and <b>Close</b> to dismiss the field overlay positioning window.<br>
<br>
<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

<h4>Microsoft Paint tip</h4>

There are lots of image processing tools that can help you with the positioning of overlay fields.  This is just a quick tip for the free/bundled Microsoft Paint program.<br>
<br>
Using Paint's "Select" tool, draw a box on the image where a field should be positioned.  Then note the left and top position, as well as the width and height of the box you drew.<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/MSPaintFieldPositionTip.png' />

Above, we have used the "Select" tool to draw an area in the "Signature of U.S. person" field. At the bottom of Paint, it shows the left position offset of 151 and the top offset of 748.  Next to it is the width of 380 and the height of 25.<br>
<br>
<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

<h3>Drop downs in document</h3>

On the right side is the <b>Drop downs</b> tab and list of drop downs used only in this document:<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/dropDownsInDocumentList.png' />

This shows all drop downs defined in the document. For drop downs that will likely appear in more than one document, we recommend you define those in the library. But many drop downs are tied specifically to a single document, and this is the place to add them.<br>
<br>
Click on a drop down to change its configuration:<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/dropDownEditor.png' />

<ul><li><b><a href='HowToGuides#EsfNames_and_PathNames.md'>EsfName</a></b> is the unique name of a drop down in this document.<br>
</li><li><b>Description</b> is a short description of the drop down.<br>
</li><li><b>Comments</b> is any other information you want to maintain about the drop down.<br>
</li><li>Check Allow Multi-Selections if the drop down should allow the user to select more than one value from the list.</li></ul>

A drop down can have one or more options specified, with the <b>label</b> being the value that is shown to the user in the drop down list, and the <b>value</b> is what is stored in the field that uses this list. Click the <b>Add option</b> button to add a new row. Click on a row and then the <b>Remove selected option</b> to delete a row. And finally you can drag each entry to change the order it will appear.<br>
<br>
Click the <b>Ok</b> button to save your changes to the drop down.<br>
<br>
Click the <b>Cancel</b> button to discard the changes made to the drop down.<br>
<br>
Click the <b>Delete</b> button to delete the drop down.<br>
<br>
<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

<h3>Document page editor cheatsheet</h3>

We recommend that when you want to build a new document, start from the top, lay out the first line, test, then lay out the second line, test, etc. This will make it easier to spot layout errors before too much is built.<br>
<br>
Next, add in your fields using the generic <code>${fieldName}</code> syntax inside the document. For each such <code>${ }</code> specified, a general purpose field will automatically be created for you. Just lay out all of the fields and do not worry about which party will manipulate which field.<br>
<br>
Once your testing shows the document layout working as expected, with general fields, you can then use the 'Fields in document' tab to update their types as necessary. At this stage, you can also define the parties who will fill out the document and assign the fields to the respective parties.<br>
<br>
<h4>Coding conventions</h4>
<code>${fieldName}</code> specifies a document field called 'fieldName'. Examples include <code>${firstName}</code>, <code>${streetAddress}</code>, <code>${SSN}</code> etc.  We recommend that each document have a field for each variable element so it will work more easily when packaged with other documents.  However, a document may reference a field (display-only value) from another document using the notation: <code>${documentName.fieldName}</code>.  <code>${fieldName}</code> is equivalent to <code>${fieldlabel:fieldName}</code>, with the former preferred as it's easier to type.<br>
<br>
If the <code>documentName</code> prefix portion is set to the literal 'document' it is interpretted as the "current document" which is the same as not using the <code>documentName</code> at all.  Use the prefix 'transaction' to access data from the transaction data, including startup data and to access related fields from the transaction (id, displayname, user.<b>fields, etc.).</b>

The names are used as programming variables and thus have are limited to 50 characters in length, must begin with a letter, and then can contain numbers, uppercase or lowercase letters and the underscore (<code>_</code>).  So <code>firstName</code> and <code>First_Name</code> are valid, while <code>First name</code> and <code>1stName</code> and <code>first-name</code> are not.<br>
<br>
If a given field appears in multiple locations in a document, only one should be used for input with the standard field notation.  The other references to the field, where it's only displayed, should use:<br>
<ul><li><code>${out:fieldName}</code> will show the field 'fieldName' for display-only. It also can be used to make a field use the output format specification defined in its field template rather than use its default format.</li></ul>

While fields are often shown together with a label, you can specify these be shown individually using the notation:<br>
<ul><li><code>${label:fieldName}</code> will show the label configured for the field 'fieldName'.<br>
</li><li><code>${field:fieldName}</code> will show just the field 'fieldName' without any configured label.</li></ul>

If you select a file using the Editor's link feature, the file link will appear in the document while editing. However, you may also use this notation to specify a configured file:<br>
<ul><li><code>${file:FileName}</code> will insert a link to the file named 'FileName' in that location.</li></ul>

If you select an image using the Editor's image feature, the image will appear in the document while editing. However, you may also use this notation to specify a configured image:<br>
<ul><li><code>${image:ImageName}</code> will insert the image named 'ImageName' in that location.</li></ul>

To insert the value of a configured property, you may use this notation:<br>
<ul><li><code>${property:PropertySetName.PropertyName}</code> will insert the value of 'PropertyName' as configured in the property set named 'PropertySetName'.<br>
</li><li><code>${htmlproperty:PropertySetName.PropertyName}</code> will insert the value of 'PropertyName' as configured in the property set named 'PropertySetName' as if the value were valid HTML (no escaping special characters to HTML entities).</li></ul>

<h4>Built-in fields used in documents</h4>
<ul><li><code>${document:esfname}</code> is replaced by the document's configured name.<br>
</li><li><code>${document:displayname}</code> is replaced by the document's display name.<br>
</li><li><code>${document:id}</code> is replaced by the document's unique id.<br>
</li><li><code>${document:version}</code> is replaced by the document's version number.<br>
</li><li><code>${document:version.id}</code> is replaced by the document version's unique id.<br>
</li><li><code>${document:page.esfname}</code> is replaced by the document version page's name.<br>
</li><li><code>${document:page.id}</code> is replaced by the document version page's unique id.<br>
</li><li><code>${document:page.number}</code> is replaced by the document versions page's number.<br>
</li><li><code>${document:party.esfname}</code> is replaced by the party's name.<br>
</li><li><code>${document:party.displayname}</code> is replaced by the party's display name.<br>
</li><li><code>${document:package.pathname}</code> is replaced by the package's path name.<br>
</li><li><code>${document:package.version}</code> is replaced by the package's version number.<br>
</li><li><code>${document:package.id}</code> is replaced by the package's unique id.<br>
</li><li><code>${document:package.version.id}</code> is replaced by the package version's unique id.</li></ul>

<h4>Built-in fields to reference from the transaction and startup data</h4>
<ul><li><code>${transaction:id}</code> is replaced by the transaction's unique id.<br>
</li><li><code>${transaction:pathname}</code> is replaced by the transaction template's path name.<br>
</li><li><code>${transaction:displayname}</code> is replaced by the transaction template's display name.<br>
</li><li><code>${transaction:ESF_Start_Timestamp}</code> is replaced by the date-time it was created.<br>
</li><li><code>${transaction:ESF_Started_API_Mode}</code> is true if the transaction was started using the API mode (from an automated start rather than a user). It is false otherwise.<br>
</li><li><code>${transaction:ESF_Started_By_User_Id}</code> is replaced by the user id of the person who started this transaction if it was started by a logged in user.<br>
</li><li><code>${transaction:ESF_Started_By_User_Email}</code> is replaced by the email address of the person who started this transaction if it was started by a logged in user.<br>
</li><li><code>${transaction:ESF_Started_By_User_Email_Address}</code> is replaced by the full email display name and email address of the person who started this transaction if it was started by a logged in user.<br>
</li><li><code>${transaction:ESF_Started_By_User_Personal_Name}</code> is replaced by the first/personal name of the person who started this transaction if it was started by a logged in user.<br>
</li><li><code>${transaction:ESF_Started_By_User_Family_Name}</code> is replaced by the last/family name of the person who started this transaction if it was started by a logged in user.<br>
</li><li><code>${transaction:ESF_Started_By_User_Employee_ID}</code> is replaced by the employee id of the person who started this transaction if it was started by a logged in user and this optional field has been set.<br>
</li><li><code>${transaction:ESF_Started_By_User_Job_Title}</code> is replaced by the job title of the person who started this transaction if it was started by a logged in user and this optional field has been set.<br>
</li><li><code>${transaction:ESF_Started_By_User_Location}</code> is replaced by the location of the person who started this transaction if it was started by a logged in user and this optional field has been set.<br>
</li><li><code>${transaction:ESF_Started_By_User_Department}</code> is replaced by the department of the person who started this transaction if it was started by a logged in user and this optional field has been set.<br>
</li><li><code>${transaction:ESF_Started_By_User_Phone_Number}</code> is replaced by the phone number of the person who started this transaction if it was started by a logged in user and this optional field has been set.<br>
</li><li><code>${transaction:paramName}</code> is replaced by the value of the named parameter passed at startup (X prefix is needed if original param started with a number; '-', '/' or '.' replaced by '<code>_</code>').<br>
</li><li><code>${transaction:ESF_Request_Header_headerName}</code> is replaced by the value of the named header passed at startup ('-', '/' or '.' replaced by '<code>_</code>').<br>
</li><li><code>${transaction:ESF_Request_Method}</code> is replaced by 'GET' or 'POST' based on type of original startup HTTP request.<br>
</li><li><code>${transaction:ESF_Request_ContentType}</code> is replaced by HTTP request's mime-type/content-type when specified.<br>
</li><li><code>${transaction:ESF_Request_RequestURL}</code> is replaced by HTTP request's original URL.<br>
</li><li><code>${transaction:ESF_Request_QueryString}</code> is replaced by HTTP request's query string portion of the URL.<br>
</li><li><code>${transaction:ESF_Request_RemoteAddr}</code> is replaced by HTTP request's remote address (typically an IP address).<br>
</li><li><code>${transaction:user.id}</code> is replaced by the user id of the logged in user who is acting as the current party if it's a logged in user.<br>
</li><li><code>${transaction:user.email}</code> is replaced by the email address of the logged in user who is acting as the current party if it's a logged in user.<br>
</li><li><code>${transaction:user.email_address}</code> is replaced by the full email display name and email address of the logged in user who is acting as the current party if it's a logged in user.<br>
</li><li><code>${transaction:user.personal_name}</code> is replaced by the first/personal name of the logged in user who is acting as the current party if it's a logged in user.<br>
</li><li><code>${transaction:user.family_name}</code> is replaced by the last/family name of the logged in user who is acting as the current party if it's a logged in user.<br>
</li><li><code>${transaction:user.employee_id}</code> is replaced by the employee id of the logged in user who is acting as the current party if it's a logged in user and this optional field has been set.<br>
</li><li><code>${transaction:user.job_title}</code> is replaced by the job title of the logged in user who is acting as the current party if it's a logged in user and this optional field has been set.<br>
</li><li><code>${transaction:user.location}</code> is replaced by the location of the logged in user who is acting as the current party if it's a logged in user and this optional field has been set.<br>
</li><li><code>${transaction:user.department}</code> is replaced by the department of the logged in user who is acting as the current party if it's a logged in user and this optional field has been set.<br>
</li><li><code>${transaction:user.phone_number}</code> is replaced by the phone number of the logged in user who is acting as the current party if it's a logged in user and this optional field has been set.</li></ul>

<h4>Built-in fields used in Package documents</h4>
<ul><li><code>${transaction:documents.todo}</code> specifies where the generated list of documents the specified party has access to are listed.</li></ul>

<h4>Built-in fields used in Email notifications configuration</h4>
<ul><li><code>${LINK}</code> specifies where the generated HTTP Link or URL will be placed in the email notification.<br>
</li><li><code>${EMAIL}</code> specifies where the party's address will be placed in the email notification, TO/CC/BCC, and/or subject.<br>
</li><li>Tip: Use <code>${out:DocumentName.FieldName}</code> instead of just <code>${DocumentName.FieldName}</code> in email text if you need the output formatting specification for the field as defined in that document.</li></ul>

<h4>Built-in fields used in password-related e-mail configuration for users</h4>
<ul><li><code>${LINK}</code> specifies where the generated HTTP Link or URL will be placed in the email notification.<br>
</li><li><code>${NAME}</code> specifies where the user's display name will be placed in the email notification and/or subject.<br>
</li><li><code>${EMAIL}</code> specifies where the user's address will be placed in the email notification, TO/CC/BCC, and/or subject.</li></ul>

<h4>Other built-in operators</h4>
<ul><li><code>${serial:SerialName}</code> is replaced by the next serial number defined with the name 'SerialName'. Numbers for test and production transactions are maintained separately. This generally should only be used to set another field value as it will return a new value every time it is referenced (i.e. not to be used directly in your document layout).</li></ul>

<h4>Field specifications</h4>

Various configuration fields allow for the specification of field specifications, which are basically the same as the field accesses above, but can be a literal or combination of other fields.<br>
<br>
For example, these are valid field specifications:<br>
<ul><li><code>this literal string</code> - This literal-only field specification simply is "expanded" to the same literal string: <b>this literal string</b>
</li><li><code>${transaction.id}</code> - This field-only specification expands to the ID of the current transaction, such as: <b>6ae1f380-8184-4a0a-ad0a-e3597d968462</b>
</li><li><code>StoresIn${state}</code> - This combines a literal <b>StoresIn</b> with the current document field <b>state</b>, assuming the state of Washington would result in something like: <b>StoresInWA</b>
</li><li><code>${firstName} ${lastName}</code> - This combines the field <b>firstName</b> with a space literal and another field <b>lastName</b> to create a full name, resulting in something like: <b>Steven Gates</b></li></ul>

Most fields that supporting entering such a field spec will show <code>${}</code> on the right side.<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/FieldSpecLookupTextField.png' />

Click on the <code>${}</code> to open the field spec lookup tool:<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/FieldSpecLookup.png' />

<ul><li>Click <b>Field spec type</b> to choose if you are looking for a field defined in a document, a property in a property set (regular or HTML properties), serial generator or one of the built-in fields for a document or transaction.<br>
</li><li>Select <b>In library</b> to select the library, when appropriate.<br>
</li><li>Select <b>In document</b> to select the document, when appropriate.<br>
</li><li>Select <b>Choose field</b> to select a field in a document, when appropriate.</li></ul>

Note that the <b>Field spec to copy/use</b> will hold the field specification string you can copy and paste as needed, or click the <b>Append</b> button to add it to the text field you clicked the <code>${}</code> icon in.<br>
<br>
<h4>Links to advanced configuration options</h4>
There are a few data types that allow for customization using Java's built in capabilities, but they are a bit technical. For advanced folks who need them, here are some useful links to documentation that describe these more.<br>
<br>
For Date, use <a href='http://docs.oracle.com/javase/6/docs/api/java/text/SimpleDateFormat.html'>SimpleDateFormat</a> specifications<br>
<br>
For Decimal and Money and even Integer, use <a href='http://docs.oracle.com/javase/6/docs/api/java/text/DecimalFormat.html'>DecimalFormat</a> specifications<br>
<br>
For General, use regular expression <a href='http://docs.oracle.com/javase/6/docs/api/java/util/regex/Pattern.html'>Pattern</a> specifications<br>
<br>
<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

<h3>Customize logic on a document</h3>

Customizing logic for a given document is very similar to customizing logic in a package except that it only applies to the document. It also operates on a restricted set of events and actions, though it can operate on page-level events which are not available to the package.<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/documentPageEditorCustomLogic.png' />

This is the best place to put document-specific extra data validations. Just select the <b>Party review document</b> event and use <b>Show error/message</b> actions with appropriate conditions to detect invalid form data.<br>
<br>
<ul><li>In <b>When event(s) occur</b> select at least one type of event that describes when you'd like the associated actions to run. You can choose from:<br>
<ul><li><b>Party retrieved document</b> occurs when a party first retrieves a document.<br>
</li><li><b>Party completed page</b> occurs when a party clicks the Continue button on a given page in a document. It is used primarily for custom validations as a user goes from page to page in a multi-page document. The party cannot continue to the next page if any action produces an error or warning message.<br>
</li><li><b>Party review document</b> occurs when a party has filled out the form or is signing and clicks the review button. The party cannot continue to review the completed document if any action produces an error or warning message.<br>
</li><li><b>Party completed document</b> occurs when a party completes a given document. The party cannot complete the document if any action produces an error or warning message.<br>
</li><li><b>Party view completed document</b> occurs when a party views a document that has already been completed.<br>
</li><li><b>Party saved document</b> occurs when a party clicks the 'Save' button, such as updating a document via the ESF_reports_access party when accessing the transaction from a report.<br>
</li></ul></li><li>In <b>Limit only to pages (optional)</b> check any pages where the actions should only fire when the selected event(s) occur, but also only when the specified page is being processed. If you do not select any, then it will not matter which page is involved.<br>
</li><li>In <b>Limit only to parties (optional)</b> check any parties if the actions should only fire when the selected event(s) occur, but also only when the specified party is processing the document. If you do no select any, then it will not matter which party is involved.<br>
</li><li>In <b>Actions</b> you can drag to re-order existing actions or click the <b>Delete</b> button to remove it.<br>
</li><li>Click the <b>Add action</b> button to add the actions you'd like to occur when the specified event arises, possibly limited based on the documents and parties selected.<br>
<ul><li>Choose <b>Set field action</b> to change any field values in your documents.<br>
</li><li>Choose <b>Calculate field value</b> to calculate a value (add, subtract, multiply, divide).<br>
</li><li>Choose <b>Calculate date value</b> to calculate a date by adding a positive (future) or negative (past) number of days, weeks, months or years.<br>
</li><li>Choose <b>Calculate monthly payment</b> to calculate a monthly payment amount based on the loan amount, term in months, and interest rate (APR).<br>
</li><li>Choose <b>Show error/message</b> to display a message or report an error to the user (mostly used during the <b>Party review document</b> and <b>Party completed page</b> events).<br>
</li><li>Choose <b>Change File field access</b> to specify block or make optional the need for a party to view/download the files associated with this field. Of course, if the party is supposed to upload files, this has no bearing.</li></ul></li></ul>

See <a href='#Conditional_actions.md'>conditional actions in a package</a> for details on conditions which are the same for package-level and document-level custom logic.<br>
<br>
<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

<h3>Package+disclosure documents</h3>

There is a special type of document that plays the role of a welcome message, the E-Sign Disclosure (required by law for consumers) and often contains the list of documents contained in the package for a given party.<br>
<br>
Since the list of documents for a given party are variable, you can include <code>${transaction:documents.todo}</code> in the package+disclosure document and it will automatically show the correct list of documents and their status for the party.<br>
<br>
The <b>ESF/Library/Template</b> contains a document just for this purpose called <b>StandardPackageDisclosures</b>.<br>
<br>
It's contents is some like the following:<br>
<br>
<pre><code>${image:Logo}<br>
<br>
Welcome to our electronic signature service.<br>
<br>
Please note that your continued use of this service constitutes your agreement to use electronic signatures in lieu of a paper document with a traditional hand-written signature. Electronic signatures are legally recognized throughout the United States. Your electronic signature will take place when you type your name and/or initials into the marked areas on the subsequent document(s) and then you click both the Review and Submit buttons on each document to indicate your agreement and/or authorization.<br>
<br>
You also certify that these documents are intended for you and that you are authorized to sign the documents. If you have received these by mistake, please do not continue and email us or call ${property:MyCompany.CustomerSupportPhone} to report our error.<br>
<br>
If you do not wish to sign these documents electronically, please contact us and do not continue with this process. However, we expect that you will prefer this free, easy-to-use, fast and environmentally sound option.<br>
<br>
Document(s) for your review:<br>
${transaction:documents.todo}<br>
</code></pre>

You are free to create your own documents with alternative welcome messages, E-Sign Disclosures and/or layout for this purpose. Just specify your package+disclosure document in the <a href='#Packages.md'>Package configuration</a>.<br>
<br>
<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

<h3>Advanced programming of a document</h3>

Not everything can be done with point & click programming. Here are a few tips that can be used when CKEditor is in <b>Source</b> mode.<br>
<br>
<h4>Style sheets</h4>
You can add your own styles just by including a standard HTML style tag at the top of your document:<br>
<br>
<code>&lt;style type="text/css"&gt;</code>

<i>put your custom styles here</i>

<code>&lt;/style&gt;</code>

<h4><code>JavaScript</code></h4>
You can add your own javascript just by including a standard HTML script tag at the top of your document:<br>
<br>
<code>&lt;script type="text/javascript"&gt;</code>

<i>put your custom JavaScript here</i>

<code>&lt;/script&gt;</code>

Such scripts run entirely in the user's browser and are only in effect if their browser is set to support JavaScript. We do not recommend using JavaScript to generate the document layout so that the captured HTML document on signing can be rendered correctly and consistently in the future. JavaScript generally should not be required for the document to work or render correctly.<br>
<br>
<h4>Java code snippets</h4>
You can add your custom Java programming to your document using JSP code syntax such as:<br>
<br>
<code>&lt;%</code> <i>put your custom java code here</i> <code>%&gt;</code>

Unlike JavaScript, this code runs on the server before the page is rendered to the user's browser.  Note that it is important to get the syntax right, especially with respect to open and close brackets for conditions and loops.<br>
<br>
Also, this syntax is only supported on a single line. The starting '<%' and ending '%>' must not span lines.<br>
<br>
This is particularly useful for optional HTML to display in a document. The variable <b>esf</b> can be used in your document custom Java code to access the server-side state. The Java interface for this object is shown below:<br>
<br>
<pre><code>public interface EsfDocumentPageInterface <br>
{<br>
	/**<br>
	 * @return true if the page is currently in EDIT mode, meaning the party is authorized to fill out fields on the form, the <br>
	 * stage before going into REVIEW mode.<br>
	 */<br>
    public boolean isEditMode();<br>
<br>
	/**<br>
	 * @return true if the page is currently in REVIEW mode, meaning the party is authorized to fill out fields on the form while in EDIT<br>
	 * mode but now is reviewing the page before submitting it.<br>
	 */<br>
    public boolean isReviewMode();<br>
    <br>
	/**<br>
	 * @return true if the page is currently in VIEW-ONLY mode, meaning the party is not authorized to fill out any fields, or is<br>
	 * returning after completing the document so no further changes can be made.<br>
	 */<br>
    public boolean isViewMode();<br>
<br>
	/**<br>
	 * @return true if the current party can only view the document and has no fields that can be updated/filled out on any<br>
	 * page in the document.<br>
	 */<br>
	public boolean isViewOnlyParty();<br>
	<br>
	/**<br>
	 * @return true if the current party is a view-only party that is not even defined as a party to the document. <br>
	 * This party cannot make any changes and is generally defined in the package but is not mapped to a specific document party.<br>
	 */<br>
	public boolean isViewOnlyNonParty();<br>
	<br>
	/**<br>
	 * @param docPartyName the String document party name to check (should be one of the document party names defined for the document)<br>
	 * @return true if the current party is the specified document party<br>
	 */<br>
	public boolean isParty(String docPartyName);<br>
	<br>
	/**<br>
	 * @return true if the current party is completed (all documents done)<br>
	 */<br>
	public boolean isPartyCompleted();<br>
	<br>
	/**<br>
	 * @return true if the current party is a logged in user<br>
	 */<br>
	public boolean isPartyLoggedIn();<br>
	<br>
	/**<br>
	 * @return true if the transaction is completed (all parties done)<br>
	 */<br>
	public boolean isTransactionCompleted();<br>
	<br>
	/**<br>
	 * @return true if the transaction is deleted (the current party has deleted the transaction)<br>
	 */<br>
	public boolean isTransactionDeleted();<br>
	<br>
	/**<br>
	 * @param packagePartyName the String package party name to check. This is mostly useful for the package+disclosure document that<br>
	 * does not have document parties defined at all.<br>
	 * @return true if the current party is the specified package party<br>
	 */<br>
	public boolean isPackageParty(String packagePartyName);<br>
	<br>
	/**<br>
	 * @param fieldSpec the String field specification, such as ${firstName} to get the field firstName from the document<br>
	 * @return the String value associated with the field spec. If the field spec is invalid (no such field can be found)<br>
	 * the field spec is returned without any values replacing it.<br>
	 */<br>
	public String getFieldSpecValue(String fieldSpec);<br>
<br>
	/**<br>
	 * @param fieldSpec the String field specification, such as ${firstName} to get the field firstName from the document<br>
	 * @return the String value associated with the field spec. If the field spec is not transformed at all, it returns an empty string.<br>
	 */<br>
	public String getFieldSpecValueOrBlankIfNotFound(String fieldSpec);<br>
<br>
	/**<br>
	 * @param v the String to check if it's blank (null, empty or just spaces)<br>
	 * @return true if 'v' is blank<br>
	 */<br>
	public boolean isBlank(String v);<br>
	/**<br>
	 * @param fieldSpec the String field specification, such as ${firstName} to get the field firstName from the document<br>
	 * @return true if the resulting field spec is blank (or has no other value we can transform to).  This is<br>
	 * essentially isBlank(getFieldSpecValueOrBlankIfNotFound(fieldSpec))<br>
	 */<br>
	public boolean isFieldSpecBlank(String fieldSpec);<br>
<br>
	/**<br>
	 * @param v the String to check if it's non-blank (not null, not empty and not just spaces)<br>
	 * @return true if 'v' is non-blank<br>
	 */<br>
	public boolean isNonBlank(String v);<br>
	/**<br>
	 * @param fieldSpec the String field specification, such as ${firstName} to get the field firstName from the document<br>
	 * @return true if the resulting field spec is nonblank.  This is essentially isNonBlank(getFieldSpecValueOrBlankIfNotFound(fieldSpec))<br>
	 */<br>
	public boolean isFieldSpecNonBlank(String fieldSpec);<br>
}<br>
</code></pre>

For example, to conditionally show some HTML based on whether the current page is in EDIT or REVIEW mode, you can use code like this:<br>
<br>
<code> &lt;% if ( esf.isEditMode() ) { %&gt;</code>

<i>put the optional HTML here to show only if the document is being filled out and/or signed</i>

<code> &lt;% } %&gt; </code>

Or<br>
<br>
<code> &lt;% if ( esf.isReviewMode() ) { %&gt;</code>

<i>put the optional HTML here to show only if the document is being reviewed before submitting</i>

<code> &lt;% } %&gt; </code>

<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

<h2>Button message sets <img src='http://open.esignforms.com/images/HowToGuidesWiki/buttonMessageSetIcon.png' /></h2>

Button messages provides a way to customize the button labels, tooltips on the buttons, messages shown to the party about how to use the button as well as other common messages shown to parties when processing a document. Open eSignForms comes with a built-in default button messages in the <b>ESF/Library/Template</b> library called <b>ESF_DefaultButtonMessage</b>.<br>
<br>
Also, the buttons added to your documents during run-time are placed in a P tag (<code>&lt;p class="buttons"&gt;</code>), so you can use your own CSS to control them. For example, by adding this to your document, you can center the buttons:<br>
<pre><code>&lt;style type="text/css"&gt;<br>
p.buttons { text-align: center; }<br>
&lt;/style&gt;<br>
</code></pre>

You may also find that you'd like the electronic signature process record to also be centered, so you could use this combination:<br>
<pre><code>&lt;style type="text/css"&gt;<br>
p.buttons { text-align: center; }<br>
div.signatureBlock { margin: 0 auto;}<br>
&lt;/style&gt;<br>
</code></pre>
The button message set is configured in each package. Note that a transaction template can specify a branding library such that if the same button message set name is defined in that library, then it will be selected at run time.<br>
<br>
Click on <b>Button message sets</b> to show all document styles in the selected library.<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/buttonMessageSet.png' />

<ul><li>Choose <b>Enabled</b> to allow the button message set to be used. If a button message set is no longer needed, click <b>Disable</b>.<br>
</li><li><b><a href='HowToGuides#EsfNames_and_PathNames.md'>EsfName</a></b> is the unique name for this button message set.<br>
</li><li><b>Description</b> is a short description of the button message set.<br>
</li><li><b>Comments</b> is any other information you want to maintain about the button message set.</li></ul>

The button message set specifies optional package and document footers, the button labels and tooltips (shown if the mouse is over the button) as well as various status messages shown to the party when processing a document.<br>
<br>
<h3>Package and document footer</h3>
<ul><li><b>Package footer</b> is optional HTML to show at the bottom of the package that lists the documents for the party to process. By default, we include a note to the party to bookmark the link to return at a later time.<br>
</li><li><b>Document footer</b> is optional HTML to show at the bottom of each document. By default nothing is shown.</li></ul>

<h3>Package buttons</h3>
Under the <b>Package buttons</b> section:<br>
<ul><li><b>Continue button label (has documents to do)</b> and <b>Tooltip to show the party</b> define the continue button when a party has a list of documents that need to be processed.<br>
</li><li><b>Continue button label (all documents completed)</b> and <b>Tooltip to show the party</b> define the continue button when a party has completed all documents and can be used to show the first document.<br>
</li><li><b>Edit button label (reports access)</b> and <b>Tooltip to show the party</b> define the edit button that only appears if accessing the transaction as the ESF_reports_access party (update access from a report).<br>
</li><li><b>View button label (document complete)</b> and <b>Tooltip to show the party</b> define the view button that only appears if returning to the package after having completed some of the documents. It also appears when accessing the transaction as the ESF_reports_access party (view access from a report).<br>
</li><li><b>Delete button label (only if no signatures and party authorized)</b> and <b>Tooltip to show the party</b> define the transaction delete button that only appears if no signature have been applied and the party defined in the package has been enabled to delete it.<br>
</li><li><b>Return/not-completing button label (only if a not-completing URL is defined)</b> and <b>Tooltip to show the party</b> define the button label the party can press if they elect not to complete the documents at this time. It is only present if the party in the package has such an URL defined. It can be used when integrating a document process flow so that if they decide not to sign they can be returned to a page where you'll know they did not complete the documents.<br>
</li><li><b>Download PDF button label (only when party completed)</b> and <b>Tooltip to show the party</b> define the download button that bundles all completed documents in a PDF.</li></ul>

<h3>Document buttons (common)</h3>
Under the <b>Document buttons</b> section is a common button shown to a parties:<br>
<ul><li><b>Go to package button label</b>, <b>Tooltip to show the party</b> and <b>Message to show the party</b> define the button on a document that will return the party back to the package list. The message is shown at the top to help the party know what it means.</li></ul>

<h3>Document buttons (party can fill/edit)</h3>
Under the <b>Document buttons (party can fill/edit)</b> section are the buttons shown to a party when they can fill, edit and/or sign a document:<br>
<ul><li><b>Next page button label</b> and <b>Tooltip to show the party</b> define the next page button to go to the next page in a multi-page document.<br>
</li><li><b>Previous page button label</b> and <b>Tooltip to show the party</b> define the previous page button to go to the previous page in a multi-page document.<br>
</li><li><b>Save button label</b> and <b>Tooltip to show the party</b> defines the save button that allows a party to save the data they've entered so far without attempting to go into review mode (and without doing data validations). This button is also shown for update access to the ESF_reports_access party when accessing from a report.<br>
</li><li><b>Continue to review button label</b>, <b>Tooltip to show the party</b> and <b>Message to show the party</b> define the button when the next step is to review the finalized document that contains all their updates.</li></ul>

<h3>Document buttons (party review after fill/edit)</h3>
Under the <b>Document buttons (party review after fill/edit)</b> section are the buttons shown to a party in review mode after they have filled out the form, signed, etc.:<br>
<ul><li><b>Submit button label (signature added),</b>Tooltip to show the party<b>and</b>Message to show the party<b>define the final submit button if the party signed the document.<br>
</li><li></b>Submit button label (no signature added), <b>Tooltip to show the party</b> and <b>Message to show the party</b> define the final submit button if the party did not sign but otherwise filled in form fields.<br>
</li><li><b>Return to edit button label</b>, <b>Tooltip to show the party</b> and <b>Message to show the party</b> define the button to allow the party to return to edit mode so changes can be made before being submitted.</li></ul>

<h3>Document buttons (view-only party initial review)</h3>
Under the <b>Document buttons (view-only party initial review)</b> section are the buttons shown to a view-only party when processing a document they have not yet read/reviewed:<br>
<ul><li><b>Next page button label</b>, <b>Tooltip to show the party</b> and <b>Message to show the party</b> define the button shown to go to the next page on a multi-page document.<br>
</li><li><b>Previous page button label</b> and <b>Tooltip to show the party</b> define the button shown to go to the previous page on a multi-page document.<br>
</li><li><b>Complete review button label</b>, <b>Tooltip to show the party</b> and <b>Message to show the party</b> define the button to submit indicating that they have completely read the document.</li></ul>

<h3>Document buttons (return completed parties)</h3>
Under the <b>Document buttons (returning completed parties)</b> section defines the buttons shown to parties who have already completed the document but have returned to review/re-read it:<br>
<ul><li><b>Next page button label</b> and <b>Tooltip to show the party</b> define the button to go to the next page in a multi-page document.<br>
</li><li><b>Previous page button label</b> and <b>Tooltip to show the party</b> define the button to go to the previous page in a multi-page document.<br>
</li><li><b>Next document button label</b> and <b>Tooltip to show the party</b> define the button to go to the next document in a multi-document package.<br>
</li><li><b>Previous document button label</b> and <b>Tooltip to show the party</b> define the button to go to the previous document in a multi-document package.</li></ul>

<h3>General messages shown to parties</h3>
Under the <b>General messages shown to parties</b> section are the messages shown to users based on where they are in the process flow:<br>
<ul><li><b>Party retrieves a document that is already completed</b> is shown when a party returns to a document that they have already completed.<br>
</li><li><b>Warning message shown to a party if attempts to work on completed document</b> is a warning message shown to a party if they use the BACK/FORWARD browser buttons and try to edit or submit a document that has already been completed.<br>
</li><li><b>View-only party views a document</b> is shown when a view-only party views a document<br>
</li><li><b>Non-signing party reviewing a document before submitting</b> is for a non-signing party who has filled out some of the document when reviewing their updates, but before being submitted.<br>
</li><li><b>Signing party reviewing a document before submitting</b> is for a signing party who is reviewing the final document, but before being submitted.<br>
</li><li><b>Party retrieves a document that needs to be filled out</b> is for a party who retrieves a document that needs to be filled out or signed.<br>
</li><li><b>Party has completed all documents</b> is shown when a party completes all documents in the package. It is shown on the package page. If a "completed URL" is defined in the party in the package, this message will not be shown as the party will be redirected to that URL when all documents are completed.<br>
</li><li><b>Party has deleted the transaction</b> is shown if the party was able to delete the transaction and all related documents.</li></ul>

<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

<h2>Document styles <img src='http://open.esignforms.com/images/HowToGuidesWiki/documentStylesIcon.png' /></h2>

Document styles provides basic control of the look of your documents. They specify CSS (Cascading Style Sheets) rules. By using a common set of styles, documents will have a consistent look. Open eSignForms comes with a built-in default style in the <b>ESF/Library/Template</b> library called <b>ESF_DefaultDocumentStyle</b>. It is a clean, modern look.<br>
<br>
The values associated with the styles can be seen in the <b>ESF/Library/Template's</b> drop downs.<br>
<br>
To use the style, you must set it as the <a href='#Documents.md'>document version's style</a>. You can also set your document style as your <a href='#Libraries.md'>library's default value</a> to use when creating new documents.<br>
<br>
Click on <b>Document styles</b> to show all document styles in the selected library.<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/documentStyles.png' />

<ul><li>Choose <b>Enabled</b> to allow the document style to be used. If a document style is no longer needed, click <b>Disable</b>.<br>
</li><li><b><a href='HowToGuides#EsfNames_and_PathNames.md'>EsfName</a></b> is the unique name for this document style.<br>
</li><li><b>Description</b> is a short description of the document style.<br>
</li><li><b>Comments</b> is any other information you want to maintain about the styles.</li></ul>

The style is composed of various aspects that are used to override the hard-coded default CSS that ensure basic document functionality. It can be viewed from the <a href='#Document_page_editor.md'>document page editor's</a> <b>View default CSS</b> link. Values that are specified as "(Default)" will use the values defined in default CSS. Values that are specified as "Inherit" use the setting of its parent element.<br>
<br>
<ul><li><b>General document contents</b> sets the font styles for the regular text you put on the page.<br>
</li><li><b>Signatures</b> sets the font styles to use for signatures and signature dates, to give a styled look that makes the typed name electronic signature stand out from the general document contents.<br>
</li><li><b>Field data on review</b> sets font styles to be applied to all fields when in review mode (display mode, compared to edit mode when the field can be entered). This can be useful if you would like all "variable data" in your documents to stand out from the boilerplate text.<br>
</li><li><b>Required data in input fields</b> specifies the styles for input fields that are required.<br>
</li><li><b>Optional data in input fields</b> specifies the styles for input fields that are not required.<br>
</li><li><b>Invalid data in input fields</b> specifies the style for input fields when they contain invalid data and an error has been reported. It helps identify fields that need to be corrected.<br>
</li><li><b>Normal label</b> specifies the style of normal-sized field label.<br>
</li><li><b>Normal error label</b> specifies the style of the normal-sized field label when that field has been flagged as invalid.<br>
</li><li><b>Small label</b> specifies the style of small-sized field label.<br>
</li><li><b>Small error label</b> specifies the style of the small-sized field label when that field has been flagged as invalid.</li></ul>

<i>Note: You can always specify the fonts for your text directly in the document page editor. But to control labels, error looks, signatures, etc. you need to use the document style.</i>

<i>Default CSS print style note: The default CSS file includes a brief print style: div.newPage will insert an actual page break; fonts are set to 90% of their screen size; and link tags (A HREF) with the "showURL" class will display the value of the link's URL since a printed link would otherwise lose that information.</i>

<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

<h2>Drop downs <img src='http://open.esignforms.com/images/HowToGuidesWiki/dropDownsIcon.png' /></h2>

Click on <b>Drop downs</b> to show all drop downs (selection boxes) in the selected library.<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/dropDown.png' />

<ul><li>Choose <b>Enabled</b> to allow the drop down to be used. If a drop down is no longer needed, click <b>Disable</b>.<br>
</li><li><b><a href='HowToGuides#EsfNames_and_PathNames.md'>EsfName</a></b> is the unique name for this drop down.<br>
</li><li><b>Description</b> is a short description of the drop down.<br>
</li><li><b>Comments</b> is any other information you want to maintain about the drop down.</li></ul>

<ul><li>Check <b>Allow Multi-Selections</b> if the drop down should allow the user to select more than one value from the list.<br>
</li><li>The <b>Label</b> is the text the user will select from when viewing the drop down list.  The <b>Value</b> is the data value that will be stored in the drop down field. The label and value can be set to same.<br>
</li><li>If "no selected value" is allowed, consider creating the first <b>Label</b> as "--SELECT--" with an empty <b>Value</b>.</li></ul>

Click the <b>Add option</b> once for each label+value you want to appear in your drop down. It will create a new entry that you can then update.<br>
<br>
Select an option by clicking a row so it is highlighted (such as clicking in the <b>Order</b> field or the narrow space between the label and value) and then click the <b>Remove selected option</b> to remove that option.<br>
<br>
Drag a row to another location to rearrange the order that the drop down displays its options.<br>
<br>
<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

<h2>Email templates <img src='http://open.esignforms.com/images/HowToGuidesWiki/emailsIcon.png' /></h2>

Email templates are used to define any email that needs to be sent from the system. Like a document, they can have variable data substituted to customize them for individual parties.<br>
<br>
Click on <b>Emails</b> to show all email templates in the selected library.<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/emailTemplate.png' />

<ul><li>Choose <b>Enabled</b> to allow the email template to be used. If an email template is no longer needed, click <b>Disable</b>.<br>
</li><li><b><a href='HowToGuides#EsfNames_and_PathNames.md'>EsfName</a></b> is the unique name for this email template.<br>
</li><li><b>Description</b> is a short description.<br>
</li><li><b>Comments</b> is any other information you want to maintain.</li></ul>

<ul><li><b>Send email FROM:</b> specifies the FROM email address that will be used. Often, this is a NO-REPLY@example.com address to indicate that the email is an automated email and not a personal email. However, you can use any email address. The default is a property set value <code>${property:ESF.SendEmailFrom}</code>. You can use any field from the documents that are used when the email is sent, or you can use the user who started the transaction with a value like <code>${transaction:ESF_Started_By_User_Email_Address}</code>.<br>
</li><li><b>Send email TO:</b> specifies who the email will be sent to. For most party-based emails, we recommend using the value <code>${EMAIL}</code> since that variable can be set (overridden) in various configuration options. For example, in a Package Party configuration, you can set the option labeled <code>Notify email address spec (${EMAIL})</code> to replace <code>${EMAIL}</code> everywhere it's used in this email template (including the email body text). The same is true for the package's custom logic action for sending an email option <code>Email address spec (${EMAIL})</code>. Multiple emails can be specified (use a semicolon to separate them).<br>
</li><li><b>CC:</b> specifies any CC recipients.<br>
</li><li><b>BCC:</b> specifies any BCC recipients (blind-copy so will not appear to other recipients).<br>
</li><li><b>Subject</b> is the subject of the email.<br>
</li><li><b>Text version</b> is the email text to show for clients who cannot or will not allow HTML-based emails. A text version is required as it's guaranteed to be used by all email clients.  You may specify the field <code>${LINK}</code> anywhere the party's pickup link should appear. Each party has a unique <code>${LINK}</code> value to ensure the system knows who is retrieving the package of documents.  In the package's custom logic action for sending an email option <code>For party (${LINK})</code> allows you to control which value to use. Emails sent to a given party will use that party's unique link value.<br>
</li><li><b>HTML version</b> is the HTML version of the email for clients that support HTML. Generally, it should be similar to the text version, but you can use various stylings to make the email more attractive.  You may put ${LINK} anywhere you need the party's unique pickup link to appear. If the actual URL of the link is not shown in your HTML version, we recommend showing the full link at the bottom, in a smaller font, with something like this:</li></ul>

<pre><code>If the above link is not active (e.g. nothing happens when you click on it), please copy the link below exactly as shown into your web browser's address or location field:<br>
<br>
${LINK}<br>
</code></pre>

<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

<h2>Files <img src='http://open.esignforms.com/images/HowToGuidesWiki/filesIcon.png' /></h2>

Files are used to upload and save files (generally not images, though) linked to by your various documents. When a file is only needed for a particular document, you should consider defining the <a href='#Files_linked_in_document.md'>Files linked in a document version</a>. But by defining the files in the library, they are available for other documents, and of course you can easily override them using a Branding Library should the file change depending on who is using the document.<br>
<br>
Click on <b>Files</b> to show all files in the selected library.<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/fileNewUpload.png' />

<ul><li>Choose <b>Enabled</b> to allow the file to be used. If a file is no longer needed, click <b>Disable</b>.<br>
</li><li><b><a href='HowToGuides#EsfNames_and_PathNames.md'>EsfName</a></b> is the unique name for this file.<br>
</li><li><b>Display name</b> is the name shown in the link to this file.<br>
</li><li><b>Description</b> is a short description.<br>
</li><li><b>Comments</b> is any other information you want to maintain.</li></ul>

If it's a new file, click the <b>Set the file...</b> button. You can then choose a file (GIF, JPEG or PNG should generally be <a href='#Images_and_Logos.md'>uploaded as an image</a>, not a file). A link to download the file will be created.<br>
<br>
Click the <b>Save</b> button to save the file.<br>
<br>
If you are replacing an existing file:<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/fileUpdate.png' />

Click the <b>Replace file...</b> button to select a new file to replace the one shown.<br>
<br>
Click the <b>Save</b> button to save the new file.<br>
<br>
<i>Tip: In a document, while you can reference a file using the <code>${file:FileName}</code> syntax, you will probably find it easier to use the editor's link button to insert a link to the file so it's visible in the editor.</i>

<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

<h2>Images and Logos <img src='http://open.esignforms.com/images/HowToGuidesWiki/imagesLogosIcon.png' /></h2>

Images/Logos are used to upload and save images and logos used across your various documents. When an image or logo is only needed for a particular document, you should consider defining the <a href='#Images_in_document.md'>image inside the document version</a>. But by defining the images in the library, they are available for other documents, and of course you can easily override them using a Branding Library should the image change depending on who is using the document.<br>
<br>
Click on <b>Images/Logos</b> to show all images in the selected library.<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/imageNewUpload.png' />

<ul><li>Choose <b>Enabled</b> to allow the image to be used. If an image is no longer needed, click <b>Disable</b>.<br>
</li><li><b><a href='HowToGuides#EsfNames_and_PathNames.md'>EsfName</a></b> is the unique name for this image.<br>
</li><li><b>Description</b> is a short description.<br>
</li><li><b>Comments</b> is any other information you want to maintain.<br>
</li><li>Check <b>Embed image in HTML</b> to include the image data directly in the HTML web page using a 'data URI'.  If not checked, the image will be served using a separate link/URL and request.</li></ul>

If it's a new image, click the <b>Set the image file</b> button. You can then choose an image file (GIF, JPEG or PNG should be used for online documents). A thumbnail image will be generated, along with a link to view the full-sized image. Note that images that have transparent backgrounds will show a black background in the thumbnail, but the original image will remain transparent.<br>
<br>
Click the <b>Save</b> button to save the image.<br>
<br>
If you are replacing an existing image:<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/imageUpdate.png' />

Click the <b>Replace image file</b> button to select a new image file to replace the one shown.<br>
<br>
Click the <b>Save</b> button to save the new image.<br>
<br>
<i>Tip: In a document, while you can reference an image using the <code>${image:imageName}</code> syntax, you will probably find it easier to use the editor's image button to insert the image so it's visible in the editor.</i>

<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

<h2>Property sets <img src='http://open.esignforms.com/images/HowToGuidesWiki/propertySetsIcon.png' /></h2>

Property sets are a bundle of related name-value pairs. This allows you to create more flexible and re-usable documents because certain key information, like company name, address, phone, contact email, etc. can be externalized with the values stored in property sets. Changes can then be made simply by updating the property set, and all documents that reference that property set will automatically begin using the new values without having to update each document.<br>
<br>
Properties are referenced first by which property set is being used, and then which property in that set is being referenced: <code>PropertySetName.PropertyName</code>.<br>
<br>
When testing, it is sometimes important that a different value be used for a given property.  If you define the same property name with a <code>_TEST</code> suffix, that property will be used when in Test or Test Like Production modes. When testing, it will first look for <code>PropertySetName.PropertyName_TEST</code> and if not found, then look for the expected property <code>PropertySetName.PropertyName</code>.<br>
<br>
Also, if you support multiple brands, you can create the property set (with the same name) in a branding library so that multiple companies can use the same document, yet each gets their company name, address, phone, etc. in their documents.<br>
<br>
Click on <b>Property sets</b> to show all property sets in the selected library.<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/propertySet.png' />

<ul><li>Choose <b>Enabled</b> to allow the property set to be used. If a property set is no longer needed, click <b>Disable</b>.<br>
</li><li><b><a href='HowToGuides#EsfNames_and_PathNames.md'>EsfName</a></b> is the unique name for this property set.<br>
</li><li><b>Description</b> is a short description.<br>
</li><li><b>Comments</b> is any other information you want to maintain.</li></ul>

In the table of name-value pairs on the right side, the fields are:<br>
<ul><li>The <b>EsfName</b> is the name of the property (must be unique within this property set).<br>
</li><li>The <b>Value</b> is the value to show when this property is referenced. It can be more than one line.<br>
</li><li>The <b>Comment</b> is any information you'd like to maintain about the property.</li></ul>

Click the <b>Add property</b> button one or more times to add one more new properties. Just replace the name and value as needed.<br>
<br>
To remove properties, click on one or more rows so they are highlighted, then click the <b>Remove selected properties</b> button. It can be tricky to select a row, but if you click in the row, but not inside a input field, it should highlight to show the row been selected.<br>
<br>
Property sets can be referenced in your documents, email templates and the like using <code>${property:propertySetName.propertyName}</code> notation. The <code>propertySetName</code> is the name of the property set, and <code>propertyName</code> is the name of the individual property defined in that property set.  In Test or Test Like Production modes, it will first look for <code>propertyName_TEST</code> to see if a special testing value should be used instead.<br>
<br>
<i>Tips: Normally, property values are encoded to be HTML-safe when displayed in your documents, but if you have taken care to create a property value containing valid HTML, you can include that in your document using <code>${htmlproperty:propertySetName.propertyName}</code> notation. You can use this as a simple, flexible way to insert variable or common HTML in your documents, including custom styles you frequently use in your documents.</i>

<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

<h3>Nesting property sets for simple property-based database</h3>

Using a custom action to set a field value, you can look up a property value using another field as the key, giving a simple DB-like lookup capabilities.<br>
<br>
For example, let's say you have a field, <code>productId</code>, and it perhaps is set from a drop down list, but it's values are 1, 2, 3, etc.<br>
<br>
We can create a property set, say <code>ProductInfo</code>, with a property values such as:<br>
<pre><code>Id1_Price = $5.00<br>
Id1_Description = This describes the first item.<br>
Id2_Price = $25.50<br>
Id2_Description = This describes the second item.<br>
Id3_Price = $19.99<br>
Id3_Description = This describes the third item.<br>
</code></pre>

Now, you want to get the product's price by it's id, you could create a field <code>productPrice</code> and in a custom action set it based on the current <code>productId</code> value using nested field specs: <code>${property:ProductInfo.Id${productId}_Price}</code>

And you can get it's description using: <code>${property:ProductInfo.Id${productId}_Description}</code>

This same technique also works if to select a property set (and/or the property name within the set), so if I instead had property sets named <code>Product_1</code>, <code>Product_2</code>, <code>Product_3</code>, etc. and they each had properties name <code>Price</code> and <code>Description</code>, we'd have property sets set something like:<br>
<br>
<pre><code>Product_1.Price<br>
Product_1.Description<br>
<br>
Product_2.Price<br>
Product_2.Description<br>
<br>
Product_3.Price<br>
Product_3.Description<br>
</code></pre>

which could be accessed depending on the <code>productId</code> using:<br>
<br>
<pre><code>${property:Product_${productId}.Price} and ${property:Product_${productId}.Description} <br>
</code></pre>

I hope this is a useful tip for those who need a simple lookup database that is based on some other value.  The trick is that property set names and property names are limited to our standard field naming convention, so it must start with a letter, be composed of letters, numbers and underscores and be no longer than 50 characters each.<br>
<br>
<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

<h2>Serial generators <img src='http://open.esignforms.com/images/HowToGuidesWiki/serialGeneratorsIcon.png' /></h2>

Serial generators are used to create unique, serial numbers. They are often used to automatically assign customer numbers, purchase order numbers, etc. It manages two numbers, one for test transactions and the other for production transactions.  Like other items in the library, you can override a serial generator via the branding library defined for a transaction template.<br>
<br>
Click on <b>Serial generators</b> to show all serial number generators in the selected library.<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/serialGenerator.png' />

<ul><li>Choose <b>Enabled</b> to allow the serial number generator to be used. If a serial generator is no longer needed, click <b>Disable</b>.<br>
</li><li><b><a href='HowToGuides#EsfNames_and_PathNames.md'>EsfName</a></b> is the unique name for this serial number generator.<br>
</li><li><b>Description</b> is a short description.<br>
</li><li><b>Comments</b> is any other information you want to maintain.<br>
</li><li><b>Next production serial</b> can be set when a new generator is being created. It will be the first serial number returned when used in a production transaction. Subsequently, it will just show the current production serial number generator value.<br>
</li><li><b>Next test serial</b> can be set when a new generator is being created. It will be the first serial number returned when used in a test transaction. Subsequently, it will just show the current production serial number generator value.</li></ul>

On the right side, the version-specific field is:<br>
<ul><li>The <b>Serial number format</b> specifies how the serial number will appear. Use '#' for each digit where if it's a leading zero, it will be suppressed. Use '0' for each digit where it will be shown even if it's a leading zero. You can use fixed letters before (prefix) and after (suffix) the # and 0 pattern. A typical pattern is ###000000000 or with a prefix like ACCT000000000. If the number is bigger than the pattern, the additional digits will be shown.</li></ul>

Serial number generators can be referenced in your documents using <code>${serial:serialName}</code> notation. The <code>serialName</code> is the name of the serial generator. Once a serial number is issued, it will not be issued again. To reduce gaps, we recommend you set your serial number field (such as a purchase order number) to a value like '#PENDING' and use a custom logic rule to set that field to the serial number when the order is submitted (or at the very least on review).<br>
<br>
<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

<h2>Fields <img src='http://open.esignforms.com/images/HowToGuidesWiki/fieldsIcon.png' /></h2>

Click on <b>Fields</b> to show all field templates in the selected library.<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/fieldTemplate.png' />

Most fields, of course, are <a href='#Fields_in_document.md'>defined in the document</a>, which you can reference for details on configuring them. The process is the same.<br>
<br>
The main purpose for a field template defined in a library is to create "standardized" field names and configuration. When creating documents, you can create fields based on those defined in the library so that their values take on the standard definition. Of course, any value can be overridden in the specific document's definition.<br>
<br>
<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

<h2>Parties <img src='http://open.esignforms.com/images/HowToGuidesWiki/partiesIcon.png' /></h2>

Click on <b>Parties</b> to show all party templates in the selected library.<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/partyTemplate.png' />

Most parties, of course, are <a href='#Parties_to_document.md'>defined in the document</a>.<br>
<br>
The main purposes for a party template defined in a library are 1) to create a "standardized" name for your parties so that as you create multiple documents, you tend use the same name for the same roles across those documents; and 2) if you configure a party in a package as a <a href='UserGuide#To_Do.md'>'To Do'</a> party, then you can define the <a href='SystemAdminGuide#Groups.md'>group</a> that represents members of the party so that any member in the group can process transactions when the party is active.<br>
<br>
If the package party is defined for To Do purposes, specify the <b>Production To Do Group</b> and <b>Test To Do Group</b> that represents the users who will be able to play this role. Also, if you support multiple companies, each branding library is able to set their own group to play the given role. So if you have an "Approver" role, you can set it to be one group for one company, but another group for the other company. The production versus test settings allow different users to play the role based on whether doing a production or test transaction.<br>
<br>
<h3>To Do configuration</h3>
To use To Do, do the following:<br>
<br>
<ol><li>Check if there there is an existing Group of users (listed under Access control) defined that represents the people who will play the role of the party. If not, create one like the most similar existing group and update the users who belong in it.<br>
</li><li>Inside the Library, under the Parties, create a new Party and set the "Production To Do Group" and "Test To Do Group" to the group determined in step 1.<br>
</li><li>In the Package, select the party listed in the package that needs access to the To Do. Then set its "To Do Party EsfName" to be the party created in step 2.</li></ol>

<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

<h1>Packages <img src='http://open.esignforms.com/images/HowToGuidesWiki/packageIcon.png' /></h1>

Packages allow you to bundle one or more documents so that they are processed as a group. Each party will be able to process one or more of the documents in the package. It is possible to have some parties only see a subset of documents.<br>
<br>
You also configure the package parties who will process the documents. The initial list of parties come from the names defined in the documents you add. But you may find that you need to rename or group the parties; for example, one document may say call the party who fills in the document as "FirstParty" while another document may have called that party "Customer". In the package, if these are really the same person, you can bundle them together.<br>
<br>
Click on <b>Programming->Packages</b> to show all packages of documents that are available to you.<br>
<br>
Click on a package to view or configure it. To create a new package, select a template or similar existing package you have permission to access and click the <b>Create new like</b> button.<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/package.png' />

<ul><li>Choose <b>Enabled</b> to allow the package to be used. If a package is no longer needed, click <b>Disable</b>.<br>
</li><li><b><a href='HowToGuides#EsfNames_and_PathNames.md'>PathName</a></b> is the unique path name for this package.<br>
</li><li><b>PDF download file name spec</b> is an optional default file name to use when parties download their documents after completing them all, as well as in reports. The default is generally 'MyDocuments.pdf' but when downloading an individual document, if that document has it's own naming specification, that name will be used.<br>
</li><li><b>Description</b> is a short description.<br>
</li><li><b>Comments</b> is any other information you want to maintain.<br>
</li><li><b>Permissions to access this package</b> contain the standard List, View Details, Create Like, Update and Delete permission lists. Just choose which groups are allowed to do each of these operations on a package. Normally, the "programming" group has permission to this as it's not a general user task.</li></ul>

For the list of documents and parties on the right side, the fields are:<br>
<ul><li>The <b>Choose documents</b> shows each Library that is available to you. If you open the arrow, it will show the documents defined in each. Just click and drag a document from this list into the <b>Documents in this package</b> table. If other documents are already in the list, note the insertion bar when you drag the document over to choose to place it at the top (first), between documents, or at the bottom (last). Of course, you can re-order at any time.<br>
</li><li>The <b>Documents in this package</b> table lists each <a href='#Package_document_configuration.md'>document in the package</a> and the order they will be presented. If you drag a document from the table back to the <b>Choose documents</b> tree and drop it anywhere there, the document will be removed from the package and will automatically be returned to the correct library where it came from.<br>
</li><li>The <b>Parties involved with this package of documents</b> table lists all <a href='#Package_party_configuration.md'>parties defined in the package</a>, as well as the order in which they should process the package of documents. The first party is the "initiator" who starts the transaction and can be a normal user or an <a href='#From_another_web_site_or_web-accessible_application,_email_proce.md'>automated API party</a>. If for any reason your package needs more parties than are defined in the documents, such as adding a party who may need to see the completed documents when done, you can use the <b>Add View-Only party</b> button to add a party that will be given 'View only' access to all documents in the package. You can then modify that party as needed.<br>
</li><li>The <b>Package+disclosure view</b> drop down list lets you choose the <a href='#Package+disclosure_documents.md'>special document</a> that plays the role of welcoming the parties, showing E-Sign disclosures, as well as the list of documents the party is expected to process. By default, this is the <b>ESF/Library/Template/StandardPackageDisclosures</b> document.<br>
</li><li>The <b>Button message set</b> drop down list lets you choose the <a href='#Button_message_sets.md'>button message set</a> to use for this package. By default, this is the <b>Esf/Library/Template/ESF_DefaultButtonMessage</b> set.</li></ul>

Click the <b>Make Test version Production</b> button to move a Test version package to Production.<br>
<br>
If the package is already a Production version, use the <b>Create next Test version</b> button to create the next package that you can test until you are ready to make it production. You can also use the <b>Revert to Test</b> button to temporarily take the package out of production for a quick fix before you make it production again (do this with caution since a production transaction will get an error, or use the prior production version if one exists, while you are making this update).<br>
<br>
Click the <b><a href='#Customize_logic.md'>Customize logic</a></b> button to add special processing rules to this package of documents.<br>
<br>
Click the <b><a href='#Map_report_fields.md'>Map report fields</a></b> button to define the fields in the documents you have selected that you would like to include in reports or To Do lists for your internal parties.<br>
<br>
Click the <b>Export</b> button to export the package configuration so it can be imported in another deployment. You will be prompted to save the configuration to your local computer disk.<br>
<br>
Click the <b><a href='#Package_import_configuration.md'>Import version...</a></b> button to import the package configuration previously exported elsewhere so that it overwrites the configuration of the package version. The package version must be a Test version to change it this way.<br>
<br>
Note that after any change to the package, including any changes made in other screens related to the package, you will have to click the <b>Save</b> button keep those changes.<br>
<br>
<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

<h2>Package document configuration</h2>

Note that you can drag to re-order the documents, or drag it back to the <b>Choose documents</b> list of libraries to remove it.<br>
<br>
Click on a document from the <b>Documents in this package</b> table to configure the parties who will process that document.<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/packageDocument.png' />

Since package parties are defined initially from the parties defined in the various documents, it is possible that the names used in various documents are not consistent. This allows you to specify which package party will play the role for a given document party. Select the package party or parties who will be allowed to play the specified document party.<br>
<br>
Click <b>Ok</b> to remember the changes. Click <b>Cancel</b> to discard any changes.<br>
<br>
<i>Tip: To save your changes, remember to click the <b>Save</b> button for the package.</i>

<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

<h2>Package party configuration</h2>

Note that you can drag a party to re-order the processing flow. If after you are done you have parties defined that do not reference any documents, you can remove them using the <b>Remove X unused package parties</b> button <img src='http://open.esignforms.com/images/HowToGuidesWiki/removeUnusedPackagePartiesButton.png' /> that appears below the list of parties.<br>
<br>
Click on a party in the <b>Parties involved with this package of documents</b> to configure the package party.<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/packageParty.png' />

<ul><li><b>Package Party EsfName</b> is the name of the party as used in the package. Remember, package parties initially default to the names they were given in the documents, but the names may not (most likely will not) be consistent across all of the documents, so this allows you to specify the name as it makes sense for this package.<br>
</li><li><b>Display name</b> is the name this party will use whenever it is shown to a user.<br>
</li><li><b>Landing page</b> defines the page the party will see when they first access the package of documents. The default is "Package (disclosures)" which shows the welcome message, E-Sign Disclosures and list of documents to be processed as specifed on the package's "Package+disclosure view". You may also select "First document" to land on the first document in the package that the party is allowed access to. Select "First To Do or First document" to land on the first document the party must work on, or the first document if all documents have been processed; this is used when a party may come back over time to complete the package so they resume on the first document that needs their action. Select "First To Do or Package" to land on the first document the party must work on, or the package document if all documents have been processed.<br>
</li><li>Check <b>Must be logged in</b> if this party is supposed to be an internal user. This ensures that step is taken only by authenticated users.<br>
</li><li>Check <b>Allow delete tran if no signatures</b> to allow the party to delete the transaction, if no signatures have been applied, from the package document. This is generally used only on the first party since they may start the transaction, and then decide not to continue. If the user does not complete it, or delete it, it will be in that user's To Do queue so they can resume later. If they are external users, the transaction will not progress unless the user comes back with the unique pickup link for it (like if they bookmarked the page or your process sent them an email with the link).<br>
</li><li>For <b>Select document parties for this package party</b> select all document+party combinations that apply. You can use the special "View only" party to require this party view the document, but otherwise not be able to change it (or sign it).  You can also use the special "View optional" party to allow this party to view the document using the 'View' button on the package, but they are not required to view it and the general process flow will not include this document.<br>
</li><li>Select a <b>To Do Party EsfName</b> if this party actually belongs to a group of users. In a Library, you can define a Party template that is associated with a To Do Group so that anybody who belongs to the group can process the transaction via the To Do work queue. Select that Party name defined in a Library and be sure it has a group associated with. Note that by creating transaction templates with separate branding libraries, it is easy to set up a package where such a party belongs to different groups, such as when running the service for multiple companies or departments.<br>
</li><li>In <b>Renotify</b> select the various intervals that you'd like an email re-notification to be sent to the party until the party step is completed (and the transaction is in progress). It is good to be able to remind a user to complete a document, but you don't want to pester them either.<br>
</li><li>Check <b>Email All To Do Parties</b> if you've also set a <b>To Do Party EsfName</b> if you would like all users who belong to the group associated with the party to receive an email notification.<br>
</li><li>In <b>Notify email address spec (${EMAIL})</b> enter an email address or a document and field specification that contains the email address of the person to notify when this party is activated. The value will replace the ${EMAIL} specification used in the Email template.<br>
</li><li>In <b>Notify Email EsfName</b> specify the Email template to use to notify this party.<br>
</li><li>In <b>On completed redirect link/URL spec</b> you can put in a literal URL or any combination of field and property specifications. If specified, when the party completes all documents in the package, the party will be redirected this URL rather than be shown the completed package page.<br>
</li><li>In <b>Not completed redirect link/URL spec</b> you can put in a literal URL or any combination of field and property specifications. If specified, when the party has not yet completed the package of documents, the package will show a "Go back (not completing now)" button that will redirect the user back to this URL to indicate that they have chosen not to complete the package at this time.</li></ul>

Click <b>Ok</b> to keep any changes, otherwise click <b>Cancel</b>.<br>
<br>
<i>Tip: To save your changes, remember to click the <b>Save</b> button for the package.</i>

<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

<h2>Customize logic</h2>

It is often necessary to add additional processing logic to fine tune the process flow. You can set up special custom rules based on when in the process flow you want it, whether it's limited to a given set of documents or parties, and then add various actions you'd like to take place then.<br>
<br>
Click on the <b>Customize logic</b> button on the package version to configure additional logic.<br>
<br>
Click on the <b>Create new custom logic</b> button <img src='http://open.esignforms.com/images/HowToGuidesWiki/createNewCustomLogicButton.png' /> to add new processing logic rule. Or you can click on a previously created rule to update it.<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/customLogic.png' />

<ul><li>In <b>When event(s) occur</b> select at least one type of event that describes when you'd like the associated actions to run. You can choose from:<br>
<ul><li><b>Party created</b> occurs when a package party is created.<br>
</li><li><b>Party activated</b> occurs when a package party is first activated to process the package.<br>
</li><li><b>Party retrieved document</b> occurs when a package party first retrieves a document.<br>
</li><li><b>Party review document</b> occurs when a package party has filled out the form or is signing and clicks the review button. The party cannot continue to review the completed document if any action produces an error or warning message.<br>
</li><li><b>Party completed document</b> occurs when a package party completes a given document. The party cannot complete the document if any action produces an error or warning message.<br>
</li><li><b>Party view completed document</b> occurs when a package party views a document that has already been completed.<br>
</li><li><b>Party saved document</b> occurs when a party clicks the 'Save' button, such as updating a document via the ESF_reports_access party when accessing the transaction from a report.<br>
</li><li><b>Party completed</b> occurs when a package party complete all documents in the package that are assigned to him or her.<br>
</li><li><b>Party transferred</b> occurs if a user transfers a given package party to another person through the transaction details page in reports and general transaction search. This occurs when a transaction is started and it turns out there was an error, such as invalid email address, or you find another person actually needs to process it.<br>
</li><li><b>Transaction started</b> occurs when the transaction is first started.<br>
</li><li><b>Transaction completed</b> occurs when the transaction is completed.<br>
</li><li><b>Transaction canceled</b> occurs when the transaction is canceled.<br>
</li><li><b>Timer expired</b> occurs when a user-defined timer expires. Because a timer fires independently in the future (no party is processing a document at the time), you should not select limiting documents or parties. A timer expired event can fire even after the transaction is completed, but it will be ignored if the transaction is canceled or suspended at the time it expires.<br>
</li></ul></li><li>In <b>Limit only to documents (optional)</b> check any documents if the actions should only fire when the selected event(s) occur, but also only when the specified document is being processed. If you do not select any, then it will not matter which document is involved.<br>
</li><li>In <b>Limit only to parties (optional)</b> check any parties if the actions should only fire when the selected event(s) occur, but also only when the specified party is processing the transaction. If you do no select any, then it will not matter which party is involved.<br>
</li><li>In <b>Actions</b> you can drag to re-order existing actions or click the <b>Delete</b> button to remove it.<br>
</li><li>Click the <b>Add action</b> button to add the actions you'd like to occur when the specified event arises, possibly limited based on the documents and parties selected.<br>
<ul><li>Choose <b>Set field action</b> to change any field values in your documents.<br>
</li><li>Choose <b>Calculate field value</b> to calculate a value (add, subtract, multiply, divide).<br>
</li><li>Choose <b>Calculate date value</b> to calculate a date by adding a positive (future) or negative (past) number of days, weeks, months or years.<br>
</li><li>Choose <b>Calculate monthly payment</b> to calculate a monthly payment amount based on the loan amount, term in months, and interest rate (APR).<br>
</li><li>Choose <b>Send email</b> to send an email. You only need to send emails that are not invitations for a party. Party invitations are specified in the package party configuration.<br>
</li><li>Choose <b>HTTP send data</b> to send data to another system via HTTP(S) GET/POST.<br>
</li><li>Choose <b>Change tran/party status</b> to cancel the transaction now or in the future, clear a future auto-cancel, skip a party step or skip an entire document.<br>
</li><li>Choose <b>Show error/message</b> to display a message or report an error to the user (mostly used during the <b>Party review document</b> and <b>Party completed page</b> events).<br>
</li><li>Choose <b>PayPal direct charge</b> to specify credit card fields in your document that will be submitted to the PayPal NVP API for a credit card sale.<br>
</li><li>Choose <b>Change File field access</b> to block or make optional the need for a party to view/download the files associated with this field. Of course, if the party is supposed to upload files, this has no bearing.<br>
</li><li>Choose <b>Set/cancel timer</b> to set a new timer that will fire a <b>Timer expired</b> event in the future, or to cancel a previously set timer. You may also cancel all timers.</li></ul></li></ul>

<img src='http://open.esignforms.com/images/HowToGuidesWiki/packageAddActionButton.png' />

Click <b>Ok</b> to keep any changes, otherwise click <b>Cancel</b>.<br>
<br>
Click <b>Close</b> to close the custom logic window.<br>
<br>
Click <b>Delete</b> to delete the selected custom logic rule.<br>
<br>
<i>Tip: To save your changes, remember to click the <b>Save</b> button for the package.</i>

<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

<h3>Conditional actions</h3>

When you configure an action, you can specify a condition that will be checked before running your action. Conditions can be arbitrarily complex, but in practice few are.<br>
<br>
By default, the initial condition associated with an action is called <b>AND</b> and by itself does nothing more than ensure all sub-conditions added to it must all be true to pass the test. You can convert it to an <b>OR</b> condition so that only one of the sub-conditions added to it must be true to pass the test.<br>
<br>
Or you can <b>negate</b> any condition which basically evaluates to the opposite (also known as <b>NOT</b>), so if your condition is true, negating it means it will not pass, but if your condition is false, then negating it means it will pass.<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/ConditionsOnPackageActions.png' />

On the left side of the action configuration shows the condition editor.<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/ConditionsOnPackageActionsNoConditions.png' />

Initially, when there are no conditions yet set, it prompts you to Right-Click to add a new condition to the default <b>AND</b> condition. The top level condition must be an <b>AND</b> or <b>OR</b> condition. You cannot delete this top level condition, but you can convert the default AND to an OR condition, and you can of course negate whichever you choose.<br>
<br>
You may also click and drag a condition to a new location, but you cannot put any condition above or below the top level AND or OR condition. There can only be one top level condition and it must be an AND or an OR condition.<br>
<br>
Right-click on <b>(Right-click to add conditions to AND)</b> to add new conditions to the top level AND condition:<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/ConditionsOnPackageActionsList.png' />

<ul><li>Click <b>Negate condition</b> to convert the selected condition to do the opposite of what it normally would be, also known as <b>NOT</b> the condition.<br>
</li><li>Click <b>Convert to OR condition</b> to change a selected AND condition (all conditions added to it must be true) to an OR condition (one condition added to it must be true). When the condition is an OR condition already, this option will let you convert it to an AND condition.<br>
</li><li>Click <b>Add OR condition</b> if you need to add a condition that itself is true only if one of the sub-conditions you add to it is true.<br>
</li><li>Click <b>Add AND condition</b> if you need to add a condition that itself is true only if all of the sub-conditions you add to it are true.<br>
</li><li>Click <b>Add COMPARISON check</b> to a condition with tests if a field equals, starts with, ends with or contains another value.<br>
</li><li>Click <b>Add ALL FIELDS BLANK check</b> to add a condition in which all fields you specify must be blank (have no value). If you negate this check, it means "ANY FIELD is NON-BLANK," that is, it's true if any of the list fields has a value. You can just specify a single field to check.<br>
</li><li>Click <b>Add ANY FIELD BLANK check</b> to add a condition in which any (at least one) of the fields you specify must be blank. If you negate this check, it means "ALL FIELDS are NON-BLANK," that is, it's true if all of the list of fields have a value. You can just specify a single field to check.<br>
</li><li>Click <b>Add SOME BUT NOT ALL FIELDS BLANK check</b> to add a condition in which at least one field is blank and at least one field has a value. To work as expected, you must specify at least two fields.<br>
</li><li>Click <b>Add EXPIRED TIMER check</b> to add a condition that checks if a specific timer expired. Generally, this is only used when the custom logic action is for a <b>Timer expired</b> event.</li></ul>

<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

<h4>All blank condition</h4>

After you have added or changed a condition, just click on the condition to configure it further.<br>
<br>
AND and OR conditions have no specific condition editors, so for these special types of conditions, you just right-click on them to negate them, convert them from one type to the other, delete it (and all of its sub-conditions), or to add further sub-conditions to them.<br>
<br>
You can also negate this condition by checking the <b>Negate condition (NOT)</b> box. Note this applies to the entire condition, not any given field specification.<br>
<br>
Click on the <b>All blank:</b> condition to change which fields are checked to be blank. You can specify one or more fields to check. A popup editor will appear.<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/ConditionsOnPackageActionsAllBlank.png' />

Click the <b>Add field to check if blank</b> button to specify a new field to check that it's blank (has no value).<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/ConditionsOnPackageActionsAllBlankForm.png' />

<ul><li>Choose from <b>In document</b> the name of the document where the field to check resides.<br>
</li><li>Choose from <b>Field</b> the name of the field in the selected document to check.</li></ul>

You can specify one or more fields to check. In this case, all specified fields must be blank to pass the test.<br>
<br>
If you negate this condition (NOT ALL BLANK), it passes if any of the fields specified has a value (ANY NON-BLANK).<br>
<br>
Like always, click <b>Ok</b> to save your changes. Click <b>Cancel</b> to abandon the change. Click <b>Close</b> to close the popup window. Click <b>Delete</b> to delete a selected field check.<br>
<br>
<i>Tip: To save your changes, you will want to click the <b>Ok</b> button on the custom logic rule as well as click the <b>Save</b> button for the package. Once you do, when  you click on the <b>IF condition</b> button, your conditions will be updated.</i>

<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

<h4>Any blank condition</h4>

Like the <a href='#All_blank_condition.md'>All blank condition</a>, <b>Any blank</b> works the same way except that it is true if any of the fields you specify is blank. At least one blank field must be present to be true.<br>
<br>
If you negate this condition (NOT ANY BLANK), it passes if all of the fields specified have a value (ALL NON-BLANK).<br>
<br>
<h4>Some but not all fields blank condition</h4>

Like the <a href='#All_blank_condition.md'>All blank condition</a>, <b>Some but not all blank</b> works the same way except that it is true if at least one field is blank and at least one field is non-blank (has a value). This condition only makes sense if at least two fields have been specified.<br>
<br>
You rarely will negate this condition, but if you do it will be true if all of the fields are blank, or if all of the fields have a value.<br>
<br>
<h4>Comparison condition</h4>

You can use a comparison condition to check if a field matches another value.<br>
<br>
Click on the <b>Compare:</b> condition to change which fields are to be compared. Only a single field comparison can be configured. A popup editor will appear.<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/ConditionsOnPackageActionsComparison.png' />

You can negate this condition by checking the <b>Negate condition (NOT)</b> box.<br>
<br>
<ul><li>Choose from <b>In document</b> the name of the document where the field to check resides.<br>
</li><li>Choose from <b>Field</b> the name of the field in the selected document to check.<br>
</li><li>Choose from <b>Comparator</b> the type of comparison to perform. Fields that are integers, decimals, money, dates or date+time, you generally want to limit the comparator to the equals, less than and greater than as the others will treat these types as if there were strings.<br>
<ul><li><b>Equals</b> will match if  the two string values are the same.<br>
</li><li><b>Starts with</b> will match if the field starts with a given value.<br>
</li><li><b>Ends with</b> will match if the field ends with a given value.<br>
</li><li><b>Contains</b> will match if the field contains the other value anywhere within its value.<br>
</li><li><b>Less than</b> will match if the field's value is less than the other value.<br>
</li><li><b>Less than or equals</b> will match if the field's value is less than or equals the other value.<br>
</li><li><b>Greater than</b> will match if the field's value is greater than the other value.<br>
</li><li><b>Greater than or equals</b> will match if the field's value is greater than or equals the other value.<br>
</li><li><b>Same length</b> will match if the field's value has the same length as the other value.<br>
</li><li><b>Shorter than</b> will match if the field's value is shorter than the length of the other value.<br>
</li><li><b>Shorter than or same length</b> will match if the field's value is shorter than or the same length as the other value.<br>
</li><li><b>Longer than</b> will match if the field's value is longer than the length of the other value.<br>
</li><li><b>Longer than or same length</b> will match if the field's value is longer than or the same length as the other value.<br>
</li></ul></li><li>Set the <b>Literal or field spec (${})</b> to the value to check against the specified field. It can be a simple string literal, or it can contains a field specification like ${DocumentName.FieldName} to compare against another field value.<br>
</li><li>Check the <b>Case sensitive?</b> box if you want the comparison to be case sensitive (uppercase and lowercase letters must match exactly). The default (unchecked) allows a match regardless, so "Bob" would be equal to "BOB".</li></ul>

If you negate this condition (NOT COMPARISON), it passes if the field does not match the specified value.<br>
<br>
Like always, click <b>Ok</b> to save your changes. Click <b>Cancel</b> to abandon the change. Click <b>Close</b> to close the popup window.<br>
<br>
<i>Tip: To save your changes, you will want to click the <b>Ok</b> button on the custom logic rule as well as click the <b>Save</b> button for the package.</i>

<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

<h4>Expired timer condition</h4>

Click the <b>Add expired timer check</b> button to specify a new timer to check if it just expired.<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/ConditionsOnPackageActionsTimerExpiredForm.png' />

<ul><li>Specify the name of the timer to check if it expired. The timer name is not case sensitive. The corresponding timer is named in a SET TIMER action.</li></ul>

If your condition should be true if any one of several timers expired, simply add additional timers. The condition will be true if any one of the listed timers expired.  You can think of this as a list of timers checked with an OR condition. A 'timer expired' event will occur only after one timer has expired.<br>
<br>
Like always, click <b>Ok</b> to save your changes. Click <b>Cancel</b> to abandon the change. Click <b>Close</b> to close the popup window. Click <b>Delete</b> to delete a selected field check.<br>
<br>
<i>Tip: To save your changes, you will want to click the <b>Ok</b> button on the custom logic rule as well as click the <b>Save</b> button for the package. Once you do, when  you click on the <b>IF condition</b> button, your conditions will be updated.</i>

<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

<h3>Set field value action</h3>

When you need to change (or clear) a value, use the <b>Set field value</b> action. Click the <b>Add field to set</b> button <img src='http://open.esignforms.com/images/HowToGuidesWiki/addFieldToSetButton.png' /> to add a new field to set. Or you can click on a previously created rule to update it.<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/setFieldValueAction.png' />

<ul><li>For <b>In document</b> select the document where the field exists that will be set.<br>
</li><li>For <b>Set field</b> select the field in the selected document that will be set.<br>
</li><li>For <b>New value or field spec to use</b> enter a literal value (or leave blank to blank out the field) or <code>${ }</code> notation to specify the new value for the field.<br>
</li><li>Check <b>Block further party edits</b> only if after setting the value no further edits will be required by parties. This is typically used in situations where a document is used both standalone as well as in a package. For example, when standalone, all of the fields will be filled in by the party. But when in a package, one or more fields may be set from values entered on previous documents (such as name, ID, address, etc.), and once set with those values, the party should not be allowed to change them further.<br>
</li><li>Select zero or more <b>Transforms</b> to apply to the value determined by evaluating the <b>New value or field spec to use</b>. There is no guarantee on the order multiple transforms will take place if more than one is selected.<br>
<ul><li><b>UPPERCASE</b> will convert all characters to uppercase letters.<br>
</li><li><b>lowercase</b> will convert all characters to lowercase letters.<br>
</li><li><b>Capitalize first</b> will capitalize the first letter only.<br>
</li><li><b>Capitalize First, Lowercase Others</b> will capitalize the first letter in each "word" and make the other letters lowercase.<br>
</li><li><b>Compress whitespace</b> will convert multiple whitespace characters into a single space. This is most useful when concatenating fields, some of which may have not value, so extra spaces are removed.<br>
</li><li><b>Strip whitespace</b> will remove all whitespace characters.<br>
</li><li><b>Trim whitespace</b> will remove all leading and trailing whitespace characters.<br>
</li><li><b>Numbers only</b> will remove all characters that are not digits or whitespace.<br>
</li><li><b>Alphabetic only</b> will remove all characters that are not letters or whitespace.<br>
</li><li><b>Alphanumeric only</b> will remove all characters that are not letters, numbers or whitespace.<br>
</li><li><b>First character only</b> will remove all characters after the first. This is a shorthand for using a substring offset of 0 with a length of 1.<br>
</li></ul></li><li><b>Subtring offset</b> is used to extract a portion of the value. The offset specifies the number of characters to skip from the beginning. Leave blank to keep the entire value. Specify 0 to include from the beginning.<br>
</li><li><b>Substring length</b> (appears only if a substring offset is specified) is the number of characters after skipping the specified number of offset characters. If blank (or number less than 1 or longer than the actual number of remaining characters), it will return all characters after the offset characters are skipped. In the string "1234567890" if the offset is 5 and the length is 4, you end u with "6789".</li></ul>

Click the <b>Ok</b> button to keep your changes, or click <b>Cancel</b>.<br>
<br>
Click the <b>Close</b> button to close the set field value actions window.<br>
<br>
Click the <b>Delete</b> button to delete the selected action.<br>
<br>
Note that you can set multiple fields at the same time using this view.<br>
<br>
<i>Tip: To save your changes, you will want to click the <b>Ok</b> button on the custom logic rule as well as click the <b>Save</b> button for the package.</i>

<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

<h3>Calculate field value action</h3>

When you need to calculate a value (add, subtract, multiple or divide), use the <b>Calculate field value</b> action. Click the <b>Add field to calculate</b> button <img src='http://open.esignforms.com/images/HowToGuidesWiki/addFieldToCalculateButton.png' /> to add a new field to calculate. Or you can click on a previously created rule to update it.<br>
<br>
This is only available for Integer, Decimal and Money fields.<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/calculateFieldValueAction.png' />

You can think of this as doing the following in code:<br>
<code>InDocument.SetField = FromDocument.Field OPERATOR FromDocument.Field</code>

<ul><li>For <b>In document</b> select the document where the field exists that will be set to the calculated value.<br>
</li><li>For <b>Set field</b> select the field in the selected "in document" that will be set by the calculation. This is the field that is changed.<br>
</li><li>For <b>From document</b> (left side of operator) select the document where the first field can be found.<br>
</li><li>For <b>Field</b> (left side of operator) select the field in the selected "from document" that will be used in the calculation. This field is not changed.<br>
</li><li>For <b>Operator</b> select the operation to be applied to the left and right hand fields. <code>+</code> means addition; <code>-</code> means subtraction; <code>*</code> means multiplication; and <code>/</code> means division.<br>
</li><li>For <b>From document</b> (right side of operator) select the document where the second field can be found.<br>
</li><li>For <b>Field</b> (right side of operator) select the field in the selected "from document" that will be used in the calculation. This field is not changed.</li></ul>

Click the <b>Ok</b> button to keep your changes, or click <b>Cancel</b>.<br>
<br>
Click the <b>Close</b> button to close the calculate field value actions window.<br>
<br>
Click the <b>Delete</b> button to delete the selected action.<br>
<br>
Note that you can calculate multiple fields at the same time using this view. Also, if you have a multi-step calculation, you can set the field to the first party of the calculation, and then in the next calculation reference that field in the left or right side to perform more operations on it.<br>
<br>
<i>Tip: To save your changes, you will want to click the <b>Ok</b> button on the custom logic rule as well as click the <b>Save</b> button for the package.</i>

<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

<h3>Calculate monthly payment action</h3>

When you need to calculate a monthly payment, use the <b>Calculate monthly payment</b> action. Click the <b>Add payment to calculate</b> button <img src='http://open.esignforms.com/images/HowToGuidesWiki/addPaymentToCalculateButton.png' /> to add a new payment to calculate. Or you can click on a previously created rule to update it.<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/calculateMonthlyPaymentAction.png' />

<ul><li>For <b>In document</b> select the document where the field exists that will be set to the calculated monthly payment value.<br>
</li><li>For <b>Set monthly payment field</b> select the "Money" field in the selected "in document" that will be set by the calculation. This is the field that is changed.<br>
</li><li>For <b>From document</b> select the document where the amount financed field can be found.<br>
</li><li>For <b>Amount financed field</b> select the "Money" field in the selected "from document" that will be used in the calculation. This field is not changed.<br>
</li><li>For <b>From document</b> select the document where the annual interest rate field can be found.<br>
</li><li>For <b>Annual interest rate field</b> select the "Decimal" field in the selected "from document" that will be used in the calculation. This field is not changed.<br>
</li><li>For <b>From document</b> select the document where the number of monthly payments field can be found.<br>
</li><li>For <b>Number of monthly payments field</b> select the "Integer" field in the selected "from document" that will be used in the calculation. This field is not changed.</li></ul>

Click the <b>Ok</b> button to keep your changes, or click <b>Cancel</b>.<br>
<br>
Click the <b>Close</b> button to close the calculate monthly payment value actions window.<br>
<br>
Click the <b>Delete</b> button to delete the selected action.<br>
<br>
Note that you can calculate multiple monthly payments at the same time using this view.<br>
<br>
<i>Tip: To save your changes, you will want to click the <b>Ok</b> button on the custom logic rule as well as click the <b>Save</b> button for the package.</i>

<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

<h3>Send email action</h3>

When you need to send an email other than the party activation email (which is set in the <a href='#Package_party_configuration.md'>package party view</a>), use the <b>Send email</b> action. Click the <b>Add email to send</b> button <img src='http://open.esignforms.com/images/HowToGuidesWiki/addEmailToSendButton.png' /> to add a new email to send. Or you can click on a previously created rule to update it.<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/sendEmailAction.png' />

<ul><li>For <b>Email template</b> choose the email template to send.<br>
</li><li>For <b>For party (${LINK})</b> select the party whose unique link will be used anywhere <code>${LINK}</code> is specified in the selected email template. Note that whoever receives such a link will be able to act as that party.<br>
</li><li>For <b>Email address spec (${EMAIL})</b> enter an email address or <code>${ }</code> field specification that will resolve to the email address to send to. This will replace the <code>${EMAIL}</code> wherever used in the selected email template. If the <b>For party</b> above is selected and this email address specification is blank (or set to <code>${EMAIL}</code> -- better to leave blank), the system will attempt to use the configured package party's email notification specification.<br>
</li><li>For <b>Attach document(s)</b> select one or more documents from the package to send with the email. This will be the document snapshot that exists for the selected document and party. Of course, you can also choose the "Latest" party for a document to send whatever is the latest snapshot of that document at the time the email is being sent.<br>
</li><li>Check <b>Attach as PDF</b> to combine the document snapshots into a single PDF file rather than sending them as attached HTML files. If any of the selected documents is configured for 'Landscape' orientation then all documents will be rendered as landscape in the PDF.<br>
</li><li>If <b>Attach as PDF</b> is selected, a <b>PDF file name spec</b> is shown so you can give the file name of the attached PDF. It's can be a simple file name, such as <code>Agreement.pdf</code>, or it may include field specifications and properties for a customized name, such as <code>Agreement for ${firstName} ${lastName}.pdf</code>.<br>
</li><li>If your package allows for files to be uploaded and attached to the transaction, an <b>Attach uploaded file(s)</b> selection list will appear so you can include any of those files to the email as well.</li></ul>

Click the <b>Ok</b> button to keep your changes, or click <b>Cancel</b>.<br>
<br>
Click the <b>Close</b> button to close the send email actions window.<br>
<br>
Click the <b>Delete</b> button to delete the selected action.<br>
<br>
Note that you can send multiple emails at the same time using this view.<br>
<br>
<i>Tip: To save your changes, you will want to click the <b>Ok</b> button on the custom logic rule as well as click the <b>Save</b> button for the package.</i>

<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

<h3>HTTP send data action</h3>

When you need to send data to another system (integration of applications), use the <b>HTTP send data</b> action. Click the <b>Add HTTP Send</b> button <img src='http://open.esignforms.com/images/HowToGuidesWiki/addHTTPSendButton.png' /> to add a new set of data to send to a specific URL. Or you can click on a previously created rule to update it.<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/HTTPSendAction.png' />

<ul><li>For <b>Method</b> choose the HTTP method to send the data to the specified URL, either a GET or a POST. In general, use POST unless a GET is all that you can use as GET requests will generally record all of your data parameters into web server logs that may not be secure if the data you are sending should be secure.<br>
</li><li>For <b>URL</b> specify the URL that will accept your data. It must begin with <code>http://</code> (data is in the clear over the Internet) or <code>https://</code> (data will be encrypted over the Internet), then have the server domain name and optional port number, along with any path specifiers. Alternatively, you can start with <code>${urlspec}</code> that expands to the URL. You can even include some hard-coded name-value params with optional field specs.  A typical URL looks like <code>https://open.esignforms.com/demo/HttpVariableTester.jsp</code>.  Note that every deployment has just such an URL available using your deployment's server name and application name. You can use this when testing as it will echo back all of the data it receives and can be used to help ensure you are sending the data you expect. If your URL needs to change based on Test versus Production modes, we recommend using a propertyset to configure the URL so that when in test mode it will use the same property name with <code>_TEST</code> added as a suffix. You can then set the HTTP Send Action's URL to something like <code>${property:MyConfig.URL}</code> which will expand at run-time (and when in test mode, it will automatically find property <code>MyConfig.URL_TEST</code> if you have defined it).<br>
</li><li>For <b>Max attempts</b> enter the number of times to attempt to send the data. Each attempt is recorded, including both the request sent and the response received. If the attempt is considered a success, no further attempts will be made.  If the attempt is not considered a success, it will try again if you specify a value greater than 1.<br>
</li><li>For <b>Retry (minutes)</b> select the number of minutes that should pass before a retry is attempted. This only has meaning if <b>Max attempts</b> is greater than 1.<br>
</li><li>For <b>Limit successful HTTP status codes</b> enter one or more numbers (standard HTTP status codes) separated by semicolons (;) that must be returned by the URL to indicate a successful send. Note that '200' is the normal HTTP status for a successful request. Leave this field blank if the HTTP status code should be ignored.<br>
</li><li>For <b>Purpose/reason spec</b> enter a literal and/or field specification that explains why the HTTP Send is taking place. The reason appears in the transaction activity log.<br>
</li><li>For <b>Match type</b> select the type of match to apply to the response returned from the URL to determine if it was a successful request.<br>
<ul><li>The match type <b>Anything</b> means that any response would indicate a success (this is not recommended unless you can rely on the HTTP status codes instead).<br>
</li><li><b>Must contain</b> means that the response must contain the associated value somewhere in the response to be considered successful.<br>
</li><li><b>Must not contain</b> means that the response must not contain the associated value anywhere in the response to be considered successful.<br>
</li><li><b>Must start with</b> means that the response must start with the associated value to be considered successful.<br>
</li><li><b>Must not start with</b> means that the response must not start with the associated value to be considered successful.<br>
</li><li><b>Must match regular expression</b> means that the <a href='http://docs.oracle.com/javase/tutorial/essential/regex/'>Java regular expression</a> must find a match in the response to be considered successful.<br>
</li><li><b>Must not match regular expression</b> means that the <a href='http://docs.oracle.com/javase/tutorial/essential/regex/'>Java regular expression</a> must not find a match in the response to be considered successful.<br>
</li></ul></li><li>For <b>Successful response it matches this value</b> specify a literal string (or a regular expression if the match type is for a regular expression) to apply based on the selected match type. This is generally a value that is included in the response that indicates it was successfully received.</li></ul>

<i>(See below for more information about specifying the name-value pairs to send.)</i>

Click the <b>Ok</b> button to keep your changes, or click <b>Cancel</b>.<br>
<br>
Click the <b>Close</b> button to close the HTTP send action window.<br>
<br>
Click the <b>Delete</b> button to delete the selected action.<br>
<br>
Note that you can send multiple HTTP requests at the same time using this view.<br>
<br>
<i>Tip: To save your changes, you will want to click the <b>Ok</b> button on the custom logic rule as well as click the <b>Save</b> button for the package.</i>

<h4>HTTP Send name-value params to send</h4>

Next, you need to specify the data you'd like to include in the HTTP(s) GET/POST request that is sent out.<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/HTTPSendNameValueList.png' />

You can use drag and drop to reorder the list of fields shown.<br>
<br>
Click on a row to modify it. You are free to change the param name to match the name expected by the receiving system (at the URL specified).<br>
<br>
For document fields, you may optionally change the format for the field. By default, it will use the field's definition in the document (it's output/display format), which basically matches what the parties see when completing the document.  But if you need a different format for the receiving system, you can adjust it here.<br>
<br>
For literal/field specs, you can also update the value to the specified literal string or field specification using <code>${}</code> notation.<br>
<br>
Click the <b>Ok</b> button to accept and changes made. Click the <b>Cancel</b> button to ignore any changes made.  Click the <b>Delete</b> button to delete the name-value from being included in the HTTP Send.<br>
<br>
<h4>Add literals or field specifications <img src='http://open.esignforms.com/images/HowToGuidesWiki/addLiteralOrFieldSpecButton.png' /></h4>

For the HTTP Send Action, use the <b>Add literal or field spec</b> button to add one literal (with or without a field specification using <code>${}</code> notation) to be sent. You will have to update the name and value by clicking on it from the list.<br>
<br>
<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

<h4>Add document fields <img src='http://open.esignforms.com/images/HowToGuidesWiki/addDocumentFieldsButton.png' /></h4>

For the HTTP Send Action, use the <b>Add document fields...</b> button to add one or more fields from your document(s) to be sent.<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/HTTPSendDocumentFieldsSelector.png' />

<ul><li>For <b>Choose a document</b> select the document that has the fields you'd like to send out.<br>
</li><li>For <b>Select fields to add</b> click on one or more fields from the selected document to send out.</li></ul>

Click the <b>Add</b> button to add the selected fields to be sent out.  Click <b>Cancel</b> to not add any fields.<br>
<br>
If the document field is a File type (for uploaded files), the param name you specify will be associated with the BASE-64 encoded file data. Two additional params are automatically included by appending <code>__fileName</code> and <code>__fileMimeType</code> to your file field's param name to supply the respective file name and mime type as it was uploaded. If multiple files were uploaded, you will receive the set of 3 params multiple times (on the receiving end, this often appears as receiving an array of values).  So if your File field param name is <code>attachment</code> then for each uploaded file associated with the field, you'll get params: <code>attachment</code> and <code>attachment__fileName</code> and <code>attachment__fileMimeType</code>.  Note two underbars are used between the param name you supply and these additional fields.<br>
<br>
<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

<h4>Add completed documents <img src='http://open.esignforms.com/images/HowToGuidesWiki/addCompletedDocumentsButton.png' /></h4>

For the HTTP Send Action, use the <b>Add completed documents...</b> button to add one or more document(s) to be sent.<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/HTTPSendCompletedDocumentsSelector.png' />

<ul><li>For <b>Completed document(s)</b> select one or more completed documents that you'd like to send out. Note you can send any version based on a particular party or the latest party. If multiple documents are selected, you will get multiple 'Param name' param-values sent except for the PDF format that combines them into a single file. Note that if you select a 'Latest' version that happens to be the same version as the a selected party-specific version, only one copy will be sent. Also, if no version exists for a given party (it hasn't taken place yet), no value will be sent with the 'Param name'.<br>
</li><li>For <b>Param name</b> select the name of the parameter that will be used. It defaults to 'document'.<br>
</li><li>For <b>Type to send</b> select the type of document to send. Use 'Document (HTML)' to send the original HTML document the party completed. Use 'Document(PDF)' to send over the selected documents as a combined PDF file.  Use 'Data (XML)' to send over the document's data in XML format. Or use 'Snapshots (XML DSig)' to send over the document and data snapshots as XML, both including their XML digital signatures.</li></ul>

Note that all documents are sent using Base-64 encoding.<br>
<br>
Base-64 encoding converts data into an ASCII format, essentially emitting 4 ASCII characters for every 3 input bytes. It has only three special characters: <code>+</code>, <code>/</code> and <code>=</code> (the equals sign for padding at the end only), but oddly enough all three have special meaning in URLs (and for URL encoding for name-value params for HTTPS GET/POST). Therefore, when viewing the Base-64 encoded data in the HTTP Send logs, you will see URL-encode Base-64, so <code>+</code> is replaced by <code>%2B</code>, <code>/</code> is replaced by <code>%2F</code> and <code>=</code> is replaced by <code>%3D</code>.<br>
<br>
Click the <b>Add</b> button to add the selected documents to be sent out.  Click <b>Cancel</b> to not add any documents.<br>
<br>
<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

<h4>Add party LINKs <img src='http://open.esignforms.com/images/HowToGuidesWiki/addPartyLINKsButton.png' /></h4>

For the HTTP Send Action, use the <b>Add party LINKs...</b> button to add one or more party pick up links to be sent.<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/HTTPSendPartyLINKsSelector.png' />

<ul><li>For <b>LINK for parties</b> select one or more parties whose pick up LINK you'd like to send out. If multiple parties are selected, you will get multiple 'param name' params sent.<br>
</li><li>For <b>Param name</b> select the name of the parameter that will be used. It defaults to 'partyLink'.</li></ul>

Click the <b>Add</b> button to add the selected parties' pick up LINKs to be sent out.  Click <b>Cancel</b> to not add any party links.<br>
<br>
<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

<h3>Change tran/party status action</h3>

When you need to cancel a transaction (now or in the future), skip a document, skip a party step in your workflow, or activate a party step ahead of its normal workflow sequence, use the <b>Change tran/party status</b> action. Click the <b>Add status change</b> button <img src='http://open.esignforms.com/images/HowToGuidesWiki/addStatusChangeButton.png' /> to add a new status change. Or you can click on a previously created rule to update it.<br>
<br>
<h4>Cancel transaction action</h4>

Change the <b>Status change type</b> to 'Cancel transaction':<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/cancelTransactionAction.png' />

<ul><li>For <b>Status change type</b> choose 'Cancel transaction'.<br>
</li><li>For <b>#</b> specify the number of <b>Cancel time</b> units before the transaction is canceled. This has no meaning for Now or Forever cancel times.<br>
</li><li>For <b>Cancel time</b> choose when the transaction should be canceled. If you select Now, the transaction will be canceled when this action takes place. You can specify a future date so it will cancel automatically in the future if it's not completed or the cancel transaction is turned off later.<br>
</li><li>For <b>Reason spec</b> provide a reason (it can include field specifications <code>${ }</code> for variable substitution) why the transaction is being canceled. The reason appears in the transaction activity log.<br>
</li><li>If you'd like to reduce the default retention for such auto-canceled transactions (from the value set in the transaction template for production/test modes), check <b>Reduce retention on cancel</b> and choose a new retention value. This is generally used to remove new transactions that do not get past the first step.</li></ul>

<h4>Clear cancel transaction action</h4>

If you set a future date for a transaction to auto-cancel if it has not yet completed, you can clear the auto-cancel requested earlier. This is often done when you want a transaction to auto-cancel if the first party does not complete the documents in a specified amount of time, but if they do complete it, then you want it to go forward normally and no longer need to complete within the original timeframe.<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/clearCancelTransactionAction.png' />

<ul><li>For <b>Status change type</b> choose 'Clear cancel transaction'.<br>
</li><li>For <b>Reason spec</b> provide a reason (it can include field specifications <code>${ }</code> for variable substitution) why the transaction is no longer going to be canceled. The reason appears in the transaction activity log.</li></ul>

<h4>Skip document action</h4>

Change the <b>Status change type</b> to 'Skip document':<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/skipDocumentAction.png' />

<ul><li>For <b>Status change type</b> choose 'Skip document'.<br>
</li><li>For <b>Reason spec</b> provide a reason (it can include field specifications <code>${ }</code> for variable substitution) why the document is being skipped. The reason appears in the transaction activity log.<br>
</li><li>For <b>Documents to skip</b> select one or more documents to skip.</li></ul>

Click the <b>Ok</b> button to keep your changes, or click <b>Cancel</b>.<br>
<br>
Click the <b>Close</b> button to close the transaction/party status change window.<br>
<br>
Click the <b>Delete</b> button to delete the selected action.<br>
<br>
Note that you can do multiple status change actions using this view.<br>
<br>
<h4>Skip party action</h4>

Change the <b>Status change type</b> to 'Skip party':<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/skipPartyAction.png' />

<ul><li>For <b>Status change type</b> choose 'Skip party'.<br>
</li><li>For <b>Reason spec</b> provide a reason (it can include field specifications <code>${ }</code> for variable substitution) why the party is being skipped. The reason appears in the transaction activity log.<br>
</li><li>For <b>Parties to skip</b> select one or more parties to skip.</li></ul>

Click the <b>Ok</b> button to keep your changes, or click <b>Cancel</b>.<br>
<br>
Click the <b>Close</b> button to close the transaction/party status change window.<br>
<br>
Click the <b>Delete</b> button to delete the selected action.<br>
<br>
Note that you can do multiple status change actions using this view.<br>
<br>
<i>Tip: To save your changes, you will want to click the <b>Ok</b> button on the custom logic rule as well as click the <b>Save</b> button for the package.</i>

<h4>Activate party action</h4>

If a party needs to be activated before it normally would be activated in party sequence, you can use this action to activate a party. Generally this is used for "final step" parties who will access the transaction for review purposes only.<br>
<br>
Change the <b>Status change type</b> to 'Activate party':<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/activatePartyAction.png' />

<ul><li>For <b>Status change type</b> choose 'Activate party'.<br>
</li><li>For <b>Reason spec</b> provide a reason (it can include field specifications <code>${ }</code> for variable substitution) why the party is being activated (out of the normal party order). The reason appears in the transaction activity log.<br>
</li><li>For <b>Parties to skip</b> select one or more parties to skip.</li></ul>

Click the <b>Ok</b> button to keep your changes, or click <b>Cancel</b>.<br>
<br>
Click the <b>Close</b> button to close the transaction/party status change window.<br>
<br>
Click the <b>Delete</b> button to delete the selected action.<br>
<br>
Note that you can do multiple status change actions using this view.<br>
<br>
<i>Tip: To save your changes, you will want to click the <b>Ok</b> button on the custom logic rule as well as click the <b>Save</b> button for the package.</i>

<h3>Show error/message action</h3>

When you need to display a message or report a custom data validation error, the show error/message action can be used. For data validations, you should use this action in a rule that specifies the <b>Party review document</b> event.<br>
<br>
If you report an error or warning on the review step, the user will not be able to complete the document until it is fixed so it no longer matches the condition specified with this action. You can also only highlight fields when doing an error or warning to call attention to the field.<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/showErrorAction.png' />

<ul><li>For <b>Error/message spec</b> enter the message or error to show the user. It may contain field specifications (${}).<br>
</li><li>Choose the message type: <b>Error</b>, <b>Warning</b>, <b>Success</b> or <b>Info</b>.<br>
</li><li>Check <b>HTML?</b> if the error/message is in HTML format already (contains HTML tags). Leave it blank normally.</li></ul>

Click the <b>Ok</b> button to keep your changes, or click <b>Cancel</b>.<br>
<br>
Click the <b>Close</b> button to close the send email actions window.<br>
<br>
Click the <b>Delete</b> button to delete the selected action.<br>
<br>
Note that you can show multiple messages at the same time using this view.<br>
<br>
<i>Tip: To save your changes, you will want to click the <b>Ok</b> button on the custom logic rule as well as click the <b>Save</b> button for the package.</i>

<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

<h3>Pay Pal direct charge action</h3>

When you need to charge a credit card using your PayPal Web Site Pro account, use the <b>PayPal direct charge</b> action. Click the <b>Add PayPal charge</b> button <img src='http://open.esignforms.com/images/HowToGuidesWiki/paypalChargeButton.png' /> to add a new payment to be charged. Or you can click on a previously created rule to update it.<br>
<br>
This action depends on you having previously configured a Property Set named <b>PayPal_NVP_API</b> with properties for LogNVP, PWD, SIGNATURE, USER and URL that are part of the PayPal NVP API service. There's a corresponding "<i>TEST" property that is used for test transactions and is generally pointed to the PayPal Sandbox where testing can take place without actually doing a credit card charge.</i>(When you order this service from PayPal so you can charge cards directly, you will be given a PWD, SIGNATURE and USER to authenticate the API calls and ensure the money is credited to your account.)<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/PayPalChargeAction.png' />

<ul><li>For <b>Customer name spec</b> enter a fixed value or a field specification of the customer name (like the company name, not the billing name, though it can be the same). This sets the CUSTOM field in the PayPal NVP API. It is optional.<br>
</li><li>For <b>Purchase description spec</b> enter a fixed value or a field specification of the item that has been purchased. This sets the DESC field in the PayPal NVP API. It is optional and will default to "Online sale" if not specified.<br>
</li><li>For <b>Buyer email address spec</b> enter a fixed value or a field specification of the buyer's email address This sets the EMAIL field in the PayPal NVP API. It is optional.<br>
</li><li>For <b>Invoice number spec</b> enter a fixed value or a field specification of your invoice/order number that goes with this sale. This sets the INVNUM field in the PayPal NVP API. It is optional and will default to the transaction id.</li></ul>

For all of the following fields, the user should enter the billing information, not their personal information, so that it matches the names and addresses associated with their credit card. They are required unless noted otherwise.<br>
<br>
<ul><li>For <b>In document</b> and <b>First name</b> select the document and field that contains the billing first name.<br>
</li><li>For <b>In document</b> and <b>Last name</b> select the document and field that contains the billing last name.<br>
</li><li>For <b>In document</b> and <b>Street line 1</b> select the document and field that contains the billing street address (line 1).<br>
</li><li>For <b>In document</b> and <b>Street line 2</b> select the document and field that contains the billing street address (line 2). This is optional.<br>
</li><li>For <b>In document</b> and <b>City</b> select the document and field that contains the billing city.<br>
</li><li>For <b>In document</b> and <b>State/province</b> select the document and field that contains the billing state or province.<br>
</li><li>For <b>In document</b> and <b>Zip/postal code</b> select the document and "Zip code" field that contains the billing zip code or postal code.<br>
</li><li>For <b>In document</b> and <b>Country</b> select the document and field that contains the billing country (2-letter code). It is optional and defaults to "US". You may want to use the standard drop down <b>ESF_Countries</b> or a modified version of this list.<br>
</li><li>For <b>In document</b> and <b>Card type</b> select the document and field that contains the credit card type (Visa, MasterCard, Amex, Discover). It is optional and defaults to a calculated value based on the the card number. A standard drop down named <b>ESF_PayPal_CardTypes</b> has these for easy use. Note that American Express requires a separate agreement with PayPal and American Express to offer it.<br>
</li><li>For <b>In document</b> and <b>Card number</b> select the document and "credit card number" field that contains the credit card number. For PCI compliance, it is recommend that this value be masked on review as well as overwritten on successful payment so that it is not stored.<br>
</li><li>For <b>In document</b> and <b>Expiration date</b> select the document and "date" field that contains the credit card expiration date in MM/YYYY format. The date formats allow for this type of entry. A party can select any day of the month if using date selector.<br>
</li><li>For <b>In document</b> and <b>Security code</b> select the document and field that contains the credit card security id (aka CCV or CVV), a 3-4 digit number printed on the card itself (on the front for American Express, and on the back otherwise). It is optional, but may be required to successfully do a charge to prove that the card was present for the online purchase. This field should also be masked on review and must be masked out on successful payment because PCI compliance requires that it not be stored once the payment is done.<br>
</li><li>For <b>In document</b> and <b>Amount to charge</b> select the document and "money" field that contains the amount to be charged. PayPal has a default max of $10,000 that is allowed.<br>
</li><li>For <b>On success mask</b> we recommend you check both the <b>Card number</b> and <b>Security code</b> since they are not needed after the charge and PCI compliance generally requires it.<br>
</li><li>For <b>Show on success</b> enter a message (with field specs if desired) that will be displayed after a successful payment is made.<br>
</li><li>For <b>Show on failure</b> enter an error message (with field specs if desired) that will be displayed if there's an error with the charge.</li></ul>

On a successful payment, the PAYPAL_TRANSACTIONID field will be set with the transaction id (not to be confused with the Open eSignForms transaction id related to your completed form) returned. It will be blank on error.<br>
<br>
On error (no charge takes place), the PAYPAL_EXCEPTION field will be set with the error returned by PayPal. It will be blank on success.<br>
<br>
Additional fields set from the PayPal response include PAYPAL_ACK, PAYPAL_AMT, PAYPAL_AVSCODE and PAYPAL_CVV2MATCH. In addition, two related fields are set with more meaningful values using PAYPAL_AVSCODE_MEANING and PAPAL_CVV2MATCH_MEANING.<br>
<br>
Click the <b>Ok</b> button to keep your changes, or click <b>Cancel</b>.<br>
<br>
Click the <b>Close</b> button to close the PayPal payment actions window.<br>
<br>
Click the <b>Delete</b> button to delete the selected action.<br>
<br>
Note that you can do multiple charges at the same time using this view.<br>
<br>
<i>Tip: To save your changes, you will want to click the <b>Ok</b> button on the custom logic rule as well as click the <b>Save</b> button for the package.</i>

<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

<h3>Change File field access action</h3>

The default behavior for all parties who do not have access to upload files is to view/download all previously uploaded files. Just as all subsequent parties see all data fields, they are also required to view all attached files. This action can be used to change that behavior when it's not desired.<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/changeFileFieldAccessAction.png' />

<ul><li>In <b>In document</b> select the document where the file upload field is defined.<br>
</li><li>In <b>File field</b> select the File Upload field to change.<br>
</li><li>In <b>Party</b> select the party whose access is being changed.<br>
</li><li>Select either <b>Make view/download optional</b> if the party will not be required to view/download the files, or <b>Block view/download</b> if the party should not be allowed to view/download the files.</li></ul>

Click the <b>Ok</b> button to keep your changes, or click <b>Cancel</b>.<br>
<br>
Click the <b>Close</b> button to close the Change File field action window.<br>
<br>
Click the <b>Delete</b> button to delete the selected action.<br>
<br>
Note that you can set multiple parties and file upload fields to skip at the same time using this view.<br>
<br>
<i>Tip: To save your changes, you will want to click the <b>Ok</b> button on the custom logic rule as well as click the <b>Save</b> button for the package.</i>

<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

<h3>Set/cancel timer action</h3>

When you need to set a timer to trigger a future action, or to cancel an existing named timer, or to cancel all timers, use the <b>Set/cancel timer</b> action.  Click the <b>Add timer action</b> button <img src='http://open.esignforms.com/images/HowToGuidesWiki/addTimerActionButton.png' /> to add a new timer action. Or you can click on a previously created action to update it.<br>
<br>
<h4>Set timer action</h4>

Change the <b>Timer type</b> to 'Set timer':<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/setTimerAction.png' />

<ul><li>For <b>Timer type</b> choose 'Set timer'.<br>
</li><li>For <b>Timer name</b> specify the name for this timer. The name is not case sensitive. You may use this name to reset the timer in another 'Set timer action' using the same name, or you can use it to cancel the timer.<br>
</li><li>For <b>Expire timestamp spec</b> specify a date-time field specification <code>${ }</code> that holds the date-time the timer should expire, or use literals like +1 to mean 1 day from now. Time values like 'now' and '+0' or any negative time specification will cause the timer to fire soon after. Note that a timer will not necessarily fire exactly at the specified time, but it should fire within a minute of the time specified.<br>
</li><li>For <b>Reason spec</b> provide a reason (it can include field specifications <code>${ }</code> for variable substitution) why the timer is being set. The reason appears in the transaction activity log.</li></ul>

<h4>Cancel timer action</h4>

Change the <b>Timer type</b> to 'Cancel timer':<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/cancelTimerAction.png' />

<ul><li>For <b>Timer type</b> choose 'Cancel timer'.<br>
</li><li>For <b>Timer name</b> specify the name for a previously set timer. The name is not case sensitive.<br>
</li><li>For <b>Reason spec</b> provide a reason (it can include field specifications <code>${ }</code> for variable substitution) why the timer is being canceled. The reason appears in the transaction activity log.</li></ul>

<h4>Cancel all timers action</h4>

Change the <b>Timer type</b> to 'Cancel all timers':<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/cancelAllTimersAction.png' />

<ul><li>For <b>Timer type</b> choose 'Cancel all timers'.<br>
</li><li>For <b>Reason spec</b> provide a reason (it can include field specifications <code>${ }</code> for variable substitution) why all timers are being canceled. The reason appears in the transaction activity log.</li></ul>

<h3>Common conditional scenarios</h3>

<h4>Make a field required only if another field is set to a value</h4>

Sometimes a field is only required if some other field is set to a given value.  In this case, configure the field itself as optional, and then add a Condition+Action as follows:<br>
<br>
Assume a checkbox named 'cb'. If checked, then a general field named 'other' is required, otherwise it's optional.<br>
<br>
<ol><li>In the field specification, make 'other' optional so it doesn't force it to be required.<br>
</li><li>Create a rule for the event "Party review document".<br>
</li><li>Add the action "Show error/message".<br>
</li><li>Right-click on the AND condition of the Action to add a "Comparison" check. Select the 'cb' field and check if it's equal to its checked value (by default it's 'Y'): cb EQUALS Y<br>
</li><li>Right-click on the AND condition to add an "All fields blank" condition and specify the field 'other'.  These two conditions basically mean: IF the 'cb' checkbox is checked AND the 'other' field is blank, THEN display an error message saying it's required.<br>
</li><li>Next, set the error message to show the user to have them complete the field.<br>
</li><li>Mark this as an error or warning so that it will block the party from going into review mode when it's displayed.<br>
</li><li>Select the 'cb' and 'other' fields to highlight them to call attention to why the "required error" is being displayed.</li></ol>

<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

<h2>Map report fields</h2>

By default, all fields in your documents are fully encrypted and can only be accessed by a given package party in a transaction. However, often you may want some fields to be available for <a href='UserGuide#Reports.md'>reports</a> or shown in the <a href='UserGuide#To_Do.md'>To Do queue</a>. For these reasons, you can map fields from the package to report fields.<br>
<br>
Each time a transaction is saved (updated by a package party), all of the field mappings are applied so that reports will have the latest field values.<br>
<br>
This also lets you map various fields that may be named "SSN", "SocialSecurityNumber", "so_sec_no" or "Tax_ID" to a single report field name so that you can create a report that essentially merges all such fields into a single report field. Use care when mapping such fields so that you map them to a common set of report fields and don't create multiple report fields that really have the same meaning.<br>
<br>
Click on the <b>Report field templates</b> button <img src='http://open.esignforms.com/images/HowToGuidesWiki/reportFieldTemplatesButton.png' /> to list all <a href='#Report_field_templates.md'>report field templates</a> and see where it's used, or to just change the name.<br>
<br>
Click the <b>Map report fields</b> button on the package version to set up mappings to report fields.<br>
<br>
Click on the <b>Map new report field</b> button <img src='http://open.esignforms.com/images/HowToGuidesWiki/mapNewReportFieldButton.png' /> to add map a new report field. Or you can click on a previously created mapping to update it.<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/packageMapReportFields.png' />

You can drag to re-order existing field mappings to control the order they will appear in the To Do listing. Otherwise, the order does not matter.<br>
<br>
<ul><li>In the <b>Document</b> drop down select the document from the package where the field to be mapped resides.<br>
</li><li>In the <b>Field</b> drop down select the field in the selected document to map to a report field.<br>
</li><li>In the <b>Save value as report field</b> drop down, select an existing report field that applies. If no such report field exists, type a new name (a + will appear before the name to indicate it's being created new if not already present) to create a new report field with an appropriate type.<br>
</li><li>Check <b>Show To Do</b> to have this field appear in the To Do queue for internal users who will process transactions this way.</li></ul>

Click the <b>Ok</b> button to keep your changes (you will need to do this if you re-order fields, too). Otherwise click <b>Cancel</b> to discard them.<br>
<br>
Click <b>Close</b> to close the data field mapping window.<br>
<br>
Click <b>Delete</b> to delete the selected field mapping.<br>
<br>
You can also click the <b><a href='#Reload_transaction_report_fields.md'>Reload tran report fields</a></b> button <img src='http://open.esignforms.com/images/HowToGuidesWiki/reloadTranReportFieldsButton.png' /> to reload existing transactions should you have created new mappings after previous transactions were completed. Since report fields are only mapped when a transaction is updated, newly mapped fields won't be available to the reports for older transactions (or in progress transactions until a party next accesses it) unless you manually reload them here.<br>
<br>
Note, too, that you can update the report field mappings and reload transactions that use a given package version at any time, including updating the current production version as well as older versions.  Report fields do not change the processing logic and thus can be modified at any time, not just for test versions.<br>
<br>
<i>Tip: To save your changes, remember to click the <b>Save</b> button for the package.</i>

<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

<h3>Reload transaction report fields</h3>

To manually reload report fields for existing transactions using the current field mappings, click the <b>Reload tran report fields</b> button from the <a href='#Map_report_fields.md'>package's map report fields</a> window.<br>
<br>
This will find all matching transactions, and then reload all defined report fields in its related package version. If you have previous package versions and you need transactions based on the older package version to also be reloaded, be sure you have mapped the fields in those package versions as well. If you update multiple package versions, you only need to run the reload once (not once per package version).<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/reloadTranReportFields.png' />

<ul><li>Select which transaction type(s) should be reloaded. Only those transactions you have access to and which use this package are listed.<br>
</li><li>If your current mode is <b>PRODUCTION: Live</b>, this will reload production transactions, otherwise it will reload test transactions.<br>
</li><li>Select the type of date and date range to limit which transactions are reloaded.<br>
</li><li>In <b>Tran id only reload</b> enter a single transaction id to reload only that one specific transaction. Otherwise leave it blank.<br>
</li><li>In <b>Party email</b> enter the email address of a party to limit the reload to just those transactions. Otherwise leave it blank.<br>
</li><li>Check <b>In progress</b> to reload transactions that are in progress.<br>
</li><li>Check <b>Completed</b> to reload transactions that are already completed.<br>
</li><li>Check <b>Canceled</b> to reload transactions that are canceled.<br>
</li><li>Check <b>Suspended</b> to reload transactions that are suspended.</li></ul>

Click the <b>Reload report fields for matching transactions</b> button to begin the reload.<br>
<br>
<i>Note that this process can take a long time based on the number of transactions that will match your selection criteria. (This process includes first finding all matching transactions, then loading each one, decrypting all of its data, parsing its XML structure, and then running the field mapping specifications.) Whenever possible, define all report field mappings before you start transactions, and if you do create new mappings later, attempt to limit the number of transactions that must be reloaded. You only need to reload them if you have reports or To Do transactions that otherwise show a blank field because the mapping was not in place when those transactions were last updated.</i>

<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

<h2>Package import configuration</h2>

When you import a package configuration, all previous documents, parties, etc. are removed from the package and replaced by the imported configuration.<br>
<br>
<img src='http://open.esignforms.com/images/HowToGuidesWiki/packageImportConfiguration.png' />

First, select the default library in your system where documents in the package are already defined. When a document is imported, the system will first look for the document in this library. If it's not found, it will attempt to scan your libraries for a matching document name.<br>
<br>
Click the <b>Upload package version XML</b> to select the package version XML file on your computer to upload. Review the messages after the import and then close the window to return to the package configuration.<br>
<br>
<i>Tip: To save your changes, remember to click the <b>Save</b> button for the package.</i>

<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>
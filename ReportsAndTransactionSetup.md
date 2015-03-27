<table width='100%'><tr>
<td width='50%'><a href='http://open.esignforms.com'><img src='http://open.esignforms.com/images/OpenESignFormsLogo.gif' /></a></td>
<td width='50%' align='right'><a href='http://www.yozons.com'><img src='http://www.yozons.com/images/logoSmall.gif' /></a></td>
</tr></table>

<h1>Reports and Transaction Setup Guide</h1>

#### How-To Guides ####
  * [Concepts, Tips & Tricks](HowToGuides.md) (Read first)
  * [User's Guide](UserGuide.md) (Read first)
  * [System Administrator's Guide](SystemAdminGuide.md)
  * [Point & Click Programming Guide](ProgrammingGuide.md)
  * **[Reports and Transaction Setup Guide](ReportsAndTransactionSetup.md)** (this guide)
  * [Point & Click Programming Integration API Guide](ProgrammingGuide_Integration_API.md)
  * [Point & Click Programming Tutorial](ProgrammingTutorial.md)

#### Table of contents ####


# Introduction #

Report templates and transaction templates are setup under the [Programming tab](ProgrammingGuide.md).

Report fields are first mapped in Packages before they are added to reports.  That is, you must define which fields in your package of documents can be reported on.

And Packages are defined before specified as a runnable transaction using transaction templates.

# Transaction Templates ![http://open.esignforms.com/images/HowToGuidesWiki/tranTemplateIcon.png](http://open.esignforms.com/images/HowToGuidesWiki/tranTemplateIcon.png) #

Transaction templates are used to define a runnable package of documents.

Click on **Programming->Tran templates** to list all transactions templates available to you.

Click on a transaction template to view or configure it. To create a new transaction template, select a template or similar existing transaction template you have permission to access and click the **Create like** button.

![http://open.esignforms.com/images/HowToGuidesWiki/transactionTemplate.png](http://open.esignforms.com/images/HowToGuidesWiki/transactionTemplate.png)

  * Select **Production enabled** if you are ready to run production-level transactions. Your package must be at the production level, and you should also ensure all components used by the package are also at the production level. When you first enable production transactions, please run a "Test Like Production" transaction to see how it works using only production-level components.  Select **Production disabled** to prevent production transactions from starting.
  * Enter a **#** number and **Production retention** value to specify how long to keep production transactions. If you select "Forever" or "Now", the number field will not be necessary. Use of "Now" makes little sense in this context. **_Be very careful when reducing the retention for production transactions because it will update all existing production transactions of this type to use the new value._**
  * Select **Test enabled** if you are ready to run testing-only transactions. You will then be able to run test transactions. Select **Test disabled** to prevent test transactions from starting.
  * Enter a **#** number and **Test retention** value to specify how long to keep test transactions. If you select "Forever" or "Now", the number field will not be necessary. Use of "Now" makes little sense in this context. We recommend shorter retention values for test transactions, such as keeping them for 3 to 6 months. This will update all existing test transactions of this type to use the new retention value.
  * In **PathName** enter the name of this transaction template. It will be displayed under the **[Start transaction](UserGuide#Start_a_transaction.md)** menu item.
  * In **Display name** put a friendly name to display for this transaction type. This name will be used in the menu display under the **Start transaction** option.
  * In **Description** give a brief overview of what this transaction is.
  * In **Package to use** select the package that will be run.
  * In **Branding library to use** select the library to be searched first to resolve components like images/logos, property sets, To Do parties, email templates, etc. If those items are not found in the branding library, it will look in the library where the current  document is defined, and then **ESF/Library/Template** last.
  * In **Comments** enter any information you want to maintain about the transaction.

The transaction template has standard List, View Details, Create Like, Update and Delete permissions under **Permissions to access this transaction template**.

It also has special permissions related to the transactions that are specified under **Permissions for transaction**

  * **Start** permission specifies who can start the transaction. Specify **ESF/Group/ExternalUsers** to allow non-authenticated users to start the transaction, such as from a link on your web site.
  * **Cancel** permission specifies who can cancel a running transaction.
  * **Re-Activate** permission specifies who can re-activate a canceled transaction.
  * **Suspend** permission specifies who can suspend a running transaction.
  * **Resume** permission specifies who can resume a suspended transaction.

On the lower left side are URLs that can be used to start a transaction of this type. The **Production URL** is the base URL used to start a transaction.  The **Test URL** adds the `ESFTEST=Yes` parameter. And the **Test like Production URL** adds the `ESFLIKEPRODUCTION=Yes` parameter to the Test URL.

<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

# Report Templates ![http://open.esignforms.com/images/HowToGuidesWiki/reportTemplateIcon.png](http://open.esignforms.com/images/HowToGuidesWiki/reportTemplateIcon.png) #

Report templates are used to define a custom report that lists data elements about and from within the package of document specified in a transaction template. You must first [map data elements in the package to report fields](ProgrammingGuide#Map_report_fields.md) to list them in a custom report.

Click on **Programming->Report templates** to list all report templates available to you.

Click on a report template to view or configure it. To create a new report template, select a template or similar existing report template you have permission to access and click the **Create like** button.

![http://open.esignforms.com/images/HowToGuidesWiki/reportTemplate.png](http://open.esignforms.com/images/HowToGuidesWiki/reportTemplate.png)

  * Click **Enabled** to allow this report to be run. Click **Disabled** to prevent it from running.
  * In **PathName** give this report template a name. The name will appear under **[Reports](UserGuide#Reports.md)** menu item.
  * In **Display name** enter a friendly name for this report. It will be shown in the menu under **Reports**.
  * In **Description** enter a short description of this report.
  * In **Comments** enter any information you want to remember about this report.
  * In **Tran templates** select one or more transaction types to be included this report. Of course, for the report to run as expected, the report fields must make sense across the various transaction types. Any report field that is not mapped by the transaction's package will be blank in the report.
  * In **Limit access to selected documents** select all documents that should be made available to those running the report. By default, no limits are in place, so all documents in the selected transactions are made available. However, there may be times when a report for a particular set of users must limit access to only a subset of documents, and this allows such a limit to be configured.

The report template has standard List, View Details, Create Like, Update and Delete permissions under **Permissions to access this report template**.

It also has special permissions related to the reports that are specified under **Permissions for reports**

  * **Run** permission specifies who can run the report. By default, users can only see test transactions they started themselves or they were a party to.
  * **See transactions started by external users** specifies who can also see transactions started by external users.
  * **See transactions started by any other user** specifies who can also see transactions started by any other user. Note that "any user" is limited to those users the user running the report is allowed to list.
  * **See transactions with any other user a party to** specifies who can also see transactions in which any other user was a party. Note that "any user" is limited to those users the user running the report is allowed to list.
  * **See Production Transactions as well as Test** specifies who can also see production transactions. By default, only Test transactions can be seen.
  * **Download report data in Excel or CSV format** specifies who can download report data in Excel or CSV formats.
  * **View transaction email log** specifies who can see email details about a transaction.
  * **View/download document snapshots** specifies who can see and download document snapshots.
  * **View/download data and uploaded files** specifies who can see and download data snapshots, which includes the data values stored in documents as well as files uploaded to a given field.
  * **Download complete transaction archives** specifies who can download a complete transaction archive.
  * **View live documents in a transaction** specifies who can view "live" documents in a transaction. By default, users only are allowed to see completed documents by each party (document snapshots created as each party completes a document). A "live" view means it will render the documents as they currently are.  Users with this permission will use the special ESF\_reports\_access party to view the documents. All document access is logged in the transaction's audit trail.
  * **Update live documents in a transaction** specifies who can update "live" documents in a transaction. By default, each party is able to update documents and fields based on their configuration when the party is active. A "live" view means it will render the documents as they currently are.  Users with this permission will use the special ESF\_reports\_access party to update the documents. All document access is logged in the transaction's audit trail. This feature is designed for transactions that are to be treated more like "records" that are updated repeatedly rather than for transactions that are processed by parties. However, it may be used to also correct data in a live transaction before subsequent parties access it. If a package doesn't define this party, one will be auto-created with view only access to all documents. You must specifically give the special ESF\_reports\_access party the ability to play an updating party in order to change any data. You may also define the party on a document to give it fine control over the fields and validation that take place for updating via the reports.

Click on the **[Fields in report](#Fields_in_report.md)** button ![http://open.esignforms.com/images/HowToGuidesWiki/fieldsInReportButton.png](http://open.esignforms.com/images/HowToGuidesWiki/fieldsInReportButton.png) to configure the report fields that will appear in the custom report.

<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

## Fields in report ##

Click the **Fields in report** button on the report template to set up the report fields to include in the custom report.

Click on the **Report field templates** button ![http://open.esignforms.com/images/HowToGuidesWiki/reportFieldTemplatesButton.png](http://open.esignforms.com/images/HowToGuidesWiki/reportFieldTemplatesButton.png) to list all [report field templates](#Report_field_templates.md) and see where it's used, or to just change the name.

Click on the **Add report field** button ![http://open.esignforms.com/images/HowToGuidesWiki/addReportFieldButton.png](http://open.esignforms.com/images/HowToGuidesWiki/addReportFieldButton.png) to add a new field. to the report. Or you can click on a previously created report field to update it.

![http://open.esignforms.com/images/HowToGuidesWiki/fieldsInReport.png](http://open.esignforms.com/images/HowToGuidesWiki/fieldsInReport.png)

You can drag to re-order existing fields to control the order they will appear in the report.

  * In **Report field** select a user-defined or built-in report field to show in the report. The following are the built-in fields:
    * **esf\_cancel\_timestamp** is the date/time the transaction was canceled.
    * **esf\_created\_by\_user** is the user who started the transaction, when it's not started by an external user.
    * **esf\_download\_html\_selected\_snapshot** will produce an "Completed docs" popup button that will produce a list of completed documents (by party, or latest) that when clicked will show that HTML document.
![http://open.esignforms.com/images/HowToGuidesWiki/completedDocAsHTMLButton.png](http://open.esignforms.com/images/HowToGuidesWiki/completedDocAsHTMLButton.png)
    * **esf\_download\_pdf\_latest\_snapshots** will produce an "All completed docs" button that will download a PDF containing all of the latest completed documents.
![http://open.esignforms.com/images/HowToGuidesWiki/allCompletedDocsAsPdfButton.png](http://open.esignforms.com/images/HowToGuidesWiki/allCompletedDocsAsPdfButton.png)
    * **esf\_download\_pdf\_selected\_snapshots** will produce a "Completed docs" dropdown button to select which completed documents and versions you want to download as a PDF. ![http://open.esignforms.com/images/HowToGuidesWiki/selectedCompletedDocsAsPdfButton.png](http://open.esignforms.com/images/HowToGuidesWiki/selectedCompletedDocsAsPdfButton.png)
    * **esf\_expire\_timestamp** is the date/time the transaction is set to expire and be deleted from the system (this is set based on the transaction template's retention values).
    * **esf\_last\_updated\_by\_user** is the user who last updated the transaction, when it's not last updated by an external user.
    * **esf\_last\_updated\_timestamp** is the date/time the transaction was last updated.
    * **esf\_literal** allows you to specify a fixed **Literal value** that will always appear in the column. This is mostly used for CSV integration with other systems where you need to provide a fixed value.
    * **esf\_package\_name** is the PathName of the package referenced by the transaction.
    * **esf\_stall\_timestamp** is the date/time the transaction stalled (was in progress, but had no active party or the active party has no email address or related TO DO group associated with it -- if they are currently working on it, then it may not be truly stalled), indicating a possible programming error.
    * **esf\_start\_timestamp** is the date/time the transaction was started.
    * **esf\_status** is the transaction status: In progress, Canceled, Completed, or Suspended.
    * **esf\_status\_text** is the transaction status description, which is typically the current document and party in the process flow.
    * **esf\_transaction\_id** is the unique transaction id.
    * **esf\_transaction\_template\_name** is the PathName of the transaction template.
  * In **Column header** specify the label to show in the column header for this field in the report.
  * In **Output format** specify the format to use for the field.
    * For general fields, you can select to show the entire value, or mask the leading or trailing characters and just show up to 4 of the actual characters.
    * For date fields, you can select the format for the date.
    * For date/time fields, you can select the format for the date/time.
    * For user fields, you can select whether to display the name and/or email address of the user.
    * For decimal/money fields, you can specify the format for the number.
    * For integer fields, you can specify the format for the number.
  * Check the **Allow search** box, when available, to allow for searching transactions based on the values held in this report field.

Click the **Ok** button to keep your changes, or click **Cancel**. This applies to changes to the report field specification, but also if you re-order the fields by dragging them to a new position.

Click the **Close** button to close the list of fields in the report window.

Click the **Delete** button to remove the selected report field.

_Tip: To save your changes, you will want to click the **Ok** button on the list of fields window as well as click the **Save** button for the report template._

<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

## Report field templates ##

Click the **Report field templates** button on the list of fields for a report template, or from the package's **Map report fields** page to modify the report field template name that is otherwise created using the same name as the document field when it is mapped to a new report field.

Report fields are shared across all reports and users so that similar data can be combined from any number of documents and produce a common report.

You cannot rename built-in fields that begin with the 'esf_' prefix._

The type of a report field is initially set based on the type of the document field being mapped. You cannot change the type unless it's a General field type, in which case you can tweak it to be 'Numbers only' (numeric) or 'Letter/numbers only' (alphanumeric). If you have existing data already mapped and you change a General type like this, you'll need to [reload the transaction data from the package](ProgrammingGuide#Reload_transaction_report_fields.md) if you want prior report data to also have the new numbers only or letters/numbers content in your reports.

![http://open.esignforms.com/images/HowToGuidesWiki/reportFieldTEmplate.png](http://open.esignforms.com/images/HowToGuidesWiki/reportFieldTEmplate.png)

  * In **Type** select the type of the field if it is a string type like General, Numbers only, or Letter/Numbers only.
  * In **EsfName** you can change the name of the report field template if it's not a built-in type.
  * In **Label** you can set the default column label for this report field template when it's added to a report.
  * In **Toolip** you can set the default tooltip for this report field template when it's added to a report.

You are also presented with two lists that show:
  * In **Referenced in the following reports** you can see which reports (that you have permission to list) include the selected field.
  * In **Package versions that map fields to this report field** you can see which package versions populate this report field.

Click the **Save** button to keep your changes, or click **Cancel**.

Click the **Close** button to close the list of report field templates window.

Click the **Delete** button to remove the selected report field template if it's not listed as being in use.

<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>

# Live Transactions #

While a transaction exists, parties can use their unique links (and users can access their work via the [To Do queue](UserGuide#To_Do.md)) to access the package of documents.

If a transaction is canceled or suspended, no access is given to any party.

<p align='right'><font size='1'><a href='#Table_of_contents.md'>Table of contents</a></font></p>
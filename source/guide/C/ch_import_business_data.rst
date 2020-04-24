.. _ch_import_bus_data:

Importing Business Data
=======================

.. _busnss-imp-bills-invoices:

Importing Bills and Invoices
----------------------------

.. _busnss-imp-inv-general:

General
~~~~~~~

This functionality creates invoices or bills from a csv import file
containing rows of invoice entry data. The import file may contain rows
for new and/or existing invoices. If an invoice already exists, GnuCash
adds the imported entries to the invoice (unless the invoice is already
posted). If the import file contains posting data for an invoice, then
GnuCash will also attempt to post the invoice. If any row of an invoice
contains an error, GnuCash will ignore all rows of the same invoice.

The field separator in the csv file must be either a comma or a
semicolon; field values may be enclosed in double quotes.

For the sake of readability, in this chapter the term “invoice” by
itself is used to refer to both customer invoices and vendor bills.

.. _busnss-imp-inv-file-format:

The format of the import file
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The import file should contain rows of invoice entry data. Any row
contains both header and entry fields, but GnuCash takes the invoice
header data from the first row of an invoice ID. For informational
purposes, the header data may be repeated for each subsequent row of the
same invoice.

There is no information in the file to indicate whether it concerns
customer invoice or vendor bill data. Instead, a user option in the
import dialog makes that distinction.

Each row should contain the fields listed below, in the same sequence,
separated by a comma or a semicolon. The fields are listed here by their
technical name, which GnuCash uses in the preview of the import data.

-  *``id``* - The invoice ID. If the invoice ID is blank, GnuCash
   replaces it with the invoice ID from the previous row. If the invoice
   ID already exists, GnuCash will add the entries to the existing
   invoice (unless it is already posted).

-  *``date_opened``* - Use the same date format as defined in
   Preferences. Defaulted to today's date if left blank, or if the date
   provided is not valid.

-  *``owner_id``* - Customer or vendor number. Mandatory in the first
   data row of an invoice. If not provided, all rows of the same invoice
   will be ignored.

-  *``billingid``* - Billing ID. Optional

-  *``notes``* - Invoice notes. Optional.

-  *``date``* - The date of the entry. Defaulted to date opened if left
   blank, or if the date provided is not valid.

-  *``desc``* - Description. Optional

-  *``action``* - Action. Optional

-  *``account``* - Account for the entry. Mandatory in each row. If not
   provided or invalid, all rows of the same invoice will be ignored.

-  *``quantity``* - Quantity. Defaulted to 1 if left blank.

-  *``price``* - Price. Mandatory for each row. If not provided, all
   rows of the same invoice will be ignored.

-  *``disc_type``* - Type of discount. Optional. Only relevant for
   invoices, not for bills. Use “%” or blank for percentage value,
   anything else for monetary value.

-  *``disc_how``* - Discount how. Optional. Only relevant for invoices,
   not for bills. Use “>” for discount applied after tax, “=” for
   discount and tax applied before tax, and “<”, blank or anything else
   for discount applied before tax.

-  *``discount``* - Amount or percentage of discount. Optional. Only
   relevant for invoices, not for bills

-  *``taxable``* - Is this entry taxable? Optional. Use “Y” or “X” for
   yes, “N” or blank for no.

-  *``taxincluded``* - Is tax included in the item price? Optional. Use
   “Y” or “X” for yes, “N” or blank for no.

-  *``tax_table``* - Tax table. Optional. If the tax table provided does
   not exist, it will be blank in the invoice.

-  *``date_posted``* - Date posted. Optional. Use the same date format
   as defined in Preferences. If you provide a date posted for the first
   row of an invoice, GnuCash will attempt to also post the invoice (as
   opposed to only saving or updating it).

-  *``due_date``* - Due date. Optional. Use the same date format as
   defined in Preferences. Defaulted to date posted, if left blank. Only
   relevant in the first row of an invoice, if the invoice is posted.

-  *``account_posted``* - Post to account, for vendor or customer
   posting. Only mandatory in the first row of an invoice, if the
   invoice is posted.

-  *``memo_posted``* - Memo. Optional. Only relevant in the first row of
   an invoice, if the invoice is posted.

-  *``accu_splits``* - Accumulate splits? Optional. Use “Y” or “X” for
   yes, “N” or blank for no. Only relevant in the first row of an
   invoice, if the invoice is posted. If you use a spreadsheet program
   to create the import file, it is advised not to use blank for no,
   because a final column with only blanks may not be recognized as
   relevant data when the spreadsheet program creates the csv file.

.. note::
   :name: busnss-imp-inv-file-format-note

   If you use the field separator character within a field, the field
   value should be enclosed in double quotes. Only for the fields
   description (desc) and notes, can you also include a double quote
   within a quoted field value, by doubling the double quote. E.g.
   ``"This field value uses the separator, and a ""quoted"" word"``,
   would be imported as
   ``This field value uses the separator, and a "quoted" word``.

Example content for two bills; one of 2 entries, and one of 3 entries.
The first is saved and posted, the second only saved. Using comma field
separator, decimal point and dd/mm/yyyy date format.

::

   1204;15/12/2018;2001;PO 210220;Special delivery;16/12/2018;Pride and Prejudice;pc;Expenses:Books;1;30.00;;;;X;;A1;17/12/2018;17/1/2019;Liabilities:Accounts Payable;;X
   1204;15/12/2018;2001;PO 210220;Special delivery;16/12/2018;Electronic principles;pc;Expenses:Books;1;50.00;;;;X;;A1;17/12/2018;17/1/2019;Liabilities:Accounts Payable;;X
   1205;15/12/2018;2044;PO 21099;;16/12/2018;Ultimate Guide;pc;Expenses:Books;1;10.01;;;;;;;;;;;
   1205;15/12/2018;2044;PO 21099;;16/12/2018;Dinner & drinks;pc;Expenses:Dining;1;10.01;;;;;;;;;;;
   1205;15/12/2018;2044;PO 21099;;16/12/2018;UG course;pc;Expenses:Education;1;10.01;;;;;;;;;;;
                   

Example content for one customer invoice, with one entry, including tax
and discount. Using comma field separator, decimal point and dd/mm/yyyy
date format. The the value of the description field contains the
separator character.

::

   20221;16/12/2018;1001;Order 3378;Discount as agreed;4/12/2018;"Accounting part 1, 2";ea;Income:Other Income;1;769.95;%;=;10;X;N;A1;16/12/2018;16/01/2019;Assets:Accounts Receivable;Posted by import;X
                   

.. _busnss-imp-inv-import-data:

Import your data
~~~~~~~~~~~~~~~~

To import your invoice data, navigate to File > Import > Import Bills &
Invoices… to open a new import dialog, and provide the necessary
information.

-  1. Choose the file to import - Select your import file, or manually
   type the path and file name.

-  2. Select import type - Select the import type, either Bill or
   Invoice.

-  3. Select import options - Select your csv format. Use the with
   quotes options if your file contains fields enclosed in double
   quotes. These options also match fields not enclosed in quotes;
   except for the fields for description and notes, fields should not
   contain the quote character itself. See
   `note_title <#busnss-imp-inv-file-format-note>`__ above. Use one of
   the other options if your file does not have fields enclosed in
   quotes; any quote characters in the file will be imported as is.

-  4. Preview - Once you have selected your import file and csv format,
   GnuCash shows you a preview of the data. You can verify if your data
   is listed in the correct columns. If you do not see any rows in the
   preview, then GnuCash was not able to match your import data rows to
   the selected csv format. See `What could go
   wrong? <#busnss-imp-inv-errors>`__ below.

-  5. Afterwards - You can choose if GnuCash should open tabs for the
   invoices after the import. Either for all invoices, or for the
   invoices that are saved but not posted, or for none of the invoices.
   Opening tabs slows down the import process considerably.

-  *Start the import* - If you are satisfied with your selections, hit
   the OK button to start the import.

If your data file contains invoice IDs that already exist, then GnuCash
will ask you (once per import session) to confirm that you want to
update existing invoices. If not confirmed, all rows for existing
invoices will be ignored.

.. note::

   Internally, GnuCash uses so called regular expressions to match the
   import rows to the data fields. The import option Custom regular
   expression offers the option to use your own regular expression for
   this matching process. Obviously, this option requires that you are
   well versed in regular expressions. When you choose the option Custom
   regular expression, GnuCash opens a window in which you can edit the
   GnuCash regular expression, or replace it with your own. Your regular
   expression should contain a named subpattern for each of the fields
   of the csv file (using the technical names). A custom regular
   expression could be useful if the rows of your source data file
   contain all required fields, but in a different order or format. E.g.
   if the format of your source data file starts with customer number,
   followed by invoice ID, followed by the due date, and uses \| as
   separator, your regular expression would start with something like
   this:

   ::

          ^(?<owner_id>[^|]*)\|(?<id>[^|]*)\|(?<due_date>[^|]*)
                              

   With a custom regular expression, GnuCash could import your source
   data files, without the need to convert them to the GnuCash import
   format.

.. _busnss-imp-inv-feedback:

Feedback and statistics
~~~~~~~~~~~~~~~~~~~~~~~

GnuCash executes the import process in three steps:

-  *``Import``* - Imports the data file and attempts to match each row
   to the data fields.

-  *``Validation and adjustment``* - Validates the data fields and
   replaces data with defaults if applicable.

-  *``Processing``* - Handles the currency related validations, and
   creates, updates and posts the invoices.

After all steps have finished, GnuCash issues information about the
result of the process. The initial dialog shows the informational or
error messages from the validation and processing steps. The second
dialog shows the statistics of the process:

-  Import - rows ignored: the number of rows that could not be matched
   to the data fields.

-  Import - rows imported: the number of rows that were successfully
   matched to the data fields.

-  Processing and validation - rows fixed: the number of rows for which
   a default value was used for a field.

-  Processing and validation - rows ignored: the number of rows for that
   were not processed because of a validation error.

-  Processing and validation - invoices created: the number of invoices
   created.

-  Processing and validation - invoices updated: the number of invoices
   that were updated.

If there were unmatched rows in the import step, a final dialog shows
the actual rows that could not be matched.

.. _busnss-imp-inv-errors:

What could go wrong?
~~~~~~~~~~~~~~~~~~~~

.. _busnss-imp-inv-err-import:

Errors in the import step
^^^^^^^^^^^^^^^^^^^^^^^^^

If the statistics show unmatched rows under “Import - rows ignored”,
then there is some issue with the format of your import file. Verify
that you use and select the correct separator. Verify that your data
rows have exactly 21 separator characters (1 for each field, except for
the last). Verify whether you use the separator character within a data
field; if so, enclose the field in double quotes.

If you use one of the with quotes import options, verify if you use the
double quote character in any of the data field values; if within the
description or notes fields, make sure that the field value is quoted,
and precede each double quote within the field with an extra double
quote; if within any other field, remove the double quote character.

.. _busnss-imp-inv-err-validation:

Errors in the validation step
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The following errors can occur in the validation step. Any error in a
data row will cause all rows of the same invoice to be ignored.

.. note::

   In versions 3.4 and earlier, an error in a data row would cause just
   that row to be ignored, as opposed all rows of the same invoice.

-  The field ``ID`` is blank. GnuCash replaces a blank invoice ID with
   the invoice ID from the previous row. But the first row of the import
   file should always have an invoice ID.

-  The field ``owner_id`` is blank. Every first row of an invoice should
   have an owner_id.

-  The customer or vendor number in field ``owner_id`` does not exist.
   The owner_id in the first row of an invoice should be an existing
   customer (for invoices) or vendor (for bills).

-  The date in field ``date_posted`` is not a valid date. If you provide
   a value for date_posted in the first row of an invoice, it should be
   a valid date. Did you use the date format as set in Preferences?

-  The account in the field ``account_posted`` does not exist. If you
   provide a value for the field ``date_posted`` in the first row of an
   invoice, the field ``account_posted`` should be an existing account.

-  The account in the field ``account_posted`` is not of type Accounts
   Receivable (for invoices) or Accounts Payable (for bills). If you
   provide a value for the field ``date_posted`` in the first row of an
   invoice, the field ``account_posted`` should be an account of the
   correct type.

-  The field ``price`` is blank. Every row should have a value for the
   field ``price``.

-  The account in the field ``account`` does not exist. Every row should
   have an existing account in the field ``account``.

Any error in the validation step is listed after the overall import
process completes. Correct your data file accordingly.

.. _busnss-imp-inv-err-processing:

Errors in the processing step
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The following errors can occur in the processing step.

-  The invoice cannot be updated because it is already posted. All rows
   of the same invoice will be ignored. If you want to update the
   existing invoice, unpost it first in GnuCash.

-  The currency of the invoice differs from the currency of the account
   posted (“Invoice x NOT posted because currencies don't match”).
   GnuCash determines the currency of the invoice either from the
   customer or vendor master data (for a new invoice) or from the
   invoice itself (for an existing invoice). The currency of the invoice
   must agree with the currency of the post to account in the field
   ``account_posted``. GnuCash creates the invoice but cannot post it.
   Manually correct the invoice in GnuCash.

-  The invoice requires currency conversion. (“Invoice x NOT posted
   because it requires currency conversion”). The invoice contains
   entries on accounts with different currencies, or the currency of the
   entries differs from the currency of the post to account. For such an
   invoice, GnuCash needs exchange rates to translate the currency
   amounts. GnuCash creates the invoice but cannot post it. Post the
   invoice manually in GnuCash, and provide the requested exchange
   rates.

.. _busnss-imp-inv-not-supported:

Not supported invoice functionality
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Currently the invoice import function does not support (at least) the
following:

-  Import of billing terms and job.

-  Import of customer and job in default chargeback project for bills.

-  Application of billing terms from customer or vendor master data.

-  Automatic numbering of invoices.

-  Credit notes.

.. _busnss-imp-customer-vendor:

Importing Customers and Vendors
-------------------------------

.. _busnss-imp-cv-general:

General
~~~~~~~

This functionality creates and updates customers and vendors from a csv
import file containing rows of vendor/customer master data. The import
file may contain rows for new and/or existing customers/vendors. If a
customer/vendor already exists, GnuCash updates the existing
customer/vendor.

.. _busnss-imp-cv-file-format:

The format of the import file
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The import file should contain rows of customer/vendor data, one row for
each customer/vendor. The customer/vendor is identified by the
customer/vendor number in the field ``id`` of the data rows. If the
field is blank, GnuCash will use the next number from the relevant
counter (set in the Counters tab under File > Properties).

There is no data in the file to indicate whether it concerns customer or
vendor master data. Instead, a user option in the import dialog makes
that distinction.

Each row should contain the fields listed below, in the same sequence,
separated by a comma or a semicolon. The fields are listed here by their
technical name, which GnuCash uses in the preview of the import data.

-  *``id``* - The customer/vendor number. If it is for an existing
   customer/vendor, GnuCash will update the customer/vendor. Note that
   in GnuCash e.g. '000010' is a different customer number than '10'. If
   the id field is empty, GnuCash will use the next number from the
   relevant counter.

-  *``company``* - The company name. If it is left blank, it is
   defaulted to the value of field ``name``. If that is also blank, then
   the row is ignored.

-  *``name``* - Billing address - Name. Optional.

-  *``addr1``* - Billing address - Address line 1. At least one of the
   four address lines of the billing address must be filled. If not,
   then the row is ignored.

-  *``addr2``* - Billing address - Address line 2.

-  *``addr3``* - Billing address - Address line 3.

-  *``addr4``* - Billing address - Address line 4.

-  *``phone``* - Billing address - Phone. Optional

-  *``fax``* - Billing address - Fax. Optional

-  *``email``* - Billing address - Email. Optional

-  *``notes``* - Notes. Optional

-  *``shipname``* - Shipping information - Name. Optional. Not relevant
   for vendors.

-  *``shipaddr1``* - Shipping information - Address line 1. Optional.
   Not relevant for vendors.

-  *``shipaddr2``* - Shipping information - Address line 2. Optional.
   Not relevant for vendors.

-  *``shipaddr3``* - Shipping information - Address line 3. Optional.
   Not relevant for vendors.

-  *``shipaddr4``* - Shipping information - Address line 4. Optional.
   Not relevant for vendors.

-  *``shipphone``* - Shipping information - Phone. Optional. Not
   relevant for vendors.

-  *``shipfax``* - Shipping information - Fax. Optional. Not relevant
   for vendors.

-  *``shipmail``* - Shipping information - Email. Optional. Not relevant
   for vendors.

Example content for a customer with a separate shipping address. Using a
semicolon for separator.

``2201;All Star Company;All Star Company;Union Avenue 776;San Juan;CA;;0482938838;;contact@allstar.com;Last contacted on 4/4/2018.;All Star Company; John Alderman, Office 456;Union Avenue 777;San Juan;CA;78998766;;alderman@allstar.com``

Example content for a vendor; no ID given, so GnuCash will take the next
number from the counter. Using a comma for separator.

``,Johnson Supplies,Johnson Supplies,Electric Park 56,Plains,VA,,0482986538,,jack@johnson.com,Discount negotiated,,,,,,,,``

All fields by technical name in the required sequence.

``id,  company,  name,  addr1,  addr2,  addr3,  addr4,  phone,  fax,  email,  notes,  shipname,  shipaddr1,  shipaddr2,  shipaddr3, shipaddr4, shiphone, shipfax, shipmail``

.. _busnss-imp-cv-import-data:

Import your data
~~~~~~~~~~~~~~~~

To import your customer or vendor data, navigate to File > Import >
Import Customes & Vendors… to open a new import dialog, and provide the
necessary information.

-  1. Choose the file to import - Select your import file, or manually
   type the path and file name.

-  2. Select import type - Select the import type, either Customer or
   Vendor.

-  3. Select import options - Select your csv format. Use the with
   quotes options if your file contains fields enclosed in double
   quotes. These options also match fields not enclosed in double
   quotes, but fields should not contain the double quote character
   itself. Use one of the other options if your file does not have
   fields enclosed in quotes; any double quote characters in the file
   will then be imported as is.

-  4. Preview - Once you have selected your import file and csv format,
   GnuCash shows you a preview of the data. You can verify if your data
   is listed in the correct columns. If you do not see any rows in the
   preview, then GnuCash was not able to match your import data rows to
   the selected csv format. See `What could go
   wrong? <#busnss-imp-cv-errors>`__ below.

-  *Start the import* - If you are satisfied with your selections, hit
   the OK button to start the import.

.. note::

   Internally, GnuCash uses so called regular expressions to match the
   import rows to the data fields. The import option Custom regular
   expression offers the option to use your own regular expression for
   this matching process. Obviously, this option requires that you are
   well versed in regular expressions. When you choose the option Custom
   regular expression, GnuCash opens a window in which you can edit the
   GnuCash regular expression, or replace it with your own. Your regular
   expression should contain a named subpattern for each of the fields
   of the csv file (using the technical names). A custom regular
   expression could be useful if the rows of your source data file
   contain all necessary fields, but in a different order or format.
   E.g. if the format of your source data file starts with customer
   number, followed by company name, name, and one address field, and
   that is all you want to import, then your custom regular expression
   would be something like this (using comma as a separator):

   ::

      ^(?<company>[^,]*),(?<id>[^,]*),(?<name>[^,]*),(?<addr1>[^,]*),(?<addr2>[^,]*),(?<addr3>[^,]*)$
                          

   With a custom regular expression, GnuCash could import your source
   data files, without the need to convert them to the GnuCash import
   format.

.. _busnss-imp-cv-feedback:

Feedback and statistics
~~~~~~~~~~~~~~~~~~~~~~~

GnuCash executes the import process in three steps:

-  *``Import``* - Imports the data file and attempts to match each row
   to the data fields.

-  *``Validation and adjustment``* - Validates the data fields and
   replaces data with defaults if applicable.

-  *``Processing``* - Creates or updates the vendor or customer master
   data.

After all steps have finished, GnuCash issues information about the
result of the process. The initial dialog shows the statistics of the
process:

-  Import results - lines ignored: the number of rows that could not be
   matched to the data fields.

-  Import results - lines imported: the number of rows that were
   successfully matched to the data fields.

-  Import results - customers/vendors fixed: the number of rows for
   which a default value was used for a field.

-  Import results - customers/vendors ignored: the number of rows for
   that were not processed because of a validation error.

-  Import results - customers/vendors created: the number of
   customers/vendors created.

-  Import results - customers/vendors updated: the number of
   customers/vendors that were updated.

If there were unmatched rows in the import step, a final dialog shows
the actual rows that could not be matched.

.. _busnss-imp-cv-errors:

What could go wrong?
~~~~~~~~~~~~~~~~~~~~

.. _busnss-imp-cv-err-import:

Errors in the import step
^^^^^^^^^^^^^^^^^^^^^^^^^

If the statistics show unmatched rows under “Import results - lines
ignored”, then there is some issue with the format of your import file.
Verify that you use and select the correct separator. Verify that your
data rows have exactly 18 separator characters (1 for each field, except
for the last). Verify whether you use the separator character within a
data field; if so, enclose the field in double quotes.

If you use one of the with quotes import options, verify if you use the
double quote character in any of the data field values. If so, remove
them; importing double quotes as is, is not supported when using the
with quotes import options.

.. _busnss-imp-cv-err-validation:

Errors in the validation step
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

If the statistics show rows under “Import results - customers/vendors
ignored”, then data rows were ignored because of one of the errors
below:

-  The field ``company`` and the field ``name`` are both blank. The
   field ``company`` is mandatory; if it is blank, then it is defaulted
   to the value of the field ``name``, but if both are blank, then the
   data row cannot be processed.

-  The fields ``addr1``, ``addr2``, ``addr3`` and ``addr4`` are all
   blank. At least one of these fields must have a value, otherwise the
   data row cannot be processed.

.. _busnss-imp-cv-not-supported:

Not supported customer/vendor functionality
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Currently the customer/vendor import function does not support (at
least) the following:

-  Import of any of the fields in the customer tab for billing
   information: currency, terms, discount, credit limit, tax included
   and tax table.

-  Import of any of the fields in the vendor tab for payment
   information: currency, terms, tax included and tax table.

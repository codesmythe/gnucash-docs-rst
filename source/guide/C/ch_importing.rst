.. _chapter_importing:

Importing Data into GnuCash
===========================

This chapter will detail procedures for importing data into GnuCash.

.. _importing-from-files:

Importing Transactions from Files
---------------------------------

Imported transactions will generally be to a specific account in your
account tree. In the following this will be referred to as the
**import** or **base** account. It may or may not be specified in the
data being imported, depending on the import format. It is usually the
first split of a transaction being imported.

All transactions will also must have a **destination** account for at
least matching splits. This may or may not be supplied in the imported
data. If it is not, an account can be assigned on the basis of the
previous import history by matching to infomation in the imported data.
The user may always over-ride this assignment.

Multi-split data previously exported from GnuCash may have both the
import and destination accounts for transaction splits specified in the
data file.

File Import Formats
~~~~~~~~~~~~~~~~~~~

Gnucash allows transactions to be imported in the following formats:

-  `QIF <#importing-qif>`__ (.qif) Quicken Interchange format - import
   data from Quicken financial software;

-  `OFX/QFX <#importing-ofx>`__ (.ofx,.qfx) Open Financial eXchange
   format (QXF is an Intuit/Quicken proprietary version of OFX);

-  `CSV <#importing-csv>`__ (.csv) Comma Separated Values;

-  `MT940 <#importing-mt940>`__ MT940

-  `MT942 <#importing-mt942>`__ MT942

-  `DTAUS <#importing-dtaus>`__ DTAUS

These import methods can be accessed from File > Import ....

.. _importing-matcher:

Import Matcher
~~~~~~~~~~~~~~

Several of the Import Assistants use an Import Matcher to implement a
Bayesian approach to assign destination accounts, if such accounts are
not specified in the imported data, to each imported transaction based
on the previous import history of the import account. It also attempts
to match the transactions being imported to any existing transactions
based on the date and the description fields.

Transaction rows which match existing transactions already in the import
account are flagged not to be imported. They will have a light green
background and the A and U+R checkboxes will be unchecked and the R
checkbox will be checked. To override and import the transaction, check
the A checkbox. The U and R boxes will be unchecked automatically. The
reliability of the match is indicated by a bar display in the Info
column. If a destination account for the second split is assigned by the
matcher if will be appended to the info column.

Transaction rows which do not match existing transactions in the import
account, for which an assignment of a destination account cannot be made
on the basis of the previous import history to the account, will be
displayed with an orange-yellow background and the A box will be checked
and U+R and R unchecked. A destination account must be specified for
these transactions.

Assign a Destination Account to a Single Transaction
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The currently selected row is selected by Left-clicking it. It is
displayed with a mid dark green background.

**Double click** on a row. This will select it and open an Account
Selection dialog. Select the desired destination account in the dialog
and click OK. The row background will change to a light green and the
assigned destination account will be displayed in the Info column.

or alternatively, **Left-click** on a row to select it followed by a
**Right-click**\ to bring up a popup menu then select "Assign a transfer
account" to display the Account Selection dialog, select the destination
account and click the OK button.

Assign a Destination Account to Multiple Transactions
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Sometimes you will have several transactions which will have the same
destination account. Gnucash allows you to select multiple transactions
and apply the same destination account to all transactions in the
selection.

Rows in a selection are displayed with a mid dark green background.

Multiple rows may be selected to have the same destination account
assigned to them.

To select rows either:

-  **Left click** on first row and then **Ctrl-Left click** on other
   rows to add to the selection or

-  **Left-click** on a first row and then **Shift-Left-click** on
   another row to select all rows between them.

then **Right-click** to display a popup menu and then select **"Assign a
transfer account"** to open the Account Selection dialog. Select the
desired destination account and click the OK button in the Account
Selection dialog.

Completing the Import
^^^^^^^^^^^^^^^^^^^^^

Once you have assigned destination accounts for all the imported
transactions using the above methods (all row backgrounds will be a
light green colour), check that the assigned destination acounts are
correct and then press the OK button at the bottom of the Generic Import
Matcher window. The transactions selected for import will have their
splits added to the selected source and destination accounts.

The choices made for the destination accounts and description/memo
fields are remembered and stored and used for future imports to the same
account to automatically assign a destination account for transaction
records not containing destination account information.

.. _importing-qif:

Import QIF
~~~~~~~~~~

To import data from Quicken®, MS Money, or other programs that use
QIF(Quicken® Interchange Format), you must first export your data to a
QIF file. One way to do this is to export each account as a separate QIF
file. An easier way, available in Quicken® 98 and beyond, is to export
all accounts at once into a single QIF file. Check your program's manual
to determine if this option is available.

To import QIF files:
^^^^^^^^^^^^^^^^^^^^

Load all of the QIF files containing data you wish to import
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

To do this, select **File -> Import -> Import QIF...** from the menu.
When the QIF Import dialog box appears, click **Next** and follow the
instructions to guide you through the process of loading your files.

This image shows the start of the QIF Import assistant.

You will be prompted for a filename to load. Use the Select button to
select your QIF file and click Next to load it. Once the file is loaded,
select Load another file if you have more files to load. When you have
loaded all your QIF files, click Next to continue with the import
process.

Review the GnuCash accounts to be created.
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The importer then matches up your QIF accounts and categories with
GnuCash accounts and gives you a brief description of the matching
process. Clicking Next will bring you to a view comparing your QIF
accounts with the corresponding GnuCash accounts created. To change an
account name, select the row containing that account name and edit the
name in the dialog box provided. Click Next when you have finished
making changes, and proceed through a similar category matching process.
QIF income and expense categories import as GnuCash income and expense
accounts Make changes to these account names if necessary, and click
Next to continue.

**Note:** If you are not sure what changes are needed, it is safe to
accept the GnuCash account names. It is easy to edit the accounts later
if you find you need to make a change.

From the drop-down list, select a standard currency to be used for the
imported accounts and click **Next** to continue. If you have stocks,
mutual funds, or other securities, you will be prompted for additional
information. The importer dialog will ask for the exchange or listing
(i.e. Nasdaq), the security's full name, and the ticker symbol. If you
do not have this information handy, you can edit the account information
later, once the import is complete. Click **Next** to continue.

Tell GnuCash to import the data.
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The last step is the import. Once you have verified your account names
and investment information, click **Finish** in the Update your GnuCash
accounts page to complete the import process. Depending upon the size of
your file, the import might take a few minutes to complete, so a
progress bar displays the percentage finished. When the import process
is complete, GnuCash will return you to the main window, which should
now display the names of the accounts you imported.

.. _importing-ofx:

Import OFX/QFX
~~~~~~~~~~~~~~

This opens a file selection dialog. Navigate to the file you wish to
import, select a file with the appropriate extension (.ofx or .qfx),
then press the **Import** button.

Gnucash opens an Account Selection dialog to select an account in your
CoA corresponding to data source. Select the appropriate account from
the account tree and press the **OK** button. On subsequent import of
files from the same source (identified by tags in the file), the source
is remembered and the account selection dialog is not displayed.

The generic import transaction matcher dialog is opened next. See the
`Import Matcher <#importing-matcher>`__ section (common to both OFX/QFX
and CSV import formats) following the Import CSV section to continue the
import process.

.. _importing-csv:

Import CSV
~~~~~~~~~~

Clicking on **Import CSV** in the Import menu will bring up the Import
Assistant dialog. The first step brings up a file selection dialog.
Navigate to the location where the file you wish to import is located
and select the file to import then click the **OK** button.

The next window will allow you to set parameters for the importing of
the file. All widgets have tooltips which explain what the setting
affects and the options for the setting.

.. _importing-csv-save:

Load and Save Settings
^^^^^^^^^^^^^^^^^^^^^^

If this import is a regular occurrence, once you have set the other
import paramters, you can save these settings by typing in a setting
name in the **Load and Save Settings Entry** combo box and pressing the
**Save** button just to the right of the box. Previously defined
settings can be retrieved by selecting the appropriate setting name from
the dropdown list activated by the down arrow at the right end of the
text box. The trash can button to the right of the Save button can be
used to remove the settings selected from the drop down list for the
box. The settings group **"GnuCash Export Settings"** define a setting
group for the export and reimport of GnuCash transaction data - use this
if importing data previously exported from GnuCash.

Account
^^^^^^^

This combo box allows you to select the base or import account into
which the transactions will be imported. It may be left unset if the
imported data contains a column listing the accounts associated with
each split or the import data specifies the account for first split of
the transaction.

File Format
^^^^^^^^^^^

This section allows you to define whether the file has:

-  **Fixed width columns** Selecting this radio button will allow you to
   define column boundaries by double clicking at the appropriate
   positions in the sample records displayed in the panel below. Single
   clicking in a column will narrow, widen or merge the column.

-  **Separators** Selecting this radio button will allow you to define
   characters which will be used to distinguish columns in the input
   file. The default is comma separated however spaces, tabs,colons or
   semicolons or any combination of them may be used to separate columns
   in the input file by selecting the appropriate check boxes. You may
   also define custom separators by typing the required characters into
   the text box and selecting the **Custom** checkbox. This may be used
   in combination with any of the predefined separators.

-  **Multi-split** Selecting this check box allows the splits for a
   single transaction to be defined on consecutive lines within the file
   with each line defining a single split. If not selected each line is
   assumed to contain the information for a single transaction including
   one or two splits.

Miscellaneous
^^^^^^^^^^^^^

The miscellaneous settings allow you to set:

-  **Encoding**\ This is usually the UTF-8 variant for your locale;

-  **Date Format** This does not default to the Locale setting so check
   it matches the data you are importing;

-  **Currency Format**;

-  **Leading Lines to Skip**;

-  **Trailing Lines to Skip**;

-  **Skip alternate lines**;

to match the settings for the file you are importing. Tooltips may also
contain information on the setting and options.

Import Panel
^^^^^^^^^^^^

The import panel shows the data being imported as it is interpreted
using the settings chosen to define columns and formats. The dropdown
lists in the headers for each column of the import allow you to
associate a specific column in the imported data with a specific field
in the display of a transaction in an account register. At a minimum to
import data, columns in the imported data containing the following
information **must** be specified:

-  **Date**\ of transaction;

-  **Account** into which transaction is to be imported (or
   alternatively set the base account as above);

-  **Description** of the transaction;

-  **Deposit or Withdrawal** column.

The **Skip Errors** check box will skip trying to import any rows with
errors in matching the columns.

When you are happy with all the import settings,
`save <#importing-csv-save>`__ them if you will use the same settings
again, then press the **Next** button. This will bring up a window which
allows you to map the accounts identified in the account column (Account
Id) with accounts in the GnuCash account tree (Account name). Double
click on a row to bring up a dialog to select the matching GnuCash
account. When you have selected a match for all accounts, click on the
**Next** button.

The Transaction Information panel allows review of data entry settings
so far.

Clicking on Match Transactions will then bring up the main `Import
Matcher <#importing-matcher>`__ window described in the next section.

.. _importing-mt940:

Import MT940
~~~~~~~~~~~~

Use this option to import MT940 data.

.. _importing-mt942:

Import MT942
~~~~~~~~~~~~

Use this option to import MT942 data.

.. _importing-dtaus:

Import DTAUS
~~~~~~~~~~~~

Use this option to import DTAUS data.

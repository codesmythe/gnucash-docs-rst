.. _ch_reports:

Reports
=======

GnuCash is a powerful double entry accounting software package that
allows users to enter and track their money in a reliable manner.
However, putting this information into GnuCash is only a part of the
process. To be truly helpful, you need to be able to extract this
information in meaningful ways. GnuCash's reporting features allow you
to just that.

GnuCash's reporting features allow you to display nearly any group of
transactions in a wide variety of formats. This makes it easy to answer
questions about your finances, such as "How much did I spend on
groceries last month?" or "How much did I earn in the previous six
months?"

GnuCash includes a number of common report types, which can be modified
to meet your specific needs. If these common reports are insufficient,
it is possible to modify or even write your own custom reports (although
this is not recommended for beginners).

.. _rpt_concepts:

Overview
--------

There are many standard reports pre-built in GnuCash, all available from
the Reports pulldown menu in the main account window.

When you select a report from the list of reports, that report is first
run with its default settings. Once you have opened the report, you can
modify its parameters by clicking on the Options button on the toolbar.
Under Options, you will see the different settings that you can change
for each report. Note that for different reports, the options will be
different.

.. _rpt_savedconfigsinfo:

Saved Reports Configurations Concepts
-------------------------------------

Once you have modified a report to meet your needs, you may wish to save
that report for reuse at a later point. GnuCash allows custom reports to
be saved, using the Save Report Configuration command.

To save a report configuration:

-  Go to the Reports Menu and choose the desired report.

-  Change the settings on the report until it includes what is needed.

-  Go to the General tab of the report's options and change the Report
   Name to something meaningful (Do not confuse this with the Report
   Title).

-  Apply the changes and close the dialog.

-  Click the Save Report Configuration or Save Report Configuration
   As... button

This will store the report options in a file in your home directory.

The first time you save a report with a name that has not already been
saved, you can use either the Save Report Configuration or the Save
Report Configuration As... button. You can modify the report name before
saving it.

Once a report has been saved with the current name, the Save Report
Configuration button will immediately update the saved report
configuration. Use the Save Report Configuration As button to save the
current report configuration with a new name.

Saved report configurations are available for use under the
Reports->Saved Report Configurations entry. They will also be available
for use on multicolumn reports.

Saved report configurations can be deleted in the Saved Report
Configurations dialog by clicking the trashcan icon.

To edit saved report configurations, open the report via Reports->Saved
Report Configurations, edit and apply the new options, and click Save
Report Configuration.

.. _rpt_standardrpts:

Standard Reports Overview
-------------------------

The standard reports that are included in GnuCash are presented in this
chapter. For each report, a short description is given, which explains
what the report is intended to show and its primary purpose. We begin
with a description of the Transaction Report, which is an all-purpose
report with many features and settings that allow sophisticated
examination of the data in a file.

.. _rpt_txnrept:

Transaction Report
~~~~~~~~~~~~~~~~~~

The Transaction Report is a fundamental report that allows users to
retrieve a wide variety of useful information from the financial
records. The report includes many features that allow powerful and
flexible reporting from the single basic report.

-  Debit and Credit subtotals can be displayed, and within a grouping
   section, if debit totals > credit totals, the group subtotal will be
   displayed in the debit column.

-  Multiple data columns enable display of transaction amounts in report
   currency and original currency in separate columns.

-  Additional sortkeys e.g. sort by reconcile status (unreconciled ->
   cleared -> reconciled), sort by weeks, allow additional views into
   the financial records.

-  Full text filter enabled for description, notes and memo, and for
   account full names. This allows easier selection of source account
   names and tailored reporting. Filters can optionally use full POSIX
   regular expressions.

-  Indenting of columns will indent the report columns for easier
   understanding of grouping and sorting. (This is now enabled by
   default for Gnucash 3.0 onwards)

-  Subtotal table is useful to understand the relationship in the data.
   This feature compiles the primary and secondary subtotals into a
   table view, allowing additional insight into financial records, e.g.
   account subtotals in different time series.

For further ideas on how to use the Transaction Report to produce common
reports, see `Using the Transaction Report <#rpt_transaction>`__.

.. _rpt_grp_assetsliabs:

Assets & Liabilities Group
~~~~~~~~~~~~~~~~~~~~~~~~~~

Reports in this group provide general information about assets and
liabilities.

.. _rpt_advport:

Advanced Portfolio
^^^^^^^^^^^^^^^^^^

The Advanced Portfolio produces a report on commodity accounts (stock
and mutual fund type accounts) using price information stored in the
GnuCash price database and within the GnuCash transaction data. If you
do not have stock price information in your file, the report will
indicate an error. This report includes extended information about
commodity holdings, including information about the basis, gain, and
return of individual commodities.

.. _rpt-advport-capgains:

Advanced Portfolio Capital Gains
''''''''''''''''''''''''''''''''

The Advanced Portfolio report doesn’t use the capital gain splits to
calculate capital gains. It calculates the gains from the various buy
and sell transactions in the account without regard to whether the gains
and losses are recorded or not. Any realized gain splits are ignored.
Realized gain splits are recognized as two splits, one in the stock’s
account with a zero number of shares and a non-zero value, the other in
an income or expense account with a value that is the negative of the
split in the stock account. These two splits can be in a separate
transaction (as created by scrubbing) or in the same transaction as the
sale (this will cause incorrect future scrubbing). The income or expense
split can be split into multiple splits, say for taxable/non-taxable or
short/long term gains, without affecting this report.

.. _rpt_assetbarchart:

Asset Barchart
^^^^^^^^^^^^^^

The Asset Barchart presents the value of assets on a monthly basis in
barchart form. By default, the report displays the eight largest
accounts that have specific asset types assigned to them, and it
displays bars for the current financial period.

Several settings on this report can greatly affect the information
included.

-  On the Accounts tab, the "Show Accounts until level" option changes
   how the report aggregates account totals. Change this value to see
   information at deeper levels of the account structure.

-  On the Display tab, the "Maximum Bars" option will display more bars
   in the chart, allowing information for more accounts to display.
   Additionally, the "Show table" option enables the display of chart
   information in tabular form below the chart.

-  On the General tab, the "Price Source" option can significantly
   affect the reported value of various commodities included in the
   report.

.. _rpt_assetpiechart:

Asset Piechart
^^^^^^^^^^^^^^

The Asset Piechart presents the value of assets on a monthly basis in
piechart form. By default, the report shows the seven largest accounts,
that have specific asset types assigned to them, arranged in descending
order by value as of the end of the current accounting period.

Several settings on this report can greatly affect the information
included.

-  On the Accounts tab, the "Show Accounts until level" option changes
   how the report aggregates account totals. Change this value to see
   information at deeper levels of the account structure.

-  On the Display tab, the "Maximum Slices" option will display more
   slices in the chart, allowing information for more accounts to
   display.

-  On the General tab, the "Price Source" option can significantly
   affect the reported value of various commodities included in the
   report.

.. _rpt_avgbalance:

Average Balance
^^^^^^^^^^^^^^^

The Average Balance report displays monthly averages for the current
accounting period.

.. _rpt_balancesheet:

Balance Sheet
^^^^^^^^^^^^^

The Balance Sheet lists Asset, Liability, and Equity account balances
for all such accounts, and provides totals as of a given date. Balance
sheets are commonly run for the last day of each fiscal year to give an
overall sense of the financial condition of the entity.

.. _rpt_generaljournal:

General Journal
^^^^^^^^^^^^^^^

The General Journal produces a register of all transactions (beginning
to end) in order by date, showing the accounts and the amounts involved,
and totals the Net Change by all currencies and assets.

This report is not customizable by date or account, though you can
include more or fewer details about the individual transactions, and
whether to include running balances and totals for the credits and
debits. If you need a report restricted to particular accounts, consider
the Transaction Report or open a particular account and choose the
Account Transaction Report.

.. _rpt_generalledger:

General Ledger
^^^^^^^^^^^^^^

The General Ledger produces information about all transactions for a
selected set of accounts. When first run, this report loads no data, and
the report options must be changed to retrieve information from the
file.

.. _rpt_investport:

Investment Portfolio
^^^^^^^^^^^^^^^^^^^^

The Investment Portfolio produces a report of commodity accounts (that
is, accounts with type "Stock" or "Mutual Fund"), giving holdings, price
and value information about commodities in the file.

.. _rpt_liabbarchart:

Liability Barchart
^^^^^^^^^^^^^^^^^^

The Liability Barchart presents the value of liabilities on a monthly
basis in barchart form. By default, the report displays the eight
largest accounts that have specific asset types assigned to them, and it
displays bars for the current financial period.

Several settings on this report can greatly affect the information
included.

-  On the Accounts tab, the "Show Accounts until level" option changes
   how the report aggregates account totals. Change this value to see
   information at deeper levels of the account structure.

-  On the Display tab, the "Maximum Bars" option will display more bars
   in the chart, allowing information for more accounts to display.
   Additionally, the "Show table" option enables the display of chart
   information in tabular form below the chart.

-  On the General tab, the "Price Source" option can significantly
   affect the reported value of various commodities included in the
   report.

.. _rpt_liabpiechart:

Liability Piechart
^^^^^^^^^^^^^^^^^^

The Liability Piechart presents the value of liabilities on a monthly
basis in piechart form. By default, the report shows the seven largest
accounts, that have specific asset types assigned to them, arranged in
descending order by value as of the end of the current accounting
period.

Several settings on this report can greatly affect the information
included.

-  On the Accounts tab, the "Show Accounts until level" option changes
   how the report aggregates account totals. Change this value to see
   information at deeper levels of the account structure.

-  On the Display tab, the "Maximum Slices" option will display more
   slices in the chart, allowing information for more accounts to
   display.

-  On the General tab, the "Price Source" option can significantly
   affect the reported value of various commodities included in the
   report.

.. _rpt_networthbar:

Net Worth Barchart
^^^^^^^^^^^^^^^^^^

The Net Worth Barchart summarizes Asset accounts, Liability accounts,
and overall Net Worth as bars on a graph on a monthly basis for the
current financial period. This report provides a graphic overview of the
file over time.

.. _rpt_networthline:

Net Worth Linechart
^^^^^^^^^^^^^^^^^^^

The Net Worth Linechart summarizes Asset accounts, Liability accounts,
and overall Net Worth as a line graph on a monthly basis for the current
financial period. This report provides a graphic overview of the file
over time.

.. _rpt_pricescatter:

Price Scatterplot
^^^^^^^^^^^^^^^^^

The Price Scatterplot displays the value of one commodity relative to
another commodity, for example the value of a stock relative to a
currency. When first run, this report loads no data, and the report
options must be changed to retrieve information from the file.
Specifically, the "Price of Commodity" setting on the Price options tab
must be changed to a specific commodity.

.. _rpt_grp_budget:

Budget Group
~~~~~~~~~~~~

Budget reports in GnuCash allow you to gather summary information
related to budgets you may have created. In order for these reports to
work, you must first create a budget. The reports in this group are
specifically based on budget information. To use these reports, you need
to have a budget saved in your file.

.. _rpt_budbalsht:

Budget Balance Sheet
^^^^^^^^^^^^^^^^^^^^

.. _rpt_budbarchart:

Budget Barchart
^^^^^^^^^^^^^^^

.. _rpt_budflow:

Budget Flow
^^^^^^^^^^^

.. _rpt_budincstate:

Budget Income Statement
^^^^^^^^^^^^^^^^^^^^^^^

.. _rpt_budprofloss:

Budget Profit & Loss
^^^^^^^^^^^^^^^^^^^^

.. _rpt_budreport:

Budget Report
^^^^^^^^^^^^^

.. _rpt_grp_business:

Business Group
~~~~~~~~~~~~~~

Reports in this group provide general information about activities
related to a business.

.. _rpt_customer:

Customer Report
^^^^^^^^^^^^^^^

.. _rpt_custsummary:

Customer Summary
^^^^^^^^^^^^^^^^

Customer Summary is a customer profit report that can help with job
analysis by comparing the income and expenses for a specific customer.

All invoices have an Owner in GnuCash, so invoices that are made will
show a customer and show in the report. When creating a Bill, the
Default Chargeback Customer is blank. To use the profit report, this
field needs an entry, since this is the tag that decides the line to
which to attach the expense. Left blank, the bill will be assigned to
"No Customer." Similarly, when income is entered directly in a register
rather than creating an invoice, it will also be assigned to "No
Customer."

Thus, if this report includes an entry for "No Customer", this means
that the report may be inaccurate, as the results are not all properly
labeled.

Possible use scenarios include:

-  Tracking retail sales from different cities

-  Tracking rental properties

-  Tracking types of business

-  Tracking commission sales

Each of these scenarios assumes that the account structure includes
breakdowns for individual tracked categories. Changing settings on the
Income and Expense tabs under Options can hone the information
displayed. By default all income and expense accounts are included;
however, since GnuCash can't really predict the names and classification
of income and expense accounts, it must group them all into the "No
Customer" entry.

Note that inventory-based businesses won't benefit from this report
because of its nature.

Useful options:

-  The Expense Accounts tab allows the selection of one or more expense
   accounts.

-  The Income Accounts tab allows the selection of one or more income
   accounts.

-  The Display tab allows sorting by name, profit percentage, or amount
   of profit.

.. _rpt_easyinv:

Easy Invoice
^^^^^^^^^^^^

.. _rpt_employee:

Employee Report
^^^^^^^^^^^^^^^

.. _rpt_fancyinv:

Fancy Invoice
^^^^^^^^^^^^^

.. _rpt_payaging:

Payable Aging
^^^^^^^^^^^^^

.. _rpt_prtinv:

Printable Invoice
^^^^^^^^^^^^^^^^^

.. _rpt_recaging:

Receivable Aging
^^^^^^^^^^^^^^^^

This report provides a listing of all customers, their current balance,
and how much they have outstanding from invoices over different time
periods&mdash;how much they owe from 0-30 days, from 31-60 days, from
61-90 days, and over 90 days. The report also contains links to each
customer and to their current customer report.

.. _rpt_vendor:

Vendor Report
^^^^^^^^^^^^^

.. _rpt_grp_incexp:

Income and Expense Group
~~~~~~~~~~~~~~~~~~~~~~~~

Reports in this group provide information about Income and Expense

.. _rpt_cashflow:

Cash Flow
^^^^^^^^^

This report shows the change in value for a set of accounts (the flow of
cash) over a given period of time. By default, this report is based on
accounts in Assets and Special Accounts, and covers the current
financial period. The report enumerates all money coming in to and going
out of the base accounts, broken down by the other account.

.. _rpt_equity:

Equity Statement
^^^^^^^^^^^^^^^^

This report can be seen as extension of the Balance Sheet report. The
Balance Sheet states the balance of Assets, Liabilities and Equity at a
specific point of time. The Equity Statement focuses on the Equity
Accounts by showing the cash flow to and from them for a given period of
time.

By balancing this cash flow with income, the report shows the available
capital at the beginning and end of the selected time period.

.. _rpt_expbarchart:

Expense Barchart
^^^^^^^^^^^^^^^^

The Expense Barchart presents the value of expenses on a monthly basis
in barchart form. By default, the report displays the eight largest
accounts that have specific expense types assigned to them, and it
displays bars for the current financial period.

Several settings on this report can greatly affect the information
included.

-  On the Accounts tab, the "Show Accounts until level" option changes
   how the report aggregates account totals. Change this value to see
   information at deeper levels of the account structure.

-  On the Display tab, the "Maximum Bars" option will display more bars
   in the chart, allowing information for more accounts to display.
   Additionally, the "Show table" option enables the display of chart
   information in tabular form below the chart.

-  On the General tab, the "Price Source" option can significantly
   affect the reported value of various commodities included in the
   report.

.. _rpt_exppiechart:

Expense Piechart
^^^^^^^^^^^^^^^^

The Expense Piechart presents the value of expenses on a monthly basis
in piechart form. By default, the report shows the seven largest
accounts, that have specific expense types assigned to them, arranged in
descending order by value as of the end of the current accounting
period.

Several settings on this report can greatly affect the information
included.

-  On the Accounts tab, the "Show Accounts until level" option changes
   how the report aggregates account totals. Change this value to see
   information at deeper levels of the account structure.

-  On the Display tab, the "Maximum Slices" option will display more
   slices in the chart, allowing information for more accounts to
   display.

-  On the General tab, the "Price Source" option can significantly
   affect the reported value of various commodities included in the
   report.

.. _rpt_expdayoweek:

Expenses vs. Day of Week
^^^^^^^^^^^^^^^^^^^^^^^^

Expenses vs. Day of Week presents a pie chart showing the totals for
selected expense accounts totaled by the day of the week of the
transaction. The report options enable you to make some adjustments
(such as accounts, display options, and the date range) but the account
selector only allows expense accounts to be chosen. The report
aggregates expense transactions by day of week, not by any other period
or category. Due to these limitations, the report may be considered a
demonstration or an example to someone wanting to examine the source
code for composing a useful custom report.

.. _rpt_incomebarchart:

Income Barchart
^^^^^^^^^^^^^^^

The Income Barchart presents the value of income on a monthly basis in
barchart form. By default, the report displays the eight largest
accounts that have specific income types assigned to them, and it
displays bars for the current financial period.

Several settings on this report can greatly affect the information
included.

-  On the Accounts tab, the "Show Accounts until level" option changes
   how the report aggregates account totals. Change this value to see
   information at deeper levels of the account structure.

-  On the Display tab, the "Maximum Bars" option will display more bars
   in the chart, allowing information for more accounts to display.
   Additionally, the "Show table" option enables the display of chart
   information in tabular form below the chart.

-  On the General tab, the "Price Source" option can significantly
   affect the reported value of various commodities included in the
   report.

.. _rpt_incexpchart:

Income & Expense Chart
^^^^^^^^^^^^^^^^^^^^^^

.. _rpt_incomepiechart:

Income Piechart
^^^^^^^^^^^^^^^

The Income Piechart presents the value of income on a monthly basis in
piechart form. By default, the report shows the seven largest accounts,
that have specific income types assigned to them, arranged in descending
order by value as of the end of the current accounting period.

Several settings on this report can greatly affect the information
included.

-  On the Accounts tab, the "Show Accounts until level" option changes
   how the report aggregates account totals. Change this value to see
   information at deeper levels of the account structure.

-  On the Display tab, the "Maximum Slices" option will display more
   slices in the chart, allowing information for more accounts to
   display.

-  On the General tab, the "Price Source" option can significantly
   affect the reported value of various commodities included in the
   report.

.. _rpt_incstatement:

Income Statement
^^^^^^^^^^^^^^^^

This report lists Income and Expense account totals for a set period. By
default, it shows all Expense and Income accounts down to 3 levels of
sub-accounts for the current financial period.

An Income Statement is also called a "Profit and Loss" report or
"Revenue Statement."

In earlier versions of GnuCash, this report was called "Profit & Loss,"
but with version 2, the report was renamed "Income Statement" to use
more common accounting terminology.

The Income Statement helps show where money is coming from and where it
is going for a given time period.

.. _rpt_incdayoweek:

Income vs. Day of Week
^^^^^^^^^^^^^^^^^^^^^^

Income vs. Day of Week presents a piechart showing the totals for
selected income accounts totaled by the day of the week of the
transaction. The report options enable you to make some adjustments
(such as accounts, display options, and the date range) but the account
selector only allows income accounts to be chosen. The report aggregates
income transactions by day of week, not by any other period or category.
Due to these limitations, the report may be considered a demonstration
or an example to someone wanting to examine the source code for
composing a useful custom report.

.. _rpt_trialbal:

Trial Balance
^^^^^^^^^^^^^

Trial Balance lists the ending balances in all accounts as of a
particular date. It is typically run at the end of an accounting period
and is primarily used to ensure that the total of all debits equals the
total of all credits.

.. _rpt_gst_statement:

Income and GST Statement
^^^^^^^^^^^^^^^^^^^^^^^^

The Income and GST Statement is a specialised Transaction Report
designed to print Business-related Sales and Receipts, as well as their
GST or VAT components. This report is designed for use in Australia, but
is also usable in any jurisdictions implementing value-added taxes (or
goods and services taxes) during regular business sales and receipts;
and the business owner is expected to submit periodic reports of total
sales, purchases, and taxes collected on sales from clients or paid to a
supplier.

This report makes some assumptions upon the accounts used for sales,
purchases, and taxes collected on sales, and paid on purchases.

-  Net Sales must be an Income-type account

-  Net Purchases must be an Expense-type account

-  GST/VAT on Sales must be a Liability-type account

-  GST/VAT on Purchases must be an Asset-type account

-  There may be multiple GST accounts, e.g. reduced GST, standard GST
   etc. The GST accounts can be printed individually, or summarised for
   sales and purchases.

-  There may be multiple sales and expenses accounts, e.g. Income:Sales,
   Income:Grants, Expenses:Suppliers, Expenses:Marketing,
   Expenses:Insurance. These amounts may be reported individually, or
   summarised for sales and purchases.

-  The transactions may be entered manually as a multi-split
   transaction, or they may be entered via the Business Invoices and
   Bills tools.

As an example, consider a business has the following transactions: It
incurs sales of $1,000 plus 5% GST, receiving $1,050. It also incurs
GST-exempt sales of $600. It purchases goods/services worth $400 plus 5%
= $420. The following transactions will record the business activities:

.. table:: Sample Chart of Accounts for Income and GST Statement

   +----------------+----------------+----------------+-------+--------+
   | Date           | Description    | Account        | Debit | Credit |
   +================+================+================+=======+========+
   | 01/01/2018     | Sales $1,000 + | Income:Sales   |       | $1,000 |
   |                | 5% GST         |                |       |        |
   +----------------+----------------+----------------+-------+--------+
   | GST on Sales   |                | $50            |       |        |
   | [Liability]    |                |                |       |        |
   +----------------+----------------+----------------+-------+--------+
   | Asset:Bank     | $1,050         |                |       |        |
   +----------------+----------------+----------------+-------+--------+
   | 02/01/2018     | GST-Free Sales | Income:Sales   |       | $600   |
   |                | $600           |                |       |        |
   +----------------+----------------+----------------+-------+--------+
   | Asset:Bank     | $600           |                |       |        |
   +----------------+----------------+----------------+-------+--------+
   | 03/01/2018     | Purchase $400  | Expe           | $400  |        |
   |                | + 5% GST       | nses:Purchases |       |        |
   +----------------+----------------+----------------+-------+--------+
   | Asset:Bank     |                | $420           |       |        |
   +----------------+----------------+----------------+-------+--------+
   | GST on         | $20            |                |       |        |
   | Purchases      |                |                |       |        |
   | [Asset]        |                |                |       |        |
   +----------------+----------------+----------------+-------+--------+

For the Income and GST Statement, the ``Accounts`` selected will be the
Income and Expense Accounts, and the ``Tax accounts`` are used to select
the GST accounts. The GST period is selected via the General tab. The
resulting report is shown as follows:

.. table:: Income and GST Statement

   +-------+-------+-------+-------+-------+-------+-------+-------+
   | Date  | D     | Total | Net   | Tax   | Total | Net   | Tax   |
   |       | escri | Sales | Sales | on    | Purc  | Purc  | on    |
   |       | ption |       |       | Sales | hases | hases | Purc  |
   |       |       |       |       |       |       |       | hases |
   +=======+=======+=======+=======+=======+=======+=======+=======+
   | 01/01 | Sales | $     | $     | $50   |       |       |       |
   | /2018 | $     | 1,050 | 1,000 |       |       |       |       |
   |       | 1,000 |       |       |       |       |       |       |
   |       | + 5%  |       |       |       |       |       |       |
   +-------+-------+-------+-------+-------+-------+-------+-------+
   | 02/01 | GST   | $600  | $600  |       |       |       |       |
   | /2018 | -Free |       |       |       |       |       |       |
   |       | Sales |       |       |       |       |       |       |
   |       | $600  |       |       |       |       |       |       |
   +-------+-------+-------+-------+-------+-------+-------+-------+
   | 03/01 | Pur   |       |       |       | $420  | $400  | $20   |
   | /2018 | chase |       |       |       |       |       |       |
   |       | $400  |       |       |       |       |       |       |
   |       | + 5%  |       |       |       |       |       |       |
   |       | GST   |       |       |       |       |       |       |
   +-------+-------+-------+-------+-------+-------+-------+-------+
   | T     |       | $     | $     | $50   | $420  | $400  | $20   |
   | otals |       | 1,650 | 1,600 |       |       |       |       |
   +-------+-------+-------+-------+-------+-------+-------+-------+

This report would indicate that there was a total of $50 GST collected,
and $20 GST on purchases, therefore a $30 GST liability is payable to
the authorities.

.. _rpt_grp_sampcust:

Sample & Custom Group
~~~~~~~~~~~~~~~~~~~~~

The reports in this group offer examples on how reports can be
customized or podified to suit personal need.

.. _rpt_custommulti:

Custom Multicolumn Report
^^^^^^^^^^^^^^^^^^^^^^^^^

This report provides a base that allows several standard and custom
reports to be combined into one view. Note that this report opens with
an empty window; you must open the options and designate which reports
to include for display. Once the reports have been selected, the
settings for individual reports in the multicolumn display can be
edited.

.. _rpt_sample:

Sample Report with Examples
^^^^^^^^^^^^^^^^^^^^^^^^^^^

This is a sample report that users can examine to learn how to write
their own reports.

.. _rpt_welcome:

Welcome Sample Report
^^^^^^^^^^^^^^^^^^^^^

This report demonstrates how the Multicolumn Report can be use to create
custom dashboard-type reports.

.. _rpt_grp_miscrpts:

Other Reports
~~~~~~~~~~~~~

Several reports are included on the main Reports menu. These are
described below.

.. _rpt_acctsummary:

Account Summary
^^^^^^^^^^^^^^^

This lists the balances of all accounts and subaccounts as of a
particular date. By default, this report shows accounts and totals down
to third-level subaccounts.

This report gives effectively the same information as the Chart of
Accounts. You can use this report to export and print the Chart of
Accounts.

.. note::

   To generate a report of account totals over a particular time period
   (especially if you do not close your books at regular intervals), you
   might consider using the Income Statement, or Cash Flow reports.

.. _rpt_balance_forecast:

Balance Forecast
^^^^^^^^^^^^^^^^

This creates a balance chart which aims to track asset (or any other
account type) balances, including amounts from future scheduled
transactions. The balances will include all regular booked amounts and
future amounts from numeric scheduled transaction templates.

This report can also add additional data charts to forecast future
minimum balances. Reserve line can be displayed to confirm if future
minimum will dip below the reserve amount. A target line may also be
displayed above the reserve line for financial planning.

.. _rpt_futsched:

Future Scheduled Transactions Summary
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. _rpt_taxtxf:

Tax Report & TXF Export
^^^^^^^^^^^^^^^^^^^^^^^

Generates a report and a downloadable .txf file of taxable income and
deductible expenses for a particular accounting period. To download the
report data, choose the Export button on the toolbar and choose between
html and .txf downloadable versions.

To use this report, you must use Edit --> Tax Options to identify which
form the taxing authority uses for each income or expense account. Note
that you can see but not modify the "Tax related" checkbox in Edit -->
Edit Account.

.. _rpt_savedrpts:

Saved Report Configurations
^^^^^^^^^^^^^^^^^^^^^^^^^^^

Selecting this will open a dialog with a list of available Saved Report
Configurations. "Saved Report Configurations" means sets of customized
settings for standard reports.

These sets must be saved by the user before they appear here. See Report
Concepts above for instructions on how to save report configurations.

.. _rpt_acctreport:

Account Report
^^^^^^^^^^^^^^

The Account Report menu entry only appears when an account register is
the active tab. This report produces a list of all transactions in the
open register.

Note that if you conduct a search that retrieves several transactions,
the results are displayed in a new search register, which can then be
used to create a report for just those transactions.

.. _rpt_accttxnrept:

Account Transaction Report
^^^^^^^^^^^^^^^^^^^^^^^^^^

This report also only appears when an account register is the active
tab. However, this report only lists transactions that have been
selected (e.g. by mouse click) in the current register. If no
transactions are selected, an empty report will be generated.

.. _rpt_transaction:

Using the Transaction Report
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The Transaction Report can be heavily customised to produce most reports
appropriate for personal finance and business bookkeeping purposes. It
aims to retrieve and filter information from the database, and present
transactions and totals, useful for the user and the accountant.

The following guide to the Transaction Report will assume the user has
set up the chart of accounts according to conventional bookkeeping
practice. For example, the following describes a typical household book
with skeleton accounts. Further accounts will undoubtedly be necessary.

.. table:: Sample Chart of Accounts for the Transaction Report

   ======================= =======================
   Account Name            Account Type
   ======================= =======================
   Asset                   ASSET (placeholder)
   Asset:Bank              BANK
   Asset:Property          ASSET
   Liability               LIABILITY (placeholder)
   Liability:Credit Card   CREDIT CARD
   Liability:Home Loan     LIABILITY
   Income                  INCOME (placeholder)
   Income:Salary           INCOME
   Income:Interest         INCOME
   Expense                 EXPENSE (placeholder)
   Expense:Groceries       EXPENSE
   Expense:Auto            EXPENSE
   Expense:Medical         EXPENSE
   Equity                  EQUITY (placeholder)
   Equity:Opening Balances EQUITY
   ======================= =======================

Conventionally, the oldest transaction would be equity transfers from
Equity:Opening Balances to Asset and Liability Accounts. Most subsequent
transactions would be transfers from Income/Expense accounts to
Assets/Liability accounts (representing day-to-day activity e.g.
receiving salary, paying utility bill), or transfers between assets and
liability accounts (representing movements between loans and assets,
e.g. paying credit card bill, receiving a loan).

The following use cases will be illustrated, and the options to be
selected explained:

Using the Transaction Report to show previous year expenses
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The Transaction Report can show how much was spent on expense accounts
last year. This will usually be the most useful basic transaction report
format. To create this report:

1. Open the report options, from the Accounts tab, click the Expense
   placeholder account and Select Children.

2. From the General tab, Choose relative dates “Start of Previous Year”
   and “End of Previous Year”.

3. From the Sorting tab, set Primary Key to Accounts, and enable Primary
   Key Subtotal.

4. Set the Secondary Key to Date, and set the Secondary Key Subtotal to
   None.

Secondary level grouping
^^^^^^^^^^^^^^^^^^^^^^^^

The following will modify the above Transaction Report to use a
secondary grouping strategy. The first grouping (i.e. Primary Key =
Accounts, Subtotal = enabled) will group transactions from the same
accounts, whereas the secondary grouping (i.e. Secondary Key = Date,
Subtotal = Monthly) will also calculate monthly sums within each
account.

1. Select options as above

2. From the Sorting tab, set Secondary Key Subtotal to Monthly

Using secondary grouping for periodic comparison
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The Display / Subtotal Table adds a subtotal summary table, which will
ease comparison of accounts across date periods. This displays the same
subtotal calculations as the main table, presented in a grid structure.

In addition, if there are multiple primary-key groups (e.g. Date
grouping with monthly subtotals, across multiple months) the subtotal
table will also compute and display the primary-key grouping Average.
The average is computed as the total amount *per row*, divided by the
*number of columns*. This may cause confusion when computing monthly
spend averages, for instance, if a month has no transactions and is not
displayed in the table, it will *not* create a corresponding column in
the table, therefore the average amount will not reflect a true monthly
average.

1. Select options as above

2. From the Display tab, enable the Subtotal Table.

Use filtering to limit accounts and transactions
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Accounts and transactions can be filtered for reporting according to
account full name (e.g. ":Business:" will select account structure
Income:Business:Sales, Income:Business:Grants, Expenses:Business:Rent,
Expenses:Business:Utilities) or transaction description/notes/memo
(select transactions tagged #gift). The filtering text may be either a
standard string, or a POSIX regular expression.

1. From the Filter tab, complete the Account Name Filter, or Transaction
   Filter. Optionally toggle the regular expression check boxes to
   toggle full POSIX regex matching. Regular expressions will allow more
   complex queries e.g. the transaction filter can be set to
   (#gift|#travel) which will filter transactions with either #gift or
   #travel. They can be complicated and are best learned from external
   guides.

Using the Transaction Report to generate a reconciliation statement.
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This sortkey 'reconcile status' will separate reconciled, cleared and
unreconciled transactions. This report may be useful in producing a
printable reconciliation report.

Alternatively, the Reconciliation Report will preset these defaults and
requires only the Accounts selection.

1. From the Accounts tab, select the relevant bank or credit card
   account

2. From the General tab, choose an appropriate date range e.g. past 3
   months

3. From the Sorting tab, set the Primary Key to Reconcile Status,
   Primary Key Subtotal to enabled, and set the Secondary Key to Date.
   The Secondary Date Subtotal is left to None

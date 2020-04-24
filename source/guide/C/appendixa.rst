.. _appendixa:

Migration Guide
===============

This appendix is to help current users of other financial software
packages in their migration to GnuCash. We address the conceptual
differences between the layout of GnuCash accounts versus other software
packages.

.. _appendixa_accts_vs_cats1:

Using Accounts vs. Categories
=============================

If you are familiar with other personal finance programs, you are
already accustomed to tracking your income and expenses as categories.
Since GnuCash is a double-entry system (see
`??? <#basics-accounting1>`__), income and expenses are tracked in
accounts. The basic concept is the same, but the account structure
allows more consistency with accepted business practices. So, if you are
a business user as well as a home user, GnuCash makes it easy to keep
track of your business as well as your personal accounts.

Income and expense accounts give you the same information you would get
with categories, but they also give you more flexibility in entering
your transactions. In GnuCash, you have the option to enter transactions
directly into income and expense accounts through their account
registers. Other programs that use categories do not offer this option,
because there is no “account register” for a category.

You also have the option in GnuCash to treat income and expense accounts
exactly as you would treat categories, if you are more comfortable with
that method. In Quicken and similar programs, transactions require an
account and a category. Substitute an income or expense account name in
GnuCash where you would normally enter a category name in the other
programs, and the result should be the same. We will discuss transaction
entry in `??? <#basics-transactions2>`__ in greater detail.

.. _appendixa_import:

Importing Data
==============

If you want to import data from your previous application, you should
distinguish between financial data and other data. Probably the best way
to import financial data is the “Quicken Interchange Format” QIF . It is
a specific format for financial data, which most financial applications
for the private sector know and can use for export.

For other data we suggest the use of the “Comma Separated Value” CSV
format.

.. _appendixa_qif1:

Import of Financial Data by QIF Files
-------------------------------------

See ` <https://en.wikipedia.org/wiki/Quicken_Interchange_Format>`__ for
it's details.

Some GnuCash users collected their knowledge about the best use in our
` <https://wiki.gnucash.org/wiki/Quicken_Migration>`__.

For other formats and more details see `??? <#chapter_importing>`__.

.. _appendixa_business:

Import of Business Data by CSV Files
------------------------------------

If you want to import customers and vendors or bills and invoices see
`??? <#ch_import_bus_data>`__.

.. _appendixa_xmlconvert1:

Converting XML GnuCash File
===========================

The GnuCash XML data file can be transformed to almost any other data
format (e.g., QIF, CSV...) quite easily if one is familiar with the
“Extensible Stylesheet Language Transformations”
`XSLT <https://en.wikipedia.org/wiki/XSLT>`__. The GnuCash data file is
well-formed XML, and it can therefore be run through an XSLT parser with
an associated stylesheet. This allows one to transform the file to just
about any format that can be designed, given a properly written
stylesheet.

A few steps need to be followed. The writing of a stylesheet is a task
for a different time, but if you can get one written, here’s what you
need to do:

1. Copy the GnuCash XML data file to a working file.

   .. important::

      If the file was last modified by a version of GnuCash older than
      2.0, then before you continue to the next step you will need to
      modify the working file’s <gnc-v2> tag to read something like
      this: <gnc-v2 xmlns:cd="http://www.gnucash.org/XML/cd"
      xmlns:book="http://www.gnucash.org/XML/book"
      xmlns:gnc="http://www.gnucash.org/XML/gnc"
      xmlns:cmdty="http://www.gnucash.org/XML/cmdty"
      xmlns:trn="http://www.gnucash.org/XML/trn"
      xmlns:split="http://www.gnucash.org/XML/split"
      xmlns:act="http://www.gnucash.org/XML/act"
      xmlns:price="http://www.gnucash.org/XML/price"
      xmlns:ts="http://www.gnucash.org/XML/ts"
      xmlns:slot="http://www.gnucash.org/XML/kvpslot"
      xmlns:cust="http://www.gnucash.org/XML/cust"
      xmlns:entry="http://www.gnucash.org/XML/entry"
      xmlns:lot="http://www.gnucash.org/XML/lot"
      xmlns:invoice="http://www.gnucash.org/XML/invoice"
      xmlns:owner="http://www.gnucash.org/XML/owner"
      xmlns:job="http://www.gnucash.org/XML/job"
      xmlns:billterm="http://www.gnucash.org/XML/billterm"
      xmlns:bt-days="http://www.gnucash.org/XML/bt-days"
      xmlns:sx="http://www.gnucash.org/XML/sx"
      xmlns:fs="http://www.gnucash.org/XML/fs"
      xmlns:addr="http://www.gnucash.org/XML/custaddr">

   .. note::

      You can put pretty much anything you want behind the equal signs,
      but a unique URL is what is typically used.

2. Create an XSLT stylesheet containing the transformation your desire,
   or obtain one that’s already written.

   -  in our repository:
      ` <https://github.com/Gnucash/gnucash/tree/maint/contrib/xslt>`__

   -  in our wiki:
      ` <https://wiki.gnucash.org/wiki/De/export_to_excel_xls_transform>`__

3. Install an XSLT processor such as Saxon
   (` <https://en.wikipedia.org/wiki/Saxon_XSLT>`__) or Xalan
   (` <https://en.wikipedia.org/wiki/Apache_Xalan>`__). Any `conforming
   processor <https://en.wikipedia.org/wiki/Category:XSLT_processors>`__
   will do, really...

4. Run the work file and the stylesheet through the processor according
   to the processor’s instructions.

5. You will now have a file in the desired output format. An
   enterprising individual could go so far as to write a stylesheet to
   transform the GnuCash data file to an OpenOffice spreadsheet (or
   vice-versa, for that matter). Such things as QIF ought to be a little
   less work.

Benefits are that you don’t need to write a Scheme module or a new C
routine to do this transformation. Anyone who knows or can learn XML and
XSLT can perform this task. Not much harder, really, than writing a Web
page....

Anyhow, I just wanted this tidbit to be captured somewhere permanently.
The process works on 3.10 datafiles, and ought to work on earlier
versions, too.

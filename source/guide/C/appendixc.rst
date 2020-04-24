.. _appendixc:

Contributed Account Trees
=========================

This is an ancient example. For recent account trees see
` <https://github.com/Gnucash/gnucash/tree/maint/data/accounts>`__,
select your language and if existing region.

If you want to contribute your new or improved templates, read
` <https://wiki.gnucash.org/wiki/Translation#How_to_translate_the_files_containing_the_new_account_hierarchies>`__.

.. _appendixc_vat1:

UK Vat
======

Account types (only shown if different to parent type)

-  [E] Expense

-  [I] Income

-  [A] Asset

-  [L] Liability

-  [Q] Equity

-  [B] Bank accounts

-  [C] Credit Cards

-  [R] Accounts Receivable

-  [P] Accounts Payable

(Box n) refers to VAT form box number (I actually have these as
descriptions to the account to remind me)

Add all the (Box n -part) together to get the whole (Box n) The VAT
shows you liability - if its negative they owe you.

Capital Equipment (Box 7 - part) and (Box 6 - part) is the value of all
\*additions\* (purchases) made over the VAT return period - not the
absolute value, nor the difference in value unless that difference is
wholly due to new purchases. Depreciation, losses (e.g a write off of
faulty item) and other reductions in capital value are not included. If
you sell a capital item then that sale and its VAT is recorded under
Income. The asset is “converted to cash”, so the “net of VAT” increase
in your bank account, when the invoice is payed, is matched by a
decrease in capital.

::

   Bank Accounts [B]
     |___ Main Account
     |___  Reserve Account

   Cash [A]

   Assets [A]
     |___ Capital Equipment    (Box 7 - Part) - additions only, not absolute value
     |           |___ Computers      Can be depreciated to zero this year
     |           |___ EU reverse VAT purchase  (Box 6 - Part) create sub-accounts if needed
     |___  Other

   Receivable [R] Customers to whom you give credit - (business section)


   Cards [C]
     |___  Card 1

   Liabilities [L]
     |___  Owed Corp Tax
     |___  Owed Fees
     |___  Owed Tax / NI
     |___  Other

   VAT [L]   Net (Box 5)
     |___ i/p [A]   purchases (Box4)
     |___  o/p [L]     (Box3)
                |___EEC   on reverse VAT purchases (Box 2)
                |___Sales   all including zero rate UK/ EU  and World (Box1)

   Payable [P]   Suppliers who give you credit (business section)

   Equity [Q]
     |___  Corp Tax
     |___  Director’s Loan
     |___  Dividends
     |             |___  Director1
     |             |___  Director2
     |             |___  Shareholder 1
     |___ Grants (and stuff that does not count as income)
     |___Opening Balances

   Income [I]   (Box 6 - part)
      |___ Interest
      |___ Misc
      | ___ Sales
                   |___ EU
                   |     |____ goods  (Box 8) (sub accounts as needed)
                   |     |____ services includes software (sub accounts as needed)
                   | ___ UK
                   |____ World

   Expenses [E]
           |__Depreciation
           |__ Emoluments
           |            |___ Directors Fees
           |            |___ NI Employer
           |            |___ Employee 1
           |                     |___NI
           |                     |___Net Salary
           |                     |___Stakeholder
           |                     |___Tax
           |___ Other Non VAT Expenses
           |___ VAT Purchases    (Box 7 - part)
                       |___  Accountancy
                       |___  Bank Charges
                       |___  Consumables
                       |___  EU  reverse VAT purchases  (Box 6 - Part)
                       |         |___ goods (Box 9) (sub accounts as needed)
                       |         |___ services   includes software (sub accounts as needed)
                       |___  Office
                       |___  Phone and Internet
                       |___  Software
                       |___  Subscriptions
                       |___  Sundry
                       |___  Travel / Accom

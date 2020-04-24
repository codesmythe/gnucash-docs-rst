.. _chapter_expenses:

Expense Accounts
================

If managing your checkbook is the first step in tracking your finances,
then using expense accounts to see where you are expending money is a
close second step. This chapter will give you an understanding of how
GnuCash uses expense accounts to help you keep track of many different
categories of transactions.

.. _expenses-concepts:

Concepts
--------

An expense type account is used to allow you to track how much you spend
on specific expenses. Many people's first experience with tracking
expenses comes from Quicken(tm), where transactions can be assigned to
one or more categories. In GnuCash, these categories are set up as
separate accounts, which are designated as Expense type accounts. This
allows GnuCash to apply the rules of double-entry accounting
consistently. Expense accounts can be as detailed or as general as you
need. Some users need only a few accounts for personal expense tracking.
Others use GnuCash expense accounts to manage their expenses in great
detail. The level of detail you choose is up to you. Keep in mind that
with GnuCash, you can change accounts for transactions, so if your needs
change later on, it is possible to move transactions around.

.. _expenses-setup:

Setting Up Accounts
-------------------

.. _expenses-su-simple:

Simple Expense Account Setup
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

For many users, the easiest way to set up expense accounts is to check
the "Common Accounts" when you create a new Account Hierarchy. This will
establish many of the most common expense accounts that users need. See
"New Account Hierarchy Setup" in Chapter 3 of the Help guide for more
information.

.. _expenses-su-complex:

Complex Expense Account Setup
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

If you have different expense accounting needs, you can refer to
`??? <#chapter_txns>`__, or Chapter 5.4 in the Help manual for
instructions on how to create accounts.

Typical reasons for adding new or different expense accounts include: to
track expenses for particular business purposes (e.g., specific types of
supply expenses), to track expenses for particular tax purposes (e.g.,
tax expenses that must be reported to others), or simply to track
expenses that are meaningful to you (e.g., payments made to a particular
charity).

.. _expenses-entering:

Entering Expense Transactions
-----------------------------

While it is possible to enter transactions directly into expense
accounts, it is not normally how these are entered. For most people,
transactions for an expense account are added when the user is entering
data into the other account in the transaction. In other words, if you
have an expense account for Charitable Donations (e.g.,
Expenses:Charity), you will typically add a transaction to the expense
account by assigning a check in your checking account register to the
Charity account.

If you open an expense account, you will see a register similar to most
others you find in GnuCash. The informal column headings for the
transaction amounts are slightly different, however. The left (debit)
column will read *Tot Expense*, while the right (credit) column will
read *Tot Rebate*.

.. _expenses-other:

Other Considerations for Expense Accounts
-----------------------------------------

Because expense accounts are generated entirely by you, there are no
statements against which you would reconcile your data. Therefore, there
is technically nothing to reconcile. You can, of course use the
reconcile process for expense accounts, which will lock the transactions
for future editing.

One point to consider is that as your use of GnuCash continues, the
balances in these accounts will grow, since there are usually very few
credit transactions that reduce the balances. There is nothing wrong
with this situation, but some users may wish to clear the balances in
their expense accounts periodically. Zeroing transactions can be entered
that transfer the balance of the account to an Equity account. GnuCash
includes a Closing Books procedure that includes zeroing out expense
accounts. Keep in mind that this is not necessary, and that if you need
to gather information on a given expense account, you can use various
reports to extract that data without zeroing the account out.

.. _chapter_budgets:

Budgets
=======

This chapter explains how to create and use budgets with GnuCash.

.. _budget_concepts1:

Basic Concepts
--------------

A budget is a tool for estimating expected income and expenses. You can
use it to help you plan how you intend for your finances to change over
a period of time, and to examine how your actual financial transactions
for the period compare to your planned transactions.

The budgeting concept is quite general, so GnuCash offers a budgeting
tool that is both simple and flexible. You, the user, have to decide how
complex or simple you want to make your budget. This guide will help you
make some of those decisions.

.. _budget_conceptsterms2:

Terminology
~~~~~~~~~~~

There are a few helpful terms listed below that will be used to discuss
budgeting.

-  *Budget* - A financial plan describing the expected revenues and/or
   disbursements for a particular time period

-  *Cash Budget* - A budget planning for expected cash receipts and cash
   disbursements. This type of budget tracks cash flow -- where your
   money comes from, where it goes, and, of course, how much.

-  *Expense Budget* - A budget chiefly for planning what you spend your
   money on. This type of budget tracks your expenses. It is typically
   not concerned with things like appreciation or repayment of
   liabilities. However, it would account for interest charges. For
   example, if you buy $100 worth of groceries with your credit card,
   you incur an $100 expense for groceries, and a $100 liability to your
   credit card company. When you pay the credit card bill for $110, you
   are incurring an additional interest expense of $10. An expense
   budget plans for the transaction of buying the groceries and paying
   the interest, but not the transaction of repaying the credit card
   company.

-  *Capital Budget* - A budget that describes a plan for paying for a
   large future expense, often through a combination of saving and
   borrowing money. Note: Capital budgets can sometimes get quite
   complex because they can try to answer the question "Can we afford to
   do such-and-such?" by exploring various hypothetical scenarios that
   can involve hypothetical accounts.

-  *Budget Period* - The period of time during which the plan is
   expected to take place. The most common budget periods are annual and
   monthly. Sometimes, you may budget for several consecutive periods at
   once, for convenience or for finer-grained planning. For example, an
   annual budget may include 12 monthly budget periods.

.. _budget_creation1:

Creating a Budget
-----------------

Even before you begin to make a budget, it’s important to have given
some thought to your account hierarchy. For example, if you want to
budget a certain amount for your electric bill and a certain amount for
your water bill, you can’t have only an *Expenses:Utilities* account.
Your accounts must be at least as specific as your budget.

.. _budget_creation2:

Choose Which Accounts To Budget For
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The first step in creating a budget is to decide what it is you want to
plan for. This decision will affect which accounts you include in your
budget. For example, if you are only interested in tracking your
expenses, you may create an expense budget by only entering amounts for
expense accounts. On the other hand, if you want to track all of your
cash flow, you may create a cash flow budget by entering amounts for
asset, liability, income and expense accounts.

Before you begin to create your budget, you need to make two decisions:
What accounts do I want to budget for? and When do I want my budget to
be for? You can always change your mind later, after you’ve created a
budget, but you need to start with something.

.. tip::

   As a rule of thumb, if you mostly care about *what* you spend your
   money on, you may want to make an expense report. If you’re also
   concerned about having enough money in the right places at the right
   times, you may want to use a cash-flow budget.

Choosing a Budget Period
~~~~~~~~~~~~~~~~~~~~~~~~

Before creating a budget you must also decide what period of time you
want to plan for. The most common budget periods are monthly and annual.
If you want your budget to plan for changes in financial patterns over
time, then you should include multiple budget periods in your budget.
For example, if you want to plan on having higher utility expenses in
the winter than in the summer, then you might break your annual budget
into 4 quarters or even 12 months, and budget a higher value for the
winter periods than for the summer periods.

Getting Started
~~~~~~~~~~~~~~~

To create your first budget click on Actions > Budget > New Budget. You
will immediately see a new budget with the default settings and no
entries. Then click on the Options button. The most important options
are the budget period and the number of periods. For the budget period,
choose the beginning date and the smallest period of time that you want
to plan for. Then, for the number of periods, choose how many periods
you want to plan for.

The budget page now shows a list of accounts with a column for each
budget period. The date shown in the title of each column is the
beginning of that budget period.

Entering Budget Values
~~~~~~~~~~~~~~~~~~~~~~

Now, you must enter the budget values - the amounts that you expect the
account balances to change during the budget period. There are two ways
to enter budget values. The first way is to simply click on the cell and
enter an amount.

If you have past transactions recorded in GnuCash, the second way is to
let GnuCash estimate the budget values by looking at those transactions.
First, select the accounts you want GnuCash to estimate. Then click on
the Estimate *Toolbar* button. In the Estimate Budget Values dialog,
select the date past which GnuCash should look for past transactions.
GnuCash will start at that date and look forward for the duration of
your budget. For example, if you are making an annual budget, and you
select Jan. 1, 2005, GnuCash will look at all the transactions in that
account from Jan. 1, 2005 through Dec. 31, 2005.

.. _budget_reporting1:

Budget Reporting
----------------

You’ve already done the hardest part - creating your budget. But now you
want to know how your actual financial transactions compare to your
plan. You need to run the Budget Report.

Click on Reports > Budget > Budget Report. For each account, the Budget
Report will show the budgeted and the actual amounts in two adjacent
columns for each period in the budget. If you have created multiple
budgets, you can use the Budget Report Options to select which budget to
use in the report.

Two other types of budget reports are commonly used in the small
business setting. They are the *Budgeted Income Statement* and the
*Budgeted Balance Sheet*.

Budgeted Income Statement
~~~~~~~~~~~~~~~~~~~~~~~~~

The budgeted income statement is similar to the income statement. Both
show the revenues and expenses for a given period as well as the profit,
which is the difference revenue - expenses. The income statement is
based on historical data, but the *budgeted* income statement is based
on the predictions made in the budget.

Budgeted Balance Sheet
~~~~~~~~~~~~~~~~~~~~~~

The budgeted balance sheet is similar to the balance sheet. Both show
the assets, liabilities, and equity. The difference is that the balance
sheet is based on historical data, and the *budgeted* balance sheet is
based on the predictions made in the budget.

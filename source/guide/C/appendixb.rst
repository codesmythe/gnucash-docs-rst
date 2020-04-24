.. _appendixb:

Frequently Asked Questions
==========================

   This is a list of questions asked on the mailing lists for which
   there really is no section in the documentation covering the subject.

.. _appendixb_info:

Sources of Information
======================

**Q:** Where is the FAQ?

**A:** You’re looking at an very old copy of it. The most up-to-date
copy can be found within the `GnuCash
Wiki <https://wiki.gnucash.org/wiki/FAQ>`__.

**Q:** Are there mailing lists for GnuCash?

**A:** Yes. Go to
` <https://lists.gnucash.org/mailman/listinfo/gnucash-user>`__ and
` <https://lists.gnucash.org/mailman/listinfo/gnucash-devel>`__ to
subscibe.

**Q:** Is there a searchable archive for the mailing lists?

**A:** Yes, you can search the mail list archives at
` <http://news.gmane.org/gmane.comp.gnome.apps.gnucash.devel>`__ and
` <http://news.gmane.org/gmane.comp.gnome.apps.gnucash.user>`__ (and
` <http://news.gmane.org/gmane.comp.gnome.apps.gnucash.german>`__ if you
speak German).

**Q:** Are there other means of obtaining support for GnuCash?

**A:** Yes. Many of the developers hang out on icq in the #gnucash
discussion on ` <irc://irc.gnome.org/gnucash>`__. Also, there is a
`wiki <https://wiki.gnucash.org/wiki/>`__ online.

.. _appendixb_general:

General Information
===================

**Q:** Can I run GnuCash on Windows?

**A:** Yes. Starting with release 2.2.0, GnuCash is also available on
Windows.

**A:** Other related options would be colinux, VMWare and a
windows-based X-server hosting a remote GnuCash session.

**Q:** I heard it is too hard to compile GnuCash!

**A:** This was probably true at the time when 1.6.0 was released. It is
no longer true today, as almost every distribution ships with all the
necessary libraries. However, by default, distributions won’t install
the development packages of the required libraries, so you might need to
start your distribution’s installer program and tell it to install not
only the library packages but also the -devel packages. In general, it
was noted that this problem concerns many applications in the gnome
domain, and this also boils down to the fact that there is no such thing
as “one monolithic gnome package”.

**Q:** Is there a batch mode (non-interactive) available for GnuCash,
for building reports, etc?

**A:** No, for now GnuCash must be run interactively.

**Q:** Can multiple people access the same datafile in GnuCash?

**A:** You can have multiple people with access to the same datafile,
but they cannot use the data file simultaneously.

To setup multi-person access, all the people must have read/write access
to the directory containing the file (to read the other’s created files,
and to create new files). One way to do this is by creating a user group
and setting the data directory to be owned by the shared group and set
to mode 2775. The “2” makes the directory setgid which copies the
permissions to all files.

**Q:** Why is GnuCash written in C?

**A:** The core functionality of GnuCash is written in C, but do not
forget that much of this can be accessed through Guile (scheme). There
are a number of reasons for why GnuCash is written in C. The first is
historical, GnuCash was started in 1996 (or maybe even earlier!) and
many of the OOP (C++, Java, Python) compilers were not yet mature and
standarized enough on the variety of platforms considered at that time,
so C was the only option at that time. A second reason is because the
standard GUI GnuCash uses is GTK, which is written in C.

**Q:** Why don’t you rewrite GnuCash in programming language xyz so that
I can contribute easily?

**A:** The quick answer is “We won’t”.

**A:** The longer answer is complex but still amounts to “We won’t”.
GnuCash is a large body of code maintained by a small group of
developers who are comfortable in C and Scheme (Guile). Actually, 80% of
it is in C and approx. 13% is in Scheme/Lisp. There is no valid reason
that would justify rewriting this amount of existing code in a newer
language. Also, creating language bindings to recent languages such as
Python or Ruby or (insert your favourite language here) is labor
intensive, and we’re already stretched pretty thin maintaining and
developing the existing code.

**A:** Having said that, this is an open source project and you’re free
to do with it or contribute what you want. Just don’t expect much
support if the reason for your changes is that you’re not willing to
learn C or Scheme. Also, GnuCash used to have SWIG bindings
(` <http://www.swig.org>`__) which have been used for some perl
programming code. According to a list discussion, these SWIG bindings
might still be a way to include other languages into GnuCash, but
currently they are unused and unmaintained.

**Q:** I really want feature XYZ but GnuCash doesn’t have it. How do I
get it added?

**A:** Ask nicely. :-) You can file an enhancement request at
` <https://bugs.gnucash.org/>`__. Please bear in mind to describe your
proposed enhancement as verbosely as possible. The trick here is to
learn how to give the best information to the programmers about what
your proposed new feature should do. If you want to speed up development
significantly, consider donating some money as described on
GnuCashDevelopment.

**Q:** Is there a web interface available for GnuCash?

**A:** No

**Q:** How can I provide security for GnuCash data using CFS, etc.)

**A:** Unanswered

**Q:** How can I contribute to the GnuCash project?

**A:** We’re working on a more formal process, but for now you should
subscribe to the mailing list at
` <https://lists.gnucash.org/mailman/listinfo/gnucash-user>`__ and
` <https://lists.gnucash.org/mailman/listinfo/gnucash-devel>`__ and
discuss what you can contribute with the participants on the lists.
Please be aware that GnuCash is a large body of code written in C and
Scheme (see “`#appendixb_general_WhyC <#appendixb_general_WhyC>`__”
above, if you want to know why). If these are languages that you are not
willing to work with, consider contributing in other ways.

**Q:** I think I found a bug. How do I report it?

**A:** First of all, try to verify that it is indeed a bug and that it
has not been reported before. Search the mail list archives (see FAQ
above). Then search the `GnuCash Bugzilla <https://bugs.gnucash.org/>`__
database.

If you feel you have indeed found a bug, you can then report it at
` <https://bugs.gnucash.org/>`__. Please bear in mind to report your bug
as verbosely as possible. The trick here is to learn how to give the
best information to the programmers about how to reproduce bugs. A
Programmer will usually only be able to fix a bug they can see, if you
can’t make the programmer see your bug, it won’t get fixed!

.. _appendixb_using:

Using GnuCash
=============

**Q:** How can I move the transactions from account “A” into account
“B”, thus combining them?

**A:** At present, GnuCash does not offer a way to move groups of splits
from one account to another. You will need to move them one at a time.
Open the register for account “A” and select the pulldown menu item View
> Transaction Journal to expose all the splits. For every split where
the “Account” field shows account “A” reset it to account “B”. To do
this quickly and safely, first use Ctrl+C to copy the destination
account name (“account B”) to the clipboard. Then highlight each
reference to account “A” by double clicking on it and use Ctrl+V to
paste the destination account name. Pressing Enter after each paste,
silently moves the transaction out of the register.

.. caution::

   If you inadvertently set the “Account” field to an unintended
   location, you will need to search through all your accounts to find
   the lost transaction to correct your mistake.

**Q:** Is it possible to merge two GnuCash files?

**A:** At present this is not possible.

**Q:** How can I save a template of my account structure?

**A:** This is available from the menu: File > Export > Export Accounts

**Q:** When I search for customers (or anything else for that matter),
how can I return a list of everything?

**A:** Enter a search criteria of matches regex, and place a single dot
“.” in the text field area. Then, click Find. The regular expression “.”
means to match anything.

**Q:** How can I record a transaction on different dates (actual date
and bank date)?

**A:** You record the transaction on the date you write the check or
initiate the transaction. When it “clears” the bank, you can click in
the “Reconciled” field to “clear” the transaction (change the
“n”on-reconciled to “c”leared).

.. _appendixb_accounting:

Accounting
==========

**Q:** How do I treat taxes? As an account payable or as an expense?

**A:** This is a loaded question, and you should really talk to your
accountant. How you treat taxes really depends on what kind of taxes
they are, and how you WANT to treat them.. In some cases they are
expenses, in some cases they are liabilities.

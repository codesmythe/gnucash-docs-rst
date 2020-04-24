.. _ch_python_bindings:

Python Bindings
===============

GnuCash historically has always been a traditional application in the
sense that you open it, use it to manipulate your financial data via the
windows it presents, save your data and close the windows again. This
has the inherent limitation that you can only do whatever the windows,
menus and toolbars allow you to do.

Sometimes you might need a little more flexibility. For example, you
need a report with just a little different information than what the
built-in reports provide, or you want to automate a frequently recurring
action. Such custom manipulations are ideal candidates to write in one
or the other scripting language.

Starting with GnuCash version 2.4 you can write Python scripts to
manipulate your financial data.

.. note::

   The Python extensions are an optional feature in the source code. To
   be able to use Python scripts, GnuCash must have been compiled with
   this option enabled, otherwise all what follows won’t work. At
   present this option is not enabled by default, so if you need this,
   you may have to compile GnuCash from source yourself.

The Python extensions come with a couple of ready to use scripts. This
chapter will show you how to use some of these.

.. note::

   This chapter is not about how to write your own Python scripts. Refer
   to the developer documentation for that instead.

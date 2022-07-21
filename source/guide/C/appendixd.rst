.. _appendixd:

Auxiliary File Formats
======================

These are the formats of some auxiliary files used by GnuCash.

.. _check_format_info:

Check Format Files (``*.chk``)
==============================

.. _check_format_overview:

Overview
--------

The check format file is used to tell GnuCash how to print a check or
checks onto a page of paper. This file first describes the overall
layout of a page (number of checks, orientation, etc) and then describes
the layout of the specific items on a single check. The file is
organized as a typical Key/Value file used by many Linux applications.
Keys/values pairs are grouped into sections that begin with the group
name enclosed in square brackets. Units for angles are degrees and length
and coordinate units are PostScript (PS) points (72 PS points = 1 inch).

GnuCash looks for check format files in two different locations when you
bring up the check printing dialog. The first location is typically
``/usr/share/gnucash/checks``, where check files distributed with the
application can be found. The second location is the user private
``~/.local/share/gnucash/checks``  [1]_ directory. Users may add check
formats at any time (even while GnuCash is running) simply by dropping a
new ``*.chk`` file in this directory. The next time the check printing
dialog is opened the new check format will appear in the list of
available check formats.

.. note::

   Printing functions behave differently depending on the version of GTK that
   is installed on your system. When GnuCash is using a version of GTK
   prior to 2.10 all offsets are measured from the lower left corner of
   the page or check. When using GTK 2.10 or later, all offsets are
   measured from the upper left corner of the page or check.

Example file
------------

A typical GnuCash check file is presented below. The contents of this
file will be described in the next sections.

::

   [Top]
   Guid = 67b144d1-96a5-48d5-9337-0e1083bbf229
   Title = Quicken/QuickBooks (tm) US-Letter
   Rotation = 0.0
   Translation = 0.0;4.0
   Show_Grid = false
   Show_Boxes = false

   [Check Positions]
   Height = 252.0
   Names = Top;Middle;Bottom

   [Check Items]
   Type_1 = PAYEE
   Coords_1 = 90.0;102.0;400.0;20.0

   Type_2 = AMOUNT_WORDS
   Coords_2 = 90.0;132.0

   Type_3 = AMOUNT_NUMBER
   Blocking_Chars_3 = true
   Coords_3 = 500.0;102.0

   Type_4 = DATE
   Coords_4 = 500.0;67.0

   Type_5 = NOTES
   Coords_5 = 50.0;212.0
           

Field Descriptions
------------------

Top Group
~~~~~~~~~

This section of the check file describes the overall layout of a page of
checks (or check) that goes into the printer.

.. table:: Overall Page Description Fields

   +----------------+-----------------+-----------+-----------------+
   | Name           | Type            | Required  | Description     |
   +================+=================+===========+=================+
   | Guid           | string          | mandatory | The guid is     |
   |                |                 |           | used to         |
   |                |                 |           | uniquely        |
   |                |                 |           | identify a      |
   |                |                 |           | check format to |
   |                |                 |           | GnuCash. It     |
   |                |                 |           | must be unique  |
   |                |                 |           | across the      |
   |                |                 |           | entire set of   |
   |                |                 |           | application     |
   |                |                 |           | supplied and    |
   |                |                 |           | user supplied   |
   |                |                 |           | check formats.  |
   |                |                 |           | If you copy an  |
   |                |                 |           | application     |
   |                |                 |           | check file as   |
   |                |                 |           | the basis of    |
   |                |                 |           | your own check  |
   |                |                 |           | format, you     |
   |                |                 |           | must change     |
   |                |                 |           | this value. The |
   |                |                 |           | *uuidgen*       |
   |                |                 |           | program may be  |
   |                |                 |           | used to         |
   |                |                 |           | generate these  |
   |                |                 |           | identifiers.    |
   +----------------+-----------------+-----------+-----------------+
   | Title          | string          | mandatory | The title is    |
   |                |                 |           | used to         |
   |                |                 |           | uniquely        |
   |                |                 |           | identify a      |
   |                |                 |           | check format to |
   |                |                 |           | the user. This  |
   |                |                 |           | value is        |
   |                |                 |           | presented       |
   |                |                 |           | verbatim in the |
   |                |                 |           | check format    |
   |                |                 |           | list of the     |
   |                |                 |           | check printing  |
   |                |                 |           | dialog. If you  |
   |                |                 |           | copy an         |
   |                |                 |           | application     |
   |                |                 |           | check file as   |
   |                |                 |           | the basis of    |
   |                |                 |           | your own check  |
   |                |                 |           | format, you     |
   |                |                 |           | should change   |
   |                |                 |           | this value. The |
   |                |                 |           | title may be    |
   |                |                 |           | any utf-8       |
   |                |                 |           | string.         |
   +----------------+-----------------+-----------+-----------------+
   | Font           | string          | optional  | If supplied,    |
   |                |                 |           | this is the     |
   |                |                 |           | default font    |
   |                |                 |           | used to print   |
   |                |                 |           | all text items  |
   |                |                 |           | on this check.  |
   |                |                 |           | This field can  |
   |                |                 |           | contain any     |
   |                |                 |           | string that is  |
   |                |                 |           | acceptable by   |
   |                |                 |           | gtk as a font   |
   |                |                 |           | specifier. If   |
   |                |                 |           | this field is   |
   |                |                 |           | omitted, the    |
   |                |                 |           | default font is |
   |                |                 |           | the font        |
   |                |                 |           | specified in    |
   |                |                 |           | the GnuCash     |
   |                |                 |           | preferences     |
   |                |                 |           | dialog. A       |
   |                |                 |           | typical string  |
   |                |                 |           | would be “sans  |
   |                |                 |           | 12”.            |
   +----------------+-----------------+-----------+-----------------+
   | Blocking_Chars | boolean         | optional  | If supplied,    |
   |                |                 |           | this is the     |
   |                |                 |           | default used    |
   |                |                 |           | when printing   |
   |                |                 |           | all *TEXT*      |
   |                |                 |           | items on this   |
   |                |                 |           | check. When set |
   |                |                 |           | to true, will   |
   |                |                 |           | print *\**\**   |
   |                |                 |           | before and      |
   |                |                 |           | after each text |
   |                |                 |           | field on the    |
   |                |                 |           | check. Blocking |
   |                |                 |           | characters are  |
   |                |                 |           | printed to      |
   |                |                 |           | protect check   |
   |                |                 |           | fields from     |
   |                |                 |           | alteration. For |
   |                |                 |           | example, the    |
   |                |                 |           | amount field    |
   |                |                 |           | may be printed  |
   |                |                 |           | as              |
   |                |                 |           | *               |
   |                |                 |           | \***100.00**\** |
   +----------------+-----------------+-----------+-----------------+
   | DateFormat     | boolean         | optional  | If supplied,    |
   |                |                 |           | this is the     |
   |                |                 |           | default used    |
   |                |                 |           | when printing   |
   |                |                 |           | all *DATE*      |
   |                |                 |           | items on this   |
   |                |                 |           | check. When set |
   |                |                 |           | to true, will   |
   |                |                 |           | print the       |
   |                |                 |           | format of the   |
   |                |                 |           | DATE in 8 point |
   |                |                 |           | type, centered  |
   |                |                 |           | and below the   |
   |                |                 |           | actual DATE.    |
   |                |                 |           | For example     |
   |                |                 |           | DDMMYYYY.       |
   +----------------+-----------------+-----------+-----------------+
   | Rotation       | double          | optional  | This value      |
   |                |                 |           | specified the   |
   |                |                 |           | rotation of the |
   |                |                 |           | entire page (in |
   |                |                 |           | degrees) around |
   |                |                 |           | the origin      |
   |                |                 |           | point. For gtk  |
   |                |                 |           | versions prior  |
   |                |                 |           | to 2.10, the    |
   |                |                 |           | origin point is |
   |                |                 |           | in the lower    |
   |                |                 |           | left corner of  |
   |                |                 |           | the page and    |
   |                |                 |           | rotation values |
   |                |                 |           | increase in the |
   |                |                 |           | co              |
   |                |                 |           | unter-clockwise |
   |                |                 |           | direction. For  |
   |                |                 |           | gtk version     |
   |                |                 |           | 2.10 and later, |
   |                |                 |           | the origin      |
   |                |                 |           | point is in the |
   |                |                 |           | upper left      |
   |                |                 |           | corner of the   |
   |                |                 |           | page and        |
   |                |                 |           | rotation values |
   |                |                 |           | increase in the |
   |                |                 |           | clockwise       |
   |                |                 |           | direction.      |
   |                |                 |           | Rotation of the |
   |                |                 |           | page is applied |
   |                |                 |           | before          |
   |                |                 |           | translation.    |
   +----------------+-----------------+-----------+-----------------+
   | Translation    | list of 2       | optional  | These values    |
   |                | doubles         |           | specify the x   |
   |                |                 |           | and y           |
   |                |                 |           | translation of  |
   |                |                 |           | the entire page |
   |                |                 |           | (in points)     |
   |                |                 |           | relative to the |
   |                |                 |           | origin point.   |
   |                |                 |           | For gtk         |
   |                |                 |           | versions prior  |
   |                |                 |           | to 2.10, the    |
   |                |                 |           | origin point is |
   |                |                 |           | in the lower    |
   |                |                 |           | left corner of  |
   |                |                 |           | the page and    |
   |                |                 |           | translation     |
   |                |                 |           | values increase |
   |                |                 |           | moving up and   |
   |                |                 |           | to the right.   |
   |                |                 |           | For gtk version |
   |                |                 |           | 2.10 and later, |
   |                |                 |           | the origin      |
   |                |                 |           | point is in the |
   |                |                 |           | upper left      |
   |                |                 |           | corner of the   |
   |                |                 |           | page and        |
   |                |                 |           | translation     |
   |                |                 |           | values increase |
   |                |                 |           | moving down and |
   |                |                 |           | to the right.   |
   |                |                 |           | Rotation of the |
   |                |                 |           | page is applied |
   |                |                 |           | before          |
   |                |                 |           | translation.    |
   +----------------+-----------------+-----------+-----------------+
   | Show_Grid      | boolean         | optional  | If this value   |
   |                |                 |           | is set to       |
   |                |                 |           | *true* then     |
   |                |                 |           | GnuCash will    |
   |                |                 |           | draw a grid on  |
   |                |                 |           | the page,       |
   |                |                 |           | starting at the |
   |                |                 |           | origin with the |
   |                |                 |           | lines spaced    |
   |                |                 |           | every 50        |
   |                |                 |           | points. This    |
   |                |                 |           | can be helpful  |
   |                |                 |           | when creating a |
   |                |                 |           | check format    |
   |                |                 |           | file.           |
   +----------------+-----------------+-----------+-----------------+
   | Show_Boxes     | boolean         | optional  | If this value   |
   |                |                 |           | is set to       |
   |                |                 |           | *true* then for |
   |                |                 |           | each item where |
   |                |                 |           | the width and   |
   |                |                 |           | height have     |
   |                |                 |           | been specified, |
   |                |                 |           | GnuCash will    |
   |                |                 |           | draw a box      |
   |                |                 |           | showing         |
   |                |                 |           | location and    |
   |                |                 |           | maximum size of |
   |                |                 |           | that item .     |
   |                |                 |           | This can be     |
   |                |                 |           | helpful when    |
   |                |                 |           | creating a      |
   |                |                 |           | check format    |
   |                |                 |           | file.           |
   +----------------+-----------------+-----------+-----------------+

.. note::

   The Blocking_Chars and DateFormat options are defined for all check
   formats in Edit->Preferences->Printing. It is recommened that these
   global options be set to false (the default), and that the options be
   set for individual Check Items as described below.

Check Positions Group
~~~~~~~~~~~~~~~~~~~~~

This group of items specifies how multiple checks are laid out on the
same sheet of paper, and gives names to each of these check locations so
that a user can specify which check location that GnuCash should print.
This entire group of key/value pairs is optional, and should be omitted
if the format file only specifies a single check per page of paper.

.. table:: Multiple Checks Per Page Fields

   +--------+-----------------+-----------+----------------------+
   | Name   | Type            | Required  | Description          |
   +========+=================+===========+======================+
   | Height | double          | mandatory | This field specifies |
   |        |                 |           | the height of a      |
   |        |                 |           | single check on the  |
   |        |                 |           | page. If there are   |
   |        |                 |           | multiple checks per  |
   |        |                 |           | page then this item  |
   |        |                 |           | is mandatory. If     |
   |        |                 |           | there is only a      |
   |        |                 |           | single check per     |
   |        |                 |           | page, this entire    |
   |        |                 |           | section should be    |
   |        |                 |           | omitted.             |
   +--------+-----------------+-----------+----------------------+
   | Names  | list of strings | mandatory | This field specifies |
   |        |                 |           | the names of the     |
   |        |                 |           | check locations that |
   |        |                 |           | can be printed on    |
   |        |                 |           | each page. These     |
   |        |                 |           | names represent the  |
   |        |                 |           | check positions      |
   |        |                 |           | starting from the    |
   |        |                 |           | top of the page and  |
   |        |                 |           | moving downward. The |
   |        |                 |           | names are presented  |
   |        |                 |           | verbatim in the      |
   |        |                 |           | check position list  |
   |        |                 |           | of the check         |
   |        |                 |           | printing dialog. A   |
   |        |                 |           | typical value for    |
   |        |                 |           | this field is        |
   |        |                 |           | "Top;Middle;Bottom", |
   |        |                 |           | but it could also be |
   |        |                 |           | "First;Second;Third" |
   |        |                 |           | or any other set of  |
   |        |                 |           | strings that clearly |
   |        |                 |           | identify the check   |
   |        |                 |           | locations. If there  |
   |        |                 |           | are multiple checks  |
   |        |                 |           | per page then this   |
   |        |                 |           | item is mandatory.   |
   |        |                 |           | If there is only a   |
   |        |                 |           | single check per     |
   |        |                 |           | page, this entire    |
   |        |                 |           | section should be    |
   |        |                 |           | omitted.             |
   +--------+-----------------+-----------+----------------------+

Check Items Group
~~~~~~~~~~~~~~~~~

This section specifies the individual items that are printed on the
check. There is no limit to the number of items that may be present in
this section, and any given type of item can be repeated multiple times.
This allows for the printing of checks that have a side stub, or for the
one-per-page business checks that have both the check and multiple check
stubs on the same page. For example, to print the payee name on a
business check and on both stubs, simply specify three payee items with
differing print coordinates.

Each key names in this section explicitly includes the item number to
which it applies. E.G. The key named Type_1 applies to the first item to
be printed, and the key Coords_3 applies to the third item to be
printed. Item numbers start at one and increase sequentially. Any gap in
the numbering sequence is interpreted by GnuCash as the end of the item
list. Items are printed in the order of their item numbers, not in the
order in which they appear in the file.

Each item specified must include a type declaration. The rest of the
parameters for that item depend upon the particular type of that item.
See `table_title <#check_table_types>`__ for a list of valid item types
and their required parameters.

.. table:: Individual Check Item Fields

   +-----------------+-----------------+-----------+-----------------+
   | Name            | Type            | Required  | Description     |
   +=================+=================+===========+=================+
   | Type\_\ *n*     | string          | mandatory | This field      |
   |                 |                 |           | specifies the   |
   |                 |                 |           | type of a       |
   |                 |                 |           | single item to  |
   |                 |                 |           | be printed on a |
   |                 |                 |           | check. See      |
   |                 |                 |           | `table          |
   |                 |                 |           | _title <#check_ |
   |                 |                 |           | table_types>`__ |
   |                 |                 |           | for a list of   |
   |                 |                 |           | valid item      |
   |                 |                 |           | types.          |
   +-----------------+-----------------+-----------+-----------------+
   | Coords\_\ *n*   | list of 2 or 4  | mandatory | This field      |
   |                 | doubles         |           | specifies the   |
   |                 |                 |           | coordinates     |
   |                 |                 |           | where the item  |
   |                 |                 |           | should be       |
   |                 |                 |           | placed on a     |
   |                 |                 |           | check, and      |
   |                 |                 |           | optionally also |
   |                 |                 |           | specifies the   |
   |                 |                 |           | width and       |
   |                 |                 |           | height of the   |
   |                 |                 |           | item. The       |
   |                 |                 |           | numbers in      |
   |                 |                 |           | order are the X |
   |                 |                 |           | and Y offset of |
   |                 |                 |           | the lower left  |
   |                 |                 |           | corner of the   |
   |                 |                 |           | item, and       |
   |                 |                 |           | optionally the  |
   |                 |                 |           | width and       |
   |                 |                 |           | height of the   |
   |                 |                 |           | item. If the    |
   |                 |                 |           | width is        |
   |                 |                 |           | supplied then   |
   |                 |                 |           | the height must |
   |                 |                 |           | also be         |
   |                 |                 |           | supplied, so    |
   |                 |                 |           | this field will |
   |                 |                 |           | always contain  |
   |                 |                 |           | two or four     |
   |                 |                 |           | numbers. For    |
   |                 |                 |           | gtk versions    |
   |                 |                 |           | prior to 2.10,  |
   |                 |                 |           | the origin      |
   |                 |                 |           | point is in the |
   |                 |                 |           | lower left      |
   |                 |                 |           | corner of the   |
   |                 |                 |           | page and        |
   |                 |                 |           | translation     |
   |                 |                 |           | values increase |
   |                 |                 |           | moving up and   |
   |                 |                 |           | to the right.   |
   |                 |                 |           | For gtk version |
   |                 |                 |           | 2.10 and later, |
   |                 |                 |           | the origin      |
   |                 |                 |           | point is in the |
   |                 |                 |           | upper left      |
   |                 |                 |           | corner of the   |
   |                 |                 |           | page and        |
   |                 |                 |           | translation     |
   |                 |                 |           | values increase |
   |                 |                 |           | moving down and |
   |                 |                 |           | to the right.   |
   |                 |                 |           |                 |
   |                 |                 |           | .. note::       |
   |                 |                 |           |                 |
   |                 |                 |           |    Regardless   |
   |                 |                 |           |    of whether   |
   |                 |                 |           |    the origin   |
   |                 |                 |           |    is at the    |
   |                 |                 |           |    top or the   |
   |                 |                 |           |    bottom of    |
   |                 |                 |           |    the page,    |
   |                 |                 |           |    the          |
   |                 |                 |           |    coordinates  |
   |                 |                 |           |    always       |
   |                 |                 |           |    specify the  |
   |                 |                 |           |    lower left   |
   |                 |                 |           |    point of the |
   |                 |                 |           |    item.        |
   +-----------------+-----------------+-----------+-----------------+
   | Font\_\ *n*     | string          | optional  | If supplied,    |
   |                 |                 |           | this is the     |
   |                 |                 |           | font used to    |
   |                 |                 |           | print this      |
   |                 |                 |           | specific text   |
   |                 |                 |           | item. This      |
   |                 |                 |           | field can       |
   |                 |                 |           | contain any     |
   |                 |                 |           | string that is  |
   |                 |                 |           | acceptable by   |
   |                 |                 |           | gtk as a font   |
   |                 |                 |           | specifier. If   |
   |                 |                 |           | this field is   |
   |                 |                 |           | omitted, the    |
   |                 |                 |           | default font is |
   |                 |                 |           | the font        |
   |                 |                 |           | specified in    |
   |                 |                 |           | the *Top*       |
   |                 |                 |           | section of the  |
   |                 |                 |           | check           |
   |                 |                 |           | description     |
   |                 |                 |           | file, or if     |
   |                 |                 |           | that was        |
   |                 |                 |           | omitted the     |
   |                 |                 |           | font specified  |
   |                 |                 |           | in the GnuCash  |
   |                 |                 |           | preferences     |
   |                 |                 |           | dialog. This    |
   |                 |                 |           | field is only   |
   |                 |                 |           | recognized when |
   |                 |                 |           | using gtk       |
   |                 |                 |           | version 2.10 or |
   |                 |                 |           | later.          |
   +-----------------+-----------------+-----------+-----------------+
   | Align\_\ *n*    | string          | optional  | If supplied,    |
   |                 |                 |           | this is the     |
   |                 |                 |           | alignment used  |
   |                 |                 |           | to print this   |
   |                 |                 |           | specific text   |
   |                 |                 |           | item. This      |
   |                 |                 |           | field must      |
   |                 |                 |           | contain one of  |
   |                 |                 |           | the strings     |
   |                 |                 |           | “left”,         |
   |                 |                 |           | “center” or     |
   |                 |                 |           | “right”. If     |
   |                 |                 |           | this field is   |
   |                 |                 |           | omitted, the    |
   |                 |                 |           | text will be    |
   |                 |                 |           | left aligned.   |
   |                 |                 |           | This field is   |
   |                 |                 |           | only recognized |
   |                 |                 |           | when using gtk  |
   |                 |                 |           | version 2.10 or |
   |                 |                 |           | later.          |
   +-----------------+-----------------+-----------+-----------------+
   | Text\_\ *n*     | string          | optional  | This field is   |
   |                 |                 |           | only used when  |
   |                 |                 |           | the item type   |
   |                 |                 |           | is *TEXT*. It   |
   |                 |                 |           | specifies the   |
   |                 |                 |           | utf-8 text that |
   |                 |                 |           | should be       |
   |                 |                 |           | printed on the  |
   |                 |                 |           | check.          |
   +-----------------+-----------------+-----------+-----------------+
   | Filename\_\ *n* | string          | optional  | This field is   |
   |                 |                 |           | only used when  |
   |                 |                 |           | the item type   |
   |                 |                 |           | is *PICTURE*.   |
   |                 |                 |           | It specifies    |
   |                 |                 |           | the filename of |
   |                 |                 |           | the image that  |
   |                 |                 |           | should be       |
   |                 |                 |           | printed on the  |
   |                 |                 |           | check. The      |
   |                 |                 |           | string may      |
   |                 |                 |           | specify either  |
   |                 |                 |           | an absolute     |
   |                 |                 |           | path name or as |
   |                 |                 |           | a relative path |
   |                 |                 |           | name. If a      |
   |                 |                 |           | relative path   |
   |                 |                 |           | name is         |
   |                 |                 |           | specified,      |
   |                 |                 |           | GnuCash first   |
   |                 |                 |           | looks in in the |
   |                 |                 |           | application     |
   |                 |                 |           | check format    |
   |                 |                 |           | folder          |
   |                 |                 |           | (typically      |
   |                 |                 |           | ``/usr/share/g  |
   |                 |                 |           | nucash/checks`` |
   |                 |                 |           | ) for the image |
   |                 |                 |           | file, and if it |
   |                 |                 |           | is not found    |
   |                 |                 |           | there then it   |
   |                 |                 |           | looks in the    |
   |                 |                 |           | user private    |
   |                 |                 |           | ``~             |
   |                 |                 |           | /.local/share/g |
   |                 |                 |           | nucash/checks`` |
   |                 |                 |           | directory for   |
   |                 |                 |           | the image. This |
   |                 |                 |           | field is only   |
   |                 |                 |           | recognized when |
   |                 |                 |           | using gtk       |
   |                 |                 |           | version 2.10 or |
   |                 |                 |           | later.          |
   +-----------------+-----------------+-----------+-----------------+
   | Blocki          | boolean         | optional  | If supplied,    |
   | ng_Chars\_\ *n* |                 |           | this will set   |
   |                 |                 |           | the print       |
   |                 |                 |           | *               |
   |                 |                 |           | Blocking_Chars* |
   |                 |                 |           | option for this |
   |                 |                 |           | item.           |
   +-----------------+-----------------+-----------+-----------------+
   | Da              | boolean         | optional  | If supplied,    |
   | teFormat\_\ *n* |                 |           | this will set   |
   |                 |                 |           | the print       |
   |                 |                 |           | *DateFormat*    |
   |                 |                 |           | option for this |
   |                 |                 |           | item.           |
   +-----------------+-----------------+-----------+-----------------+

These are the individual items that can be printed on a check. All items
require the coordinates on the page where the item should be printed.
The majority of these items result in text being printed on the page,
and these items may have individual font and alignments specified. For
example, the numerical amount of a check could be printed right
justified while everything else is printed left justified. Other types
may have unique parameters.

.. table:: Individual Check Item Types

   +----------------+----------------+----------------+----------------+
   | Name           | Required       | Optional       | Description    |
   |                | Fields         | Fields         |                |
   +================+================+================+================+
   | PAYEE          | Coords         | Font Align     | This type      |
   |                |                | Blocking_Chars | value tells    |
   |                |                |                | GnuCash to     |
   |                |                |                | print the      |
   |                |                |                | check payee    |
   |                |                |                | name at the    |
   |                |                |                | specified      |
   |                |                |                | coordinates.   |
   +----------------+----------------+----------------+----------------+
   | DATE           | Coords         | Font Align     | This type      |
   |                |                | Blocking_Chars | value tells    |
   |                |                | DateFormat     | GnuCash to     |
   |                |                |                | print the      |
   |                |                |                | check date at  |
   |                |                |                | the specified  |
   |                |                |                | coordinates.   |
   +----------------+----------------+----------------+----------------+
   | NOTES          | Coords         | Font Align     | This type      |
   |                |                | Blocking_Chars | value tells    |
   |                |                |                | GnuCash to     |
   |                |                |                | print the      |
   |                |                |                | transaction    |
   |                |                |                | notes field at |
   |                |                |                | the specified  |
   |                |                |                | coordinates.   |
   +----------------+----------------+----------------+----------------+
   | CHECK_NUMBER   | Coords         | Font Align     | This type      |
   |                |                | Blocking_Chars | value tells    |
   |                |                |                | GnuCash to     |
   |                |                |                | print the      |
   |                |                |                | check number   |
   |                |                |                | at the         |
   |                |                |                | specified      |
   |                |                |                | coordinates.   |
   |                |                |                | The check      |
   |                |                |                | number         |
   |                |                |                | reflects the   |
   |                |                |                | book option    |
   |                |                |                | selection      |
   |                |                |                | under File >   |
   |                |                |                | Properties for |
   |                |                |                | number source  |
   |                |                |                | (transaction   |
   |                |                |                | number or      |
   |                |                |                | anchor-split   |
   |                |                |                | action - see   |
   |                |                |                | `Use Split     |
   |                |                |                | Action Field   |
   |                |                |                | for            |
   |                |                |                | Number <ghe    |
   |                |                |                | lp:gnucash-hel |
   |                |                |                | p?num-action-b |
   |                |                |                | ook-option>`__ |
   |                |                |                | in the Book    |
   |                |                |                | Options        |
   |                |                |                | section of the |
   |                |                |                | GnuCash Help   |
   |                |                |                | Manual).       |
   +----------------+----------------+----------------+----------------+
   | MEMO           | Coords         | Font Align     | This type      |
   |                |                | Blocking_Chars | value tells    |
   |                |                |                | GnuCash to     |
   |                |                |                | print the      |
   |                |                |                | split memo     |
   |                |                |                | field at the   |
   |                |                |                | specified      |
   |                |                |                | coordinates.   |
   +----------------+----------------+----------------+----------------+
   | ACTION         | Coords         | Font Align     | This type      |
   |                |                | Blocking_Chars | value tells    |
   |                |                |                | GnuCash to     |
   |                |                |                | print the      |
   |                |                |                | split action   |
   |                |                |                | field at the   |
   |                |                |                | specified      |
   |                |                |                | coordinates.   |
   |                |                |                | However, the   |
   |                |                |                | printed field  |
   |                |                |                | reflects the   |
   |                |                |                | book option    |
   |                |                |                | selection      |
   |                |                |                | under File >   |
   |                |                |                | Properties for |
   |                |                |                | number source  |
   |                |                |                | (transaction   |
   |                |                |                | number or      |
   |                |                |                | anchor-split   |
   |                |                |                | action - see   |
   |                |                |                | `Use Split     |
   |                |                |                | Action Field   |
   |                |                |                | for            |
   |                |                |                | Number <ghe    |
   |                |                |                | lp:gnucash-hel |
   |                |                |                | p?num-action-b |
   |                |                |                | ook-option>`__ |
   |                |                |                | in the Book    |
   |                |                |                | Options        |
   |                |                |                | section of the |
   |                |                |                | GnuCash Help   |
   |                |                |                | Manual). If    |
   |                |                |                | number source  |
   |                |                |                | for the book   |
   |                |                |                | is specified   |
   |                |                |                | as             |
   |                |                |                | anchor-split   |
   |                |                |                | action, this   |
   |                |                |                | field will     |
   |                |                |                | instead print  |
   |                |                |                | the            |
   |                |                |                | transaction    |
   |                |                |                | number field.  |
   +----------------+----------------+----------------+----------------+
   | AMOUNT_WORDS   | Coords         | Font Align     | This type      |
   |                |                | Blocking_Chars | value tells    |
   |                |                |                | GnuCash to     |
   |                |                |                | print the      |
   |                |                |                | check amount   |
   |                |                |                | in words at    |
   |                |                |                | the specified  |
   |                |                |                | coordinates.   |
   |                |                |                | The amount     |
   |                |                |                | will appear    |
   |                |                |                | similar to the |
   |                |                |                | string "One    |
   |                |                |                | thousand, two  |
   |                |                |                | hundred thirty |
   |                |                |                | four and       |
   |                |                |                | 56/100".       |
   +----------------+----------------+----------------+----------------+
   | AMOUNT_NUMBER  | Coords         | Font Align     | This type      |
   |                |                | Blocking_Chars | value tells    |
   |                |                |                | GnuCash to     |
   |                |                |                | print the      |
   |                |                |                | check amount   |
   |                |                |                | in numbers at  |
   |                |                |                | the specified  |
   |                |                |                | coordinates.   |
   |                |                |                | The amount     |
   |                |                |                | will appear    |
   |                |                |                | similar to the |
   |                |                |                | number         |
   |                |                |                | "$1,234.56".   |
   +----------------+----------------+----------------+----------------+
   | ADDRESS        | Coords         | Font Align     | This type      |
   |                |                | Blocking_Chars | value tells    |
   |                |                |                | GnuCash to     |
   |                |                |                | print the      |
   |                |                |                | address at the |
   |                |                |                | specified      |
   |                |                |                | coordinates.   |
   +----------------+----------------+----------------+----------------+
   | SPLITS_ACCOUNT | Coords         | Font Align     | This type      |
   |                |                | Blocking_Chars | value tells    |
   |                |                |                | GnuCash to     |
   |                |                |                | print the      |
   |                |                |                | account names  |
   |                |                |                | for each split |
   |                |                |                | entry stating  |
   |                |                |                | at the         |
   |                |                |                | specified      |
   |                |                |                | coordinates.   |
   |                |                |                | See the note   |
   |                |                |                | on splits      |
   |                |                |                | printing.      |
   +----------------+----------------+----------------+----------------+
   | SPLITS_AMOUNT  | Coords         | Font Align     | This type      |
   |                |                | Blocking_Chars | value tells    |
   |                |                |                | GnuCash to     |
   |                |                |                | print the      |
   |                |                |                | amount for     |
   |                |                |                | each split     |
   |                |                |                | entry stating  |
   |                |                |                | at the         |
   |                |                |                | specified      |
   |                |                |                | coordinates.   |
   |                |                |                | Amounts are    |
   |                |                |                | printed with   |
   |                |                |                | currency       |
   |                |                |                | symbols. See   |
   |                |                |                | the note on    |
   |                |                |                | splits         |
   |                |                |                | printing.      |
   +----------------+----------------+----------------+----------------+
   | SPLITS_MEMO    | Coords         | Font Align     | This type      |
   |                |                | Blocking_Chars | value tells    |
   |                |                |                | GnuCash to     |
   |                |                |                | print the memo |
   |                |                |                | text for each  |
   |                |                |                | split entry    |
   |                |                |                | stating at the |
   |                |                |                | specified      |
   |                |                |                | coordinates.   |
   |                |                |                | See the note   |
   |                |                |                | on splits      |
   |                |                |                | printing.      |
   +----------------+----------------+----------------+----------------+
   | TEXT           | Coords, Text   | Font Align     | This type      |
   |                |                | Blocking_Chars | value tells    |
   |                |                |                | GnuCash to     |
   |                |                |                | print an       |
   |                |                |                | arbitrary      |
   |                |                |                | string at the  |
   |                |                |                | specified      |
   |                |                |                | coordinates.   |
   |                |                |                | The string to  |
   |                |                |                | be printed is  |
   |                |                |                | specified with |
   |                |                |                | the *Text_n*   |
   |                |                |                | key.           |
   +----------------+----------------+----------------+----------------+
   | PICTURE        | Coords,        | (none)         | This type      |
   |                | Filename       |                | value tells    |
   |                |                |                | GnuCash to     |
   |                |                |                | print an image |
   |                |                |                | at the         |
   |                |                |                | specified      |
   |                |                |                | coordinates.   |
   |                |                |                | The image to   |
   |                |                |                | be printed is  |
   |                |                |                | specified with |
   |                |                |                | the            |
   |                |                |                | *Filename_n*   |
   |                |                |                | key. This type |
   |                |                |                | is only        |
   |                |                |                | recognized     |
   |                |                |                | when using gtk |
   |                |                |                | version 2.10   |
   |                |                |                | or later.      |
   +----------------+----------------+----------------+----------------+

.. note::

   SPLIT items include all split entries for the transaction except for
   the split that applies to the current account register (referred to
   as the anchor-split). This is usually the last split listed when
   splits are displayed in the register. The coordinate location defines
   the lower left location for the split information.

.. _check_format_notes:

Creating Check Format Files
---------------------------

Creating your own check format file is a fairly simple task. The easiest
way to start is to copy an existing check format file from the
application directory (typically ``/usr/share/gnucash/checks``) to the
directory ``~/.local/share/gnucash/checks``. Make sure to change the
guid so the new file will be accepted by gnucash, and change the title
to something descriptive. Then change or add individual item fields as
necessary. You can also create a new check file by clicking the Save
Format button on the Custom format page of the check printing dialog.

.. note::

   Key names are case sensitive. If you are having problems with a check
   format file, ensure that all key names have capital letters as
   documented above.

.. [1]
   Up to GnuCash 2.6.21 it was ``~/.gnucash/checks``

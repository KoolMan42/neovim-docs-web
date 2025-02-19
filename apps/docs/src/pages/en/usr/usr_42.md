---
title: Tree Sitter
description: Some page
layout: "@layouts/MainLayout.astro"
---


## <a id="" class="section-title" href="#">*Usr_42.Txt*	Nvim</a> 

VIM USER MANUAL - by Bram Moolenaar

Add new menus


By now you know that Vim is very flexible.  This includes the menus used in
the GUI.  You can define your own menu entries to make certain commands easily
accessible.  This is for mouse-happy users only.

[42.1](#42.1)	Introduction
[42.2](#42.2)	Menu commands
[42.3](#42.3)	Various
[42.4](#42.4)	Toolbar and popup menus

Next chapter: [usr_43.txt](#usr_43.txt)  Using filetypes
Previous chapter: [usr_41.txt](#usr_41.txt)  Write a Vim script
Table of contents: [usr_toc.txt](#usr_toc.txt)


## <a id="" class="section-title" href="#">*42.1*	Introduction</a> 

The menus that Vim uses are defined in the file "$VIMRUNTIME/menu.vim".  If
you want to write your own menus, you might first want to look through that
file.
To define a menu item, use the ":menu" command.  The basic form of this
command is as follows:
```

:menu {menu-item} {keys}

The {menu-item} describes where on the menu to put the item.  A typical
{menu-item} is "File.Save", which represents the item "Save" under the
"File" menu.  A dot is used to separate the names.  Example:
```

:menu File.Save  :update<CR>

The ":update" command writes the file when it was modified.
You can add another level: "Edit.Settings.Shiftwidth" defines a submenu
"Settings" under the "Edit" menu, with an item "Shiftwidth".  You could use
even deeper levels.  Don't use this too much, you need to move the mouse quite
a bit to use such an item.
The ":menu" command is very similar to the ":map" command: the left side
specifies how the item is triggered and the right hand side defines the
characters that are executed.  {keys} are characters, they are used just like
you would have typed them.  Thus in Insert mode, when {keys} is plain text,
that text is inserted.


ACCELERATORS

The ampersand character (&) is used to indicate an accelerator.  For instance,
you can use Alt-F to select "File" and S to select "Save".  (The 'winaltkeys'
option may disable this though!).  Therefore, the {menu-item} looks like
"&File.&Save".  The accelerator characters will be underlined in the menu.
You must take care that each key is used only once in each menu.  Otherwise
you will not know which of the two will actually be used.  Vim doesn't warn
you for this.


PRIORITIES

The actual definition of the File.Save menu item is as follows:
```

:menu 10.340 &File.&Save<Tab>:w  :confirm w<CR>

The number 10.340 is called the priority number.  It is used by the editor to
decide where it places the menu item.  The first number (10) indicates the
position on the menu bar.  Lower numbered menus are positioned to the left,
higher numbers to the right.
These are the priorities used for the standard menus:

10	20     40     50      60       70		9999

+------------------------------------------------------------+
[ File	Edit  Tools  Syntax  Buffers  Window		Help ](# File	Edit  Tools  Syntax  Buffers  Window		Help )
+------------------------------------------------------------+

Notice that the Help menu is given a very high number, to make it appear on
the far right.
The second number (340) determines the location of the item within the
pull-down menu.  Lower numbers go on top, higher number on the bottom.  These
are the priorities in the File menu:

+-----------------+
10.310	[Open...	  ](#Open...	  )
10.320	[Split-Open...	  ](#Split-Open...	  )
10.325	[New		  ](#New		  )
10.330	[Close		  ](#Close		  )
10.335	[---------------- ](#---------------- )
10.340	[Save		  ](#Save		  )
10.350	[Save As...	  ](#Save As...	  )
10.400	[---------------- ](#---------------- )
10.410	[Split Diff with  ](#Split Diff with  )
10.420	[Split Patched By ](#Split Patched By )
10.500	[---------------- ](#---------------- )
10.510	[Print		  ](#Print		  )
10.600	[---------------- ](#---------------- )
10.610	[Save-Exit	  ](#Save-Exit	  )
10.620	[Exit		  ](#Exit		  )
+-----------------+

Notice that there is room in between the numbers.  This is where you can
insert your own items, if you really want to (it's often better to leave the
standard menus alone and add a new menu for your own items).
When you create a submenu, you can add another ".number" to the priority.
Thus each name in {menu-item} has its priority number.


SPECIAL CHARACTERS

The {menu-item} in this example is "&File.&Save<Tab>:w".  This brings up an
important point: {menu-item} must be one word.  If you want to put a dot,
space or tabs in the name, you either use the <> notation (<Space> and <Tab>,
for instance) or use the backslash (\) escape.
```

:menu 10.305 &File.&Do\ It\.\.\. :exit<CR>

In this example, the name of the menu item "Do It..." contains a space and the
command is ":exit<CR>".

The <Tab> character in a menu name is used to separate the part that defines
the menu name from the part that gives a hint to the user.  The part after the

```
Tab> is displayed right aligned in the menu.  In the File.Save menu the name
used is "&File.&Save<Tab>:w".  Thus the menu name is "File.Save" and the hint
is ":w".


SEPARATORS

The separator lines, used to group related menu items together, can be defined
by using a name that starts and ends in a '-'.  For example "-sep-".  When
using several separators the names must be different.  Otherwise the names
don't matter.
The command from a separator will never be executed, but you have to define
one anyway.  A single colon will do.  Example:
```

:amenu 20.510 Edit.-sep3- :


## <a id="" class="section-title" href="#">*42.2*	Menu Commands</a> 

You can define menu items that exist for only certain modes.  This works just
like the variations on the ":map" command:

:menu		Normal, Visual and Operator-pending mode
:nmenu		Normal mode
:vmenu		Visual mode
:omenu		Operator-pending mode
:menu!		Insert and Command-line mode
:imenu		Insert mode
:cmenu		Command-line mode
:tlmenu		Terminal mode
:amenu		All modes (except for Terminal mode)

To avoid that the commands of a menu item are being mapped, use the command
":noremenu", ":nnoremenu", ":anoremenu", etc.


USING :AMENU

The ":amenu" command is a bit different.  It assumes that the {keys} you
give are to be executed in Normal mode.  When Vim is in Visual or Insert mode
when the menu is used, Vim first has to go back to Normal mode.  ":amenu"
inserts a CTRL-C or CTRL-O for you.  For example, if you use this command:
```
:amenu  90.100 Mine.Find\ Word  *

Then the resulting menu commands will be:

### <a id="" class="section-title" href="#">	Normal mode:</a>
### <a id="CTRL-C " class="section-title" href="#CTRL-C ">	Visual mode:</a>
Operator-pending mode:	CTRL-C *
### <a id="CTRL-O " class="section-title" href="#CTRL-O ">	Insert mode:</a>
Command-line mode:	CTRL-C *

When in Command-line mode the CTRL-C will abandon the command typed so far.
In Visual and Operator-pending mode CTRL-C will stop the mode.  The CTRL-O in
Insert mode will execute the command and then return to Insert mode.
CTRL-O only works for one command.  If you need to use two or more
commands, put them in a function and call that function.  Example:
```

:amenu  Mine.Next\ File  :call <SID>NextFile()<CR>
:function <SID>NextFile()
:  next
:  1/^Code
:endfunction

This menu entry goes to the next file in the argument list with ":next".  Then
it searches for the line that starts with "Code".
The <SID> before the function name is the script ID.  This makes the
function local to the current Vim script file.  This avoids problems when a
function with the same name is defined in another script file.  See [<SID>](#<SID>).


SILENT MENUS

The menu executes the {keys} as if you typed them.  For a ":" command this
means you will see the command being echoed on the command line.  If it's a
long command, the hit-Enter prompt will appear.  That can be very annoying!
To avoid this, make the menu silent.  This is done with the <silent>
argument.  For example, take the call to NextFile() in the previous example.
When you use this menu, you will see this on the command line:

:call <SNR>34_NextFile() ~

To avoid this text on the command line, insert "<silent>" as the first
argument:
```

:amenu <silent> Mine.Next\ File :call <SID>NextFile()<CR>

Don't use "<silent>" too often.  It is not needed for short commands.  If you
make a menu for someone else, being able to see the executed command will
give them a hint about what they could have typed, instead of using the mouse.


LISTING MENUS

When a menu command is used without a {keys} part, it lists the already
defined menus.  You can specify a {menu-item}, or part of it, to list specific
menus.  Example:
```

:amenu

This lists all menus.  That's a long list!  Better specify the name of a menu
to get a shorter list:
```

:amenu Edit

This lists only the "Edit" menu items for all modes.  To list only one
specific menu item for Insert mode:
```

:imenu Edit.Undo

Take care that you type exactly the right name.  Case matters here.  But the
'&' for accelerators can be omitted.  The <Tab> and what comes after it can be
left out as well.


DELETING MENUS

To delete a menu, the same command is used as for listing, but with "menu"
changed to "unmenu".  Thus ":menu" becomes, ":unmenu", ":nmenu" becomes
":nunmenu", etc.  To delete the "Tools.Make" item for Insert mode:
```

:iunmenu Tools.Make

You can delete a whole menu, with all its items, by using the menu name.
Example:
```

:aunmenu Syntax

This deletes the Syntax menu and all the items in it.


## <a id="" class="section-title" href="#">*42.3*	Various</a> 

You can change the appearance of the menus with flags in 'guioptions'.  In the
default value they are all included, except "M".  You can remove a flag with a
command like:
```

:set guioptions-=m

```

m		When removed the menubar is not displayed.

M		When added the default menus are not loaded.

g		When removed the inactive menu items are not made grey
but are completely removed.  (Does not work on all
systems.)

For translating menu items, see [:menutrans](#:menutrans).

Since the mouse has to be used to select a menu item, it is a good idea to use
the ":browse" command for selecting a file.  And ":confirm" to get a dialog
instead of an error message, e.g., when the current buffer contains changes.
These two can be combined:
```

:amenu File.Open  :browse confirm edit<CR>

The ":browse" makes a file browser appear to select the file to edit.  The
":confirm" will pop up a dialog when the current buffer has changes.  You can
then select to save the changes, throw them away or cancel the command.
For more complicated items, the confirm() and inputdialog() functions can
be used.  The default menus contain a few examples.


## <a id="" class="section-title" href="#">*42.4*	Toolbar and Popup Menus</a> 

There are two special menus: ToolBar and PopUp.  Items that start with these
names do not appear in the normal menu bar.


TOOLBAR

The toolbar appears only when the "T" flag is included in the 'guioptions'
option.
The toolbar uses icons rather than text to represent the command.  For
example, the {menu-item} named "ToolBar.New" causes the "New" icon to appear
on the toolbar.
The Vim editor has 28 built-in icons.  You can find a table here:
[builtin-tools](#builtin-tools).  Most of them are used in the default toolbar.  You can
redefine what these items do (after the default menus are setup).
You can add another bitmap for a toolbar item.  Or define a new toolbar
item with a bitmap.  For example, define a new toolbar item with:
```

:tmenu ToolBar.Compile  Compile the current file
:amenu ToolBar.Compile  :!cc %:S -o %:r:S<CR>

Now you need to create the icon.  For MS-Windows it must be in bitmap format,
with the name "Compile.bmp".  For Unix XPM format is used, the file name is
"Compile.xpm".  The size must be 18 by 18 pixels.  On MS-Windows other sizes
can be used as well, but it will look ugly.
Put the bitmap in the directory "bitmaps" in one of the directories from
'runtimepath'.  E.g., for Unix "~/.config/nvim/bitmaps/Compile.xpm".

You can define tooltips for the items in the toolbar.  A tooltip is a short
text that explains what a toolbar item will do.  For example "Open file".  It
appears when the mouse pointer is on the item, without moving for a moment.
This is very useful if the meaning of the picture isn't that obvious.
Example:
```

:tmenu ToolBar.Make  Run make in the current directory

```

Note:
Pay attention to the case used.  "Toolbar" and "toolbar" are different
from "ToolBar"!

To remove a tooltip, use the [:tunmenu](#:tunmenu) command.

The 'toolbar' option can be used to display text instead of a bitmap, or both
text and a bitmap.  Most people use just the bitmap, since the text takes
quite a bit of space.


POPUP MENU

The popup menu pops up where the mouse pointer is.  On MS-Windows you activate
it by clicking the right mouse button.  Then you can select an item with the
left mouse button.  On Unix the popup menu is used by pressing and holding the
right mouse button.
The popup menu only appears when the 'mousemodel' has been set to "popup"
or "popup_setpos".  The difference between the two is that "popup_setpos"
moves the cursor to the mouse pointer position.  When clicking inside a
selection, the selection will be used unmodified.  When there is a selection
but you click outside of it, the selection is removed.
There is a separate popup menu for each mode.  Thus there are never grey
items like in the normal menus.

### <a id="42" class="section-title" href="#42">What is the meaning of life, the universe and everything?</a>
Douglas Adams, the only person who knew what this question really was about is
now dead, unfortunately.  So now you might wonder what the meaning of death
is...


## <a id="Using filetypes" class="section-title" href="#Using filetypes">Next Chapter: |Usr_43.Txt|</a> 

Copyright: see [manual-copyright](#manual-copyright)  vim:tw=78:ts=8:noet:ft=help:norl:


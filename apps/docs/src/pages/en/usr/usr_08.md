---
title: Tree Sitter
description: Some page
layout: "@layouts/MainLayout.astro"
---


## <a id="" class="section-title" href="#">*Usr_08.Txt*	Nvim</a> 

VIM USER MANUAL - by Bram Moolenaar

Splitting windows


Display two different files above each other.  Or view two locations in the
file at the same time.  See the difference between two files by putting them
side by side.  All this is possible with split windows.

[08.1](#08.1)	Split a window
[08.2](#08.2)	Split a window on another file
[08.3](#08.3)	Window size
[08.4](#08.4)	Vertical splits
[08.5](#08.5)	Moving windows
[08.6](#08.6)	Commands for all windows
[08.7](#08.7)	Viewing differences with diff mode
[08.8](#08.8)	Various
[08.9](#08.9)	Tab pages

Next chapter: [usr_09.txt](#usr_09.txt)  Using the GUI
Previous chapter: [usr_07.txt](#usr_07.txt)  Editing more than one file
Table of contents: [usr_toc.txt](#usr_toc.txt)


## <a id="" class="section-title" href="#">*08.1*	Split a Window</a> 

The easiest way to open a new window is to use the following command:
```

:split

This command splits the screen into two windows and leaves the cursor in the
top one:

+----------------------------------+
[/* file one.c */		   ](#/* file one.c */		   )
[~				   ](#~				   )
[~				   ](#~				   )
[one.c=============================](#one.c=============================)
[/* file one.c */		   ](#/* file one.c */		   )
[~				   ](#~				   )
[one.c=============================](#one.c=============================)
[				   ](#				   )
+----------------------------------+

What you see here is two windows on the same file.  The line with "====" is
the status line.  It displays information about the window above it.  (In
practice the status line will be in reverse video.)
The two windows allow you to view two parts of the same file.  For example,
you could make the top window show the variable declarations of a program, and
the bottom one the code that uses these variables.

The CTRL-W w command can be used to jump between the windows.  If you are in
the top window, CTRL-W w jumps to the window below it.  If you are in the
bottom window it will jump to the first window.  (CTRL-W CTRL-W does the same
thing, in case you let go of the CTRL key a bit later.)


CLOSE THE WINDOW

To close a window, use the command:
```

:close

Actually, any command that quits editing a file works, like ":quit" and "ZZ".
But ":close" prevents you from accidentally exiting Vim when you close the
last window.


CLOSING ALL OTHER WINDOWS

If you have opened a whole bunch of windows, but now want to concentrate on
one of them, this command will be useful:
```

:only

This closes all windows, except for the current one.  If any of the other
windows has changes, you will get an error message and that window won't be
closed.


## <a id="" class="section-title" href="#">*08.2*	Split a Window on Another File</a> 

The following command opens a second window and starts editing the given file:
```
:split two.c

If you were editing one.c, then the result looks like this:

+----------------------------------+
[/* file two.c */		   ](#/* file two.c */		   )
[~				   ](#~				   )
[~				   ](#~				   )
[two.c=============================](#two.c=============================)
[/* file one.c */		   ](#/* file one.c */		   )
[~				   ](#~				   )
[one.c=============================](#one.c=============================)
[				   ](#				   )
+----------------------------------+

To open a window on a new, empty file, use this:
```

:new

You can repeat the ":split" and ":new" commands to create as many windows as
you like.


## <a id="" class="section-title" href="#">*08.3*	Window Size</a> 

The ":split" command can take a number argument.  If specified, this will be
the height of the new window.  For example, the following opens a new window
three lines high and starts editing the file alpha.c:
```

:3split alpha.c

For existing windows you can change the size in several ways.  When you have a
working mouse, it is easy: Move the mouse pointer to the status line that
separates two windows, and drag it up or down.

To increase the size of a window:
```

CTRL-W +

To decrease it:
```

CTRL-W -

Both of these commands take a count and increase or decrease the window size
by that many lines.  Thus "4 CTRL-W +" make the window four lines higher.

To set the window height to a specified number of lines:
```

{height}CTRL-W _

That's: a number {height}, CTRL-W and then an underscore (the - key with Shift
on English-US keyboards).
To make a window as high as it can be, use the CTRL-W _ command without a
count.


USING THE MOUSE

In Vim you can do many things very quickly from the keyboard.  Unfortunately,
the window resizing commands require quite a bit of typing.  In this case,
using the mouse is faster.  Position the mouse pointer on a status line.  Now
press the left mouse button and drag.  The status line will move, thus making
the window on one side higher and the other smaller.


OPTIONS

The 'winheight' option can be set to a minimal desired height of a window and
'winminheight' to a hard minimum height.
Likewise, there is 'winwidth' for the minimal desired width and
'winminwidth' for the hard minimum width.
The 'equalalways' option, when set, makes Vim equalize the windows sizes
when a window is closed or opened.


## <a id="" class="section-title" href="#">*08.4*	Vertical Splits</a> 

The ":split" command creates the new window above the current one.  To make
the window appear at the left side, use:
```

:vsplit

or:
```
:vsplit two.c

The result looks something like this:

+--------------------------------------+
### <a id="[/ file one.c /" class="section-title" href="#|/ file one.c /">	](#/ file one.c /" class="section-title" href="#|/ file one.c /">	)/* file two.c */</a>
[~		    |~		       ](#~		    |~		       )
[~		    |~		       ](#~		    |~		       )
[~		    |~		       ](#~		    |~		       )
[two.c===============one.c=============](#two.c===============one.c=============)
[				       ](#				       )
+--------------------------------------+

Actually, the | lines in the middle will be in reverse video.  This is called
the vertical separator.  It separates the two windows left and right of it.

There is also the ":vnew" command, to open a vertically split window on a new,
empty file.  Another way to do this:
```

:vertical new

The ":vertical" command can be inserted before another command that splits a
window.  This will cause that command to split the window vertically instead
of horizontally.  (If the command doesn't split a window, it works
unmodified.)


MOVING BETWEEN WINDOWS

Since you can split windows horizontally and vertically as much as you like,
you can create almost any layout of windows.  Then you can use these commands
to move between them:

CTRL-W h	move to the window on the left
CTRL-W j	move to the window below
CTRL-W k	move to the window above
CTRL-W l	move to the window on the right

CTRL-W t	move to the TOP window
CTRL-W b	move to the BOTTOM window

You will notice the same letters as used for moving the cursor.  And the
cursor keys can also be used, if you like.
More commands to move to other windows: [Q_wi](#Q_wi).


## <a id="" class="section-title" href="#">*08.5*	Moving Windows</a> 

You have split a few windows, but now they are in the wrong place.  Then you
need a command to move the window somewhere else.  For example, you have three
windows like this:

+----------------------------------+
[/* file two.c */		   ](#/* file two.c */		   )
[~				   ](#~				   )
[~				   ](#~				   )
[two.c=============================](#two.c=============================)
[/* file three.c */		   ](#/* file three.c */		   )
[~				   ](#~				   )
[~				   ](#~				   )
[three.c===========================](#three.c===========================)
[/* file one.c */		   ](#/* file one.c */		   )
[~				   ](#~				   )
[one.c=============================](#one.c=============================)
[				   ](#				   )
+----------------------------------+

Clearly the last one should be at the top.  Go to that window (using CTRL-W w)
and then type this command:
```

CTRL-W K

This uses the uppercase letter K.  What happens is that the window is moved to
the very top.  You will notice that K is again used for moving upwards.
When you have vertical splits, CTRL-W K will move the current window to the
top and make it occupy the full width of the Vim window.  If this is your
layout:

+-------------------------------------------+
### <a id="[/ three.c /" class="section-title" href="#|/ three.c /">	](#/ three.c /" class="section-title" href="#|/ three.c /">	)/* two.c */</a>
[~	      |~	      |~	    ](#~	      |~	      |~	    )
[~	      |~	      |~	    ](#~	      |~	      |~	    )
[~	      |~	      |~	    ](#~	      |~	      |~	    )
[~	      |~	      |~	    ](#~	      |~	      |~	    )
[~	      |~	      |~	    ](#~	      |~	      |~	    )
[two.c=========three.c=========one.c========](#two.c=========three.c=========one.c========)
[					    ](#					    )
+-------------------------------------------+

Then using CTRL-W K in the middle window (three.c) will result in:

+-------------------------------------------+
[/* three.c */				    ](#/* three.c */				    )
[~					    ](#~					    )
[~					    ](#~					    )
[three.c====================================](#three.c====================================)
### <a id="[/ one.c /" class="section-title" href="#|/ one.c /">	](#/ one.c /" class="section-title" href="#|/ one.c /">	)/* two.c */</a>
[~		       |~		    ](#~		       |~		    )
[two.c==================one.c===============](#two.c==================one.c===============)
[					    ](#					    )
+-------------------------------------------+

The other three similar commands (you can probably guess these now):

CTRL-W H	move window to the far left
CTRL-W J	move window to the bottom
CTRL-W L	move window to the far right


## <a id="" class="section-title" href="#">*08.6*	Commands for All Windows</a> 

When you have several windows open and you want to quit Vim, you can close
each window separately.  A quicker way is using this command:
```

:qall

This stands for "quit all".  If any of the windows contain changes, Vim will
not exit.  The cursor will automatically be positioned in a window with
changes.  You can then either use ":write" to save the changes, or ":quit!" to
throw them away.

If you know there are windows with changes, and you want to save all these
changes, use this command:
```

:wall

This stands for "write all".  But actually, it only writes files with
changes.  Vim knows it doesn't make sense to write files that were not
changed.
And then there is the combination of ":qall" and ":wall": the "write and
quit all" command:
```

:wqall

This writes all modified files and quits Vim.
Finally, there is a command that quits Vim and throws away all changes:
```

:qall!

Be careful, there is no way to undo this command!


OPENING A WINDOW FOR ALL ARGUMENTS

To make Vim open a window for each file, start it with the "-o" argument:
```

vim -o one.txt two.txt three.txt

This results in:

+-------------------------------+
[file one.txt			](#file one.txt			)
[~				](#~				)
[one.txt========================](#one.txt========================)
[file two.txt			](#file two.txt			)
[~				](#~				)
[two.txt========================](#two.txt========================)
[file three.txt			](#file three.txt			)
[~				](#~				)
[three.txt======================](#three.txt======================)
[				](#				)
+-------------------------------+

The "-O" argument is used to get vertically split windows.
When Vim is already running, the ":all" command opens a window for each
file in the argument list.  ":vertical all" does it with vertical splits.


## <a id="" class="section-title" href="#">*08.7*	Viewing Differences With Diff Mode</a> 

There is a special way to start Nvim, which shows the differences between two
files.  Let's take a file "main.c" and insert a few characters in one line.
Write this file with the 'backup' option set, so that the backup file
"main.c~" will contain the previous version of the file.
Type this command in a shell to start Nvim in diff mode:
```

nvim -d main.c~ main.c

Vim will start, with two windows side by side.  You will only see the line
in which you added characters, and a few lines above and below it.

VV		      VV
+-----------------------------------------+
[+ +--123 lines: /* a|+ +--123 lines: /* a](#+ +--123 lines: /* a|+ +--123 lines: /* a)  <- fold
[  text		     |	text		  ](#  text		     |	text		  )
[  text		     |	text		  ](#  text		     |	text		  )
[  text		     |	text		  ](#  text		     |	text		  )
[  text		     |	changed text	  ](#  text		     |	changed text	  )  <- changed line
[  text		     |	text		  ](#  text		     |	text		  )
[  text		     |	------------------](#  text		     |	------------------)  <- deleted line
[  text		     |	text		  ](#  text		     |	text		  )
[  text		     |	text		  ](#  text		     |	text		  )
[  text		     |	text		  ](#  text		     |	text		  )
[+ +--432 lines: text|+ +--432 lines: text](#+ +--432 lines: text|+ +--432 lines: text)  <- fold
[  ~		     |	~		  ](#  ~		     |	~		  )
[  ~		     |	~		  ](#  ~		     |	~		  )
[main.c~==============main.c==============](#main.c~==============main.c==============)
[					  ](#					  )
+-----------------------------------------+

(This picture doesn't show the highlighting, use "nvim -d" for that.)

The lines that were not modified have been collapsed into one line.  This is
called a closed fold.  They are indicated in the picture with "<- fold".  Thus
the single fold line at the top stands for 123 text lines.  These lines are
equal in both files.
The line marked with "<- changed line" is highlighted, and the inserted
text is displayed with another color.  This clearly shows what the difference
is between the two files.
The line that was deleted is displayed with "---" in the main.c window.
See the "<- deleted line" marker in the picture.  These characters are not
really there.  They just fill up main.c, so that it displays the same number
of lines as the other window.


THE FOLD COLUMN

Each window has a column on the left with a slightly different background.  In
the picture above these are indicated with "VV".  You notice there is a plus
character there, in front of each closed fold.  Move the mouse pointer to that
plus and click the left button.  The fold will open, and you can see the text
that it contains.
The fold column contains a minus sign for an open fold.  If you click on
this -, the fold will close.
Obviously, this only works when you have a working mouse.  You can also use
"zo" to open a fold and "zc" to close it.


DIFFING IN VIM

Another way to start in diff mode can be done from inside Vim.  Edit the
"main.c" file, then make a split and show the differences:
```

:edit main.c
:vertical diffsplit main.c~

The ":vertical" command is used to make the window split vertically.  If you
omit this, you will get a horizontal split.

If you have a patch or diff file, you can use the third way to start diff
mode.  First edit the file to which the patch applies.  Then tell Vim the name
of the patch file:
```

:edit main.c
:vertical diffpatch main.c.diff

WARNING: The patch file must contain only one patch, for the file you are
editing.  Otherwise you will get a lot of error messages, and some files might
be patched unexpectedly.
The patching will only be done to the copy of the file in Vim.  The file on
your harddisk will remain unmodified (until you decide to write the file).


SCROLL BINDING

When the files have more changes, you can scroll in the usual way.  Vim will
try to keep both the windows start at the same position, so you can easily see
the differences side by side.
When you don't want this for a moment, use this command:
```

:set noscrollbind


JUMPING TO CHANGES

When you have disabled folding in some way, it may be difficult to find the
changes.  Use this command to jump forward to the next change:
```

]c

To go the other way use:
```

[c

Prepended a count to jump further away.


REMOVING CHANGES

You can move text from one window to the other.  This either removes
differences or adds new ones.  Vim doesn't keep the highlighting updated in
all situations.  To update it use this command:
```

:diffupdate

To remove a difference, you can move the text in a highlighted block from one
window to another.  Take the "main.c" and "main.c~" example above.  Move the
cursor to the left window, on the line that was deleted in the other window.
Now type this command:
```

dp

The change will be removed by putting the text of the current window in the
other window.  "dp" stands for "diff put".
You can also do it the other way around.  Move the cursor to the right
window, to the line where "changed" was inserted.  Now type this command:
```

do

The change will now be removed by getting the text from the other window.
Since there are no changes left now, Vim puts all text in a closed fold.
"do" stands for "diff obtain".  "dg" would have been better, but that already
has a different meaning ("dgg" deletes from the cursor until the first line).

For details about diff mode, see [diff-mode](#diff-mode).


## <a id="" class="section-title" href="#">*08.8*	Various</a> 

The 'laststatus' option can be used to specify when the last window has a
statusline:

0	never
1	only when there are split windows (the default)
2	always
3	have a global statusline at the bottom instead of one for each
window

Many commands that edit another file have a variant that splits the window.
For Command-line commands this is done by prepending an "s".  For example:
":tag" jumps to a tag, ":stag" splits the window and jumps to a
tag.
For Normal mode commands a CTRL-W is prepended.  CTRL-^ jumps to the
alternate file, CTRL-W CTRL-^ splits the window and edits the alternate file.

The 'splitbelow' option can be set to make a new window appear below the
current window.  The 'splitright' option can be set to make a vertically split
window appear right of the current window.

When splitting a window you can prepend a modifier command to tell where the
window is to appear:

:leftabove {cmd}	left or above the current window
:aboveleft {cmd}	idem
:rightbelow {cmd}	right or below the current window
:belowright {cmd}	idem
:topleft {cmd}		at the top or left of the Vim window
:botright {cmd}		at the bottom or right of the Vim window


## <a id="" class="section-title" href="#">*08.9*	Tab Pages</a> 

You will have noticed that windows never overlap.  That means you quickly run
out of screen space.  The solution for this is called Tab pages.

Assume you are editing "thisfile".  To create a new tab page use this command:
```

:tabedit thatfile

This will edit the file "thatfile" in a window that occupies the whole Vim
window.  And you will notice a bar at the top with the two file names:

+----------------------------------+
[ thisfile | /thatfile/ __________X](# thisfile | /thatfile/ __________X)    (thatfile is bold)
[/* thatfile */			   ](#/* thatfile */			   )
[that				   ](#that				   )
[that				   ](#that				   )
[~				   ](#~				   )
[~				   ](#~				   )
[~				   ](#~				   )
[				   ](#				   )
+----------------------------------+

You now have two tab pages.  The first one has a window for "thisfile" and the
second one a window for "thatfile".  It's like two pages that are on top of
each other, with a tab sticking out of each page showing the file name.

Now use the mouse to click on "thisfile" in the top line.  The result is

+----------------------------------+
[ /thisfile/ | thatfile __________X](# /thisfile/ | thatfile __________X)    (thisfile is bold)
[/* thisfile */			   ](#/* thisfile */			   )
[this				   ](#this				   )
[this				   ](#this				   )
[~				   ](#~				   )
[~				   ](#~				   )
[~				   ](#~				   )
[				   ](#				   )
+----------------------------------+

Thus you can switch between tab pages by clicking on the label in the top
line.  If you don't have a mouse or don't want to use it, you can use the "gt"
command.  Mnemonic: Goto Tab.

Now let's create another tab page with the command:
```

:tab split

This makes a new tab page with one window that is editing the same buffer as
the window we were in:

+-------------------------------------+
[ thisfile | /thisfile/ | thatfile __X](# thisfile | /thisfile/ | thatfile __X)   (thisfile is bold)
[/* thisfile */			      ](#/* thisfile */			      )
[this				      ](#this				      )
[this				      ](#this				      )
[~				      ](#~				      )
[~				      ](#~				      )
[~				      ](#~				      )
[				      ](#				      )
+-------------------------------------+

You can put ":tab" before any Ex command that opens a window.  The window will
be opened in a new tab page.  Another example:
```

:tab help gt

Will show the help text for "gt" in a new tab page.

A few more things you can do with tab pages:

- click with the mouse in the space after the last label
The next tab page will be selected, like with "gt".

- click with the mouse on the "X" in the top right corner
The current tab page will be closed.  Unless there are unsaved
changes in the current tab page.

- double click with the mouse in the top line
A new tab page will be created.

- the "tabonly" command
Closes all tab pages except the current one.  Unless there are unsaved
changes in other tab pages.

For more information about tab pages see [tab-page](#tab-page).


## <a id="Using the GUI" class="section-title" href="#Using the GUI">Next Chapter: |Usr_09.Txt|</a> 

Copyright: see [manual-copyright](#manual-copyright)  vim:tw=78:ts=8:noet:ft=help:norl:


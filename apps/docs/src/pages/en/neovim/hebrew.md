---
title: Tree Sitter
description: Some page
layout: "@layouts/MainLayout.astro"
---


## <a id="Nvim" class="section-title" href="#Nvim"> Hebrew Txt</a> 

VIM REFERENCE MANUAL    by Ron Aaron (and Avner Lottem)


### <a id="hebrew" class="section-title" href="#hebrew">Hebrew Language support (options & mapping) for Vim</a>

The supporting 'rightleft' functionality was originally created by Avner
Lottem. <alottem at gmail dot com>  Ron Aaron <ron at ronware dot org> is
currently helping support these features.


Introduction
------------
Hebrew-specific options are 'hkmap', 'hkmapp' 'keymap'=hebrew and 'aleph'.
Hebrew-useful options are 'delcombine', 'allowrevins', 'revins', 'rightleft'
and 'rightleftcmd'.

The 'rightleft' mode reverses the display order, so characters are displayed
from right to left instead of the usual left to right.  This is useful
primarily when editing Hebrew or other Middle-Eastern languages.
See [rileft.txt](#rileft.txt) for further details.

Details
--------------
+  Options:
+  'rightleft' ('rl') sets window orientation to right-to-left.  This means
that the logical text 'ABC' will be displayed as 'CBA', and will start
drawing at the right edge of the window, not the left edge.
+  'hkmap' ('hk') sets keyboard mapping to Hebrew, in insert/replace modes.
+  'aleph' ('al'), numeric, holds the decimal code of Aleph, for keyboard
mapping.
+  'hkmapp' ('hkp') sets keyboard mapping to 'phonetic hebrew'

NOTE: these three ('hkmap', 'hkmapp' and 'aleph') are obsolete.  You should
use ":set keymap=hebrewp" instead.

+  'delcombine' ('deco'), boolean, if editing UTF-8 encoded Hebrew, allows
one to remove the niqud or te`amim by pressing 'x' on a character (with
associated niqud).

+  'rightleftcmd' ('rlc') makes the command-prompt for searches show up on
the right side.  It only takes effect if the window is 'rightleft'.

+  Encoding:
+  Under Unix, ISO 8859-8 encoding (Hebrew letters codes: 224-250).
+  Under MS DOS, PC encoding (Hebrew letters codes: 128-154).
These are defaults, that can be overridden using the 'aleph' option.
+  You should prefer using UTF8, as it supports the combining-characters
('deco' does nothing if UTF8 encoding is not active).

+  Vim arguments:
+  'vim -H file' starts editing a Hebrew file, i.e. 'rightleft' and 'hkmap'
are set.

+  Keyboard:
+  The 'allowrevins' option enables the CTRL-_ command in Insert mode and
in Command-line mode.

+  CTRL-_ in insert/replace modes toggles 'revins' and 'hkmap' as follows:

When in rightleft window, 'revins' and 'nohkmap' are toggled, since
English will likely be inserted in this case.

When in norightleft window, 'revins' 'hkmap' are toggled, since Hebrew
will likely be inserted in this case.

CTRL-_ moves the cursor to the end of the typed text.

+  CTRL-_ in command mode only toggles keyboard mapping (see Bugs below).
This setting is independent of 'hkmap' option, which only applies to
insert/replace mode.

Note: On some keyboards, CTRL-_ is mapped to CTRL-?.

+  Keyboard mapping while 'hkmap' is set (standard Israeli keyboard):

q w e r t y u i o p
/ ' ק ר א ט ו ן ם פ

a s d f g h j k l ; '
ש ד ג כ ע י ח ל ך ף ,

z x c v b n m , . /
ז ס ב ה נ מ צ ת ץ .

This is also the keymap when 'keymap=hebrew' is set.  The advantage of
'keymap' is that it works properly when using UTF8, e.g. it inserts the
correct characters; 'hkmap' does not.  The 'keymap' keyboard can also
insert niqud and te`amim.  To see what those mappings are, look at the
keymap file 'hebrew.vim' etc.


Typing backwards

If the 'revins' (reverse insert) option is set, inserting happens backwards.
This can be used to type Hebrew.  When inserting characters the cursor is not
moved and the text moves rightwards.  A <BS> deletes the character under the
cursor.  CTRL-W and CTRL-U also work in the opposite direction.  <BS>, CTRL-W
and CTRL-U do not stop at the start of insert or end of line, no matter how
the 'backspace' option is set.

There is no reverse replace mode (yet).

If the 'showmode' option is set, "-- REVERSE INSERT --" will be shown in the
status line when reverse Insert mode is active.

When the 'allowrevins' option is set, reverse Insert mode can be also entered
via CTRL-_, which has some extra functionality: First, keyboard mapping is
changed according to the window orientation -- if in a left-to-right window,
'revins' is used to enter Hebrew text, so the keyboard changes to Hebrew
('hkmap' is set); if in a right-to-left window, 'revins' is used to enter
English text, so the keyboard changes to English ('hkmap' is reset).  Second,
when exiting 'revins' via CTRL-_, the cursor moves to the end of the typed
text (if possible).


Pasting when in a rightleft window
----------------------------------
When cutting text with the mouse and pasting it in a rightleft window
the text will be reversed, because the characters come from the cut buffer
from the left to the right, while inserted in the file from the right to
the left.   In order to avoid it, toggle 'revins' (by typing CTRL-? or CTRL-_)
before pasting.


Hebrew characters and the 'isprint' variable
--------------------------------------------
Sometimes Hebrew character codes are in the non-printable range defined by
the 'isprint' variable.  For example in the Linux console, the Hebrew font
encoding starts from 128, while the default 'isprint' variable is @,161-255.
The result is that all Hebrew characters are displayed as ~x.  To solve this
problem, set isprint=@,128-255.


vim:tw=78:ts=8:noet:ft=help:norl:


---
title: Tree Sitter
description: Some page
layout: "@layouts/MainLayout.astro"
---


## <a id="" class="section-title" href="#">*Usr_04.Txt*	Nvim</a> 

VIM USER MANUAL - by Bram Moolenaar

Making small changes


This chapter shows you several ways of making corrections and moving text
around.  It teaches you the three basic ways to change text: operator-motion,
Visual mode and text objects.

[04.1](#04.1)	Operators and motions
[04.2](#04.2)	Changing text
[04.3](#04.3)	Repeating a change
[04.4](#04.4)	Visual mode
[04.5](#04.5)	Moving text
[04.6](#04.6)	Copying text
[04.7](#04.7)	Using the clipboard
[04.8](#04.8)	Text objects
[04.9](#04.9)	Replace mode
[04.10](#04.10)	Conclusion

Next chapter: [usr_05.txt](#usr_05.txt)  Set your settings
Previous chapter: [usr_03.txt](#usr_03.txt)  Moving around
Table of contents: [usr_toc.txt](#usr_toc.txt)


## <a id="" class="section-title" href="#">*04.1*	Operators and Motions</a> 

In chapter 2 you learned the "x" command to delete a single character.  And
using a count: "4x" deletes four characters.
The "dw" command deletes a word.  You may recognize the "w" command as the
move word command.  In fact, the "d" command may be followed by any motion
command, and it deletes from the current location to the place where the
cursor winds up.
The "4w" command, for example, moves the cursor over four words.  The "d4w"
command deletes four words.

To err is human. To really foul up you need a computer. ~
------------------>
d4w

To err is human. you need a computer. ~

Vim only deletes up to the position where the motion takes the cursor.  That's
because Vim knows that you probably don't want to delete the first character
of a word.  If you use the "e" command to move to the end of a word, Vim
guesses that you do want to include that last character:

To err is human. you need a computer. ~
-------->
d2e

To err is human. a computer. ~

Whether the character under the cursor is included depends on the command you
used to move to that character.  The reference manual calls this "exclusive"
when the character isn't included and "inclusive" when it is.

The "$" command moves to the end of a line.  The "d$" command deletes from the
cursor to the end of the line.  This is an inclusive motion, thus the last
character of the line is included in the delete operation:

To err is human. a computer. ~
------------>
d$

To err is human ~

There is a pattern here: operator-motion.  You first type an operator command.
For example, "d" is the delete operator.  Then you type a motion command like
"4l" or "w".  This way you can operate on any text you can move over.


## <a id="" class="section-title" href="#">*04.2*	Changing Text</a> 

Another operator is "c", change.  It acts just like the "d" operator, except
it leaves you in Insert mode.  For example, "cw" changes a word.  Or more
specifically, it deletes a word and then puts you in Insert mode.

To err is human ~
------->
c2wbe<Esc>

To be human ~

This "c2wbe<Esc>" contains these bits:

c	the change operator
2w	move two words (they are deleted and Insert mode started)
be	insert this text

```
Esc>	back to Normal mode

You will have noticed something strange: The space before "human" isn't
deleted.  There is a saying that for every problem there is an answer that is
simple, clear, and wrong.  That is the case with the example used here for the
"cw" command.  The c operator works just like the d operator, with one
exception: "cw".  It actually works like "ce", change to end of word.  Thus
the space after the word isn't included.  This is an exception that dates back
to the old Vi.  Since many people are used to it now, the inconsistency has
remained in Vim.


MORE CHANGES

Like "dd" deletes a whole line, "cc" changes a whole line.  It keeps the
existing indent (leading white space) though.

Just like "d$" deletes until the end of the line, "c$" changes until the end
of the line.  It's like doing "d$" to delete the text and then "a" to start
Insert mode and append new text.


SHORTCUTS

Some operator-motion commands are used so often that they have been given a
single-letter command:

x  stands for  dl  (delete character under the cursor)
X  stands for  dh  (delete character left of the cursor)
D  stands for  d$  (delete to end of the line)
C  stands for  c$  (change to end of the line)
s  stands for  cl  (change one character)
S  stands for  cc  (change a whole line)


WHERE TO PUT THE COUNT

The commands "3dw" and "d3w" delete three words.  If you want to get really
picky about things, the first command, "3dw", deletes one word three times;
the command "d3w" deletes three words once.  This is a difference without a
distinction.  You can actually put in two counts, however.  For example,
"3d2w" deletes two words, repeated three times, for a total of six words.


REPLACING WITH ONE CHARACTER

The "r" command is not an operator.  It waits for you to type a character, and
will replace the character under the cursor with it.  You could do the same
with "cl" or with the "s" command, but with "r" you don't have to press <Esc>
to get back out of insert mode.

there is somerhing grong here ~
rT	     rt    rw

There is something wrong here ~

Using a count with "r" causes that many characters to be replaced with the
same character.  Example:

There is something wrong here ~
5rx

There is something xxxxx here ~

To replace a character with a line break use "r<Enter>".  This deletes one
character and inserts a line break.  Using a count here only applies to the
number of characters deleted: "4r<Enter>" replaces four characters with one
line break.


## <a id="" class="section-title" href="#">*04.3*	Repeating a Change</a> 

The "." command is one of the simplest yet powerful commands in Vim.  It
repeats the last change.  For instance, suppose you are editing an HTML file
and want to delete all the <B> tags.  You position the cursor on the first <
and delete the <B> with the command "df>".  You then go to the < of the next

```
/B> and delete it using the "." command.  The "." command executes the last
change command (in this case, "df>").  To delete another tag, position the
cursor on the < and use the "." command.

To <B>generate</B> a table of <B>contents ~
f<   find first <     --->
df>  delete to >	 -->
f<   find next <	   --------->
.    repeat df>			    --->
f<   find next <		       ------------->
.    repeat df>					    -->

The "." command works for all changes you make, except for "u" (undo), CTRL-R
(redo) and commands that start with a colon (:).

Another example: You want to change the word "four" to "five".  It appears
several times in your text.  You can do this quickly with this sequence of
commands:

/four<Enter>	find the first string "four"
cwfive<Esc>	change the word to "five"
n		find the next "four"
.		repeat the change to "five"
n		find the next "four"
.		repeat the change
etc.


## <a id="" class="section-title" href="#">*04.4*	Visual Mode</a> 

To delete simple items the operator-motion changes work quite well.  But often
it's not so easy to decide which command will move over the text you want to
change.  Then you can use Visual mode.

You start Visual mode by pressing "v".  You move the cursor over the text you
want to work on.  While you do this, the text is highlighted.  Finally type
the operator command.
For example, to delete from the middle of a word to the middle of another:

This is an examination sample of visual mode ~
---------->
velllld

This is an example of visual mode ~

When doing this you don't really have to count how many times you have to
press "l" to end up in the right position.  You can immediately see what text
will be deleted when you press "d".

If at any time you decide you don't want to do anything with the highlighted
text, just press <Esc> and Visual mode will stop without doing anything.


SELECTING LINES

If you want to work on whole lines, use "V" to start Visual mode.  You will
see right away that the whole line is highlighted, without moving around.
When you move left or right nothing changes.  When you move up or down the
selection is extended whole lines at a time.
For example, select three lines with "Vjj":

+------------------------+
[ text more text	   ](# text more text	   )
>> [ more text more text    | ](# more text more text    | )
selected lines >> [ text text text	   | ](# text text text	   | ) Vjj
>> [ text more		   ](# text more		   ) V
[ more text more	   ](# more text more	   )
+------------------------+


SELECTING BLOCKS

If you want to work on a rectangular block of characters, use CTRL-V to start
Visual mode.  This is very useful when working on tables.

name		Q1	Q2	Q3
pierre		123	455	234
john		0	90	39
steve		392	63	334

To delete the middle "Q2" column, move the cursor to the "Q" of "Q2".  Press
CTRL-V to start blockwise Visual mode.  Now move the cursor three lines down
with "3j" and to the next word with "w".  You can see the first character of
the last column is included.  To exclude it, use "h".  Now press "d" and the
middle column is gone.


GOING TO THE OTHER SIDE

If you have selected some text in Visual mode, and discover that you need to
change the other end of the selection, use the "o" command (Hint: o for other
end).  The cursor will go to the other end, and you can move the cursor to
change where the selection starts.  Pressing "o" again brings you back to the
other end.

When using blockwise selection, you have four corners.  "o" only takes you to
one of the other corners, diagonally.  Use "O" to move to the other corner in
the same line.

Note that "o" and "O" in Visual mode work very differently from Normal mode,
where they open a new line below or above the cursor.


## <a id="" class="section-title" href="#">*04.5*	Moving Text</a> 

When you delete something with "d", "x", or another command, the text is
saved.  You can paste it back by using the "p" command.  (The Vim name for
this is put).
Take a look at how this works.  First you will delete an entire line, by
putting the cursor on the line you want to delete and typing "dd".  Now you
move the cursor to where you want to put the line and use the "p" (put)
command.  The line is inserted on the line below the cursor.

a line		a line	      a line
line 2	  dd	line 3	  p   line 3
line 3			      line 2

Because you deleted an entire line, the "p" command placed the text line below
the cursor.  If you delete part of a line (a word, for instance), the "p"
command puts it just after the cursor.

Some more boring try text to out commands. ~
---->
dw

Some more boring text to out commands. ~
------->
welp

Some more boring text to try out commands. ~


MORE ON PUTTING

The "P" command puts text like "p", but before the cursor.  When you deleted a
whole line with "dd", "P" will put it back above the cursor.  When you deleted
a word with "dw", "P" will put it back just before the cursor.

You can repeat putting as many times as you like.  The same text will be used.

You can use a count with "p" and "P".  The text will be repeated as many times
as specified with the count.  Thus "dd" and then "3p" puts three copies of the
same deleted line.


SWAPPING TWO CHARACTERS

Frequently when you are typing, your fingers get ahead of your brain (or the
other way around?).  The result is a typo such as "teh" for "the".  Vim
makes it easy to correct such problems.  Just put the cursor on the e of "teh"
and execute the command "xp".  This works as follows: "x" deletes the
character e and places it in a register.  "p" puts the text after the cursor,
which is after the h.

teh     th     the ~
x       p


## <a id="" class="section-title" href="#">*04.6*	Copying Text</a> 

To copy text from one place to another, you could delete it, use "u" to undo
the deletion and then "p" to put it somewhere else.  There is an easier way:
yanking.  The "y" operator copies text into a register.  Then a "p" command
can be used to put it.
Yanking is just a Vim name for copying.  The "c" letter was already used
for the change operator, and "y" was still available.  Calling this
operator "yank" made it easier to remember to use the "y" key.

Since "y" is an operator, you use "yw" to yank a word.  A count is possible as
usual.  To yank two words use "y2w".  Example:

let sqr = LongVariable * ~
-------------->
y2w

let sqr = LongVariable * ~
p

let sqr = LongVariable * LongVariable ~

Notice that "yw" includes the white space after a word.  If you don't want
this, use "ye".

The "yy" command yanks a whole line, just like "dd" deletes a whole line.

a text line   yy	a text line	       a text line
line 2			line 2		p      line 2
last line		last line	       a text line
last line

"Y" was originally equivalent to "yank the entire line", as opposed to "D"
which is "delete to end of the line".  "Y" has thus been remapped to mean
"yank to end of the line" to make it consistent with the behavior of "D".
Mappings will be covered in later chapters.


## <a id="" class="section-title" href="#">*04.7*	Using the Clipboard</a> 

If you are using the GUI version of Vim (gvim), you can find the "Copy" item
in the "Edit" menu.  First select some text with Visual mode, then use the
Edit/Copy menu item.  The selected text is now copied to the clipboard.  You
can paste the text in other programs.  In Vim itself too.

If you have copied text to the clipboard in another application, you can paste
it in Vim with the Edit/Paste menu item.  This works in Normal mode and Insert
mode.  In Visual mode the selected text is replaced with the pasted text.

The "Cut" menu item deletes the text before it's put on the clipboard.  The
"Copy", "Cut" and "Paste" items are also available in the popup menu (only
when there is a popup menu, of course).  If your Vim has a toolbar, you can
also find these items there.

If you are not using the GUI, or if you don't like using a menu, you have to
use another way.  You use the normal "y" (yank) and "p" (put) commands, but
prepend "* (double-quote star) before it.  To copy a line to the clipboard:
```

"*yy

To put text from the clipboard back into the text:
```

"*p

This only works on versions of Vim that include clipboard support.  More about
the clipboard can be found in section [09.3| and here: |clipboard](#09.3| and here: |clipboard).


## <a id="" class="section-title" href="#">*04.8*	Text Objects</a> 

If the cursor is in the middle of a word and you want to delete that word, you
need to move back to its start before you can do "dw".  There is a simpler way
to do this: "daw".

this is some example text. ~
daw

this is some text. ~

The "d" of "daw" is the delete operator.  "aw" is a text object.  Hint: "aw"
stands for "A Word".  Thus "daw" is "Delete A Word".  To be precise, the white
space after the word is also deleted (or the white space before the word if at
the end of the line).

Using text objects is the third way to make changes in Vim.  We already had
operator-motion and Visual mode.  Now we add operator-text object.
It is very similar to operator-motion, but instead of operating on the text
between the cursor position before and after a movement command, the text
object is used as a whole.  It doesn't matter where in the object the cursor
was.

To change a whole sentence use "cis".  Take this text:

Hello there.  This ~
is an example.  Just ~
some text. ~

Move to the start of the second line, on "is an".  Now use "cis":

Hello there.    Just ~
some text. ~

The cursor is in between the blanks in the first line.  Now you type the new
sentence "Another line.":

Hello there.  Another line.  Just ~
some text. ~

"cis" consists of the "c" (change) operator and the "is" text object.  This
stands for "Inner Sentence".  There is also the "as" ("A Sentence") object.
The difference is that "as" includes the white space after the sentence and
"is" doesn't.  If you would delete a sentence, you want to delete the white
space at the same time, thus use "das".  If you want to type new text the
white space can remain, thus you use "cis".

You can also use text objects in Visual mode.  It will include the text object
in the Visual selection.  Visual mode continues, thus you can do this several
times.  For example, start Visual mode with "v" and select a sentence with
"as".  Now you can repeat "as" to include more sentences.  Finally you use an
operator to do something with the selected sentences.

You can find a long list of text objects here: [text-objects](#text-objects).


## <a id="" class="section-title" href="#">*04.9*	Replace Mode</a> 

The "R" command causes Vim to enter replace mode.  In this mode, each
character you type replaces the one under the cursor.  This continues until
you type <Esc>.
In this example you start Replace mode on the first "t" of "text":

This is text. ~
Rinteresting.<Esc>

This is interesting. ~

You may have noticed that this command replaced 5 characters in the line with
twelve others.  The "R" command automatically extends the line if it runs out
of characters to replace.  It will not continue on the next line.

You can switch between Insert mode and Replace mode with the <Insert> key.

When you use <BS> (backspace) to make a correction, you will notice that the
old text is put back.  Thus it works like an undo command for the previously
typed character.


## <a id="" class="section-title" href="#">*04.10*	Conclusion</a> 

The operators, movement commands and text objects give you the possibility to
make lots of combinations.  Now that you know how they work, you can use N
operators with M movement commands to make N * M commands!

You can find a list of operators here: [operator](#operator).

For example, there are many other ways to delete pieces of text.  Here are a
few common ones:

x	delete character under the cursor (short for "dl")
X	delete character before the cursor (short for "dh")
D	delete from cursor to end of line (short for "d$")
dw	delete from cursor to next start of word
db	delete from cursor to previous start of word
diw	delete word under the cursor (excluding white space)
daw	delete word under the cursor (including white space)
dG	delete until the end of the file
dgg	delete until the start of the file

If you use "c" instead of "d" they become change commands.  And with "y" you
yank the text.  And so forth.


There are a few common commands to make changes that didn't fit somewhere
else:

~	Change case of the character under the cursor, and move the
cursor to the next character.  This is not an operator (unless
'tildeop' is set), thus you can't use it with a motion
command.  It does work in Visual mode, where it changes case
for all the selected text.

I	Start Insert mode after moving the cursor to the first
non-blank in the line.

A	Start Insert mode after moving the cursor to the end of the
line.


## <a id="Set your settings" class="section-title" href="#Set your settings">Next Chapter: |Usr_05.Txt|</a> 

Copyright: see [manual-copyright](#manual-copyright)  vim:tw=78:ts=8:noet:ft=help:norl:


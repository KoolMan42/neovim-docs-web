---
title: Tree Sitter
description: Some page
layout: "@layouts/MainLayout.astro"
---


## <a id="" class="section-title" href="#">*Usr_20.Txt*	Nvim</a> 

VIM USER MANUAL - by Bram Moolenaar

Typing command-line commands quickly


Vim has a few generic features that makes it easier to enter commands.  Colon
commands can be abbreviated, edited and repeated.  Completion is available for
nearly everything.

[20.1](#20.1)	Command line editing
[20.2](#20.2)	Command line abbreviations
[20.3](#20.3)	Command line completion
[20.4](#20.4)	Command line history
[20.5](#20.5)	Command line window

Next chapter: [usr_21.txt](#usr_21.txt)  Go away and come back
Previous chapter: [usr_12.txt](#usr_12.txt)  Clever tricks
Table of contents: [usr_toc.txt](#usr_toc.txt)


## <a id="" class="section-title" href="#">*20.1*	Command Line Editing</a> 

When you use a colon (:) command or search for a string with / or ?, Vim puts
the cursor on the bottom of the screen.  There you type the command or search
pattern.  This is called the Command line.  Also when it's used for entering a
search command.

The most obvious way to edit the command you type is by pressing the <BS> key.
This erases the character before the cursor.  To erase another character,
typed earlier, first move the cursor with the cursor keys.
For example, you have typed this:
```

:s/col/pig/

Before you hit <Enter>, you notice that "col" should be "cow".  To correct
this, you type <Left> five times.  The cursor is now just after "col".  Type

```
BS> and "w" to correct:
```

:s/cow/pig/

Now you can press <Enter> directly.  You don't have to move the cursor to the
end of the line before executing the command.

The most often used keys to move around in the command line:


```
Left>			one character left

```
Right>			one character right

```
S-Left> or <C-Left>	one word left

```
S-Right> or <C-Right>	one word right
CTRL-B or <Home>	to begin of command line
CTRL-E or <End>		to end of command line

Note:

```
S-Left> (cursor left key with Shift key pressed) and <C-Left> (cursor
left key with Control pressed) will not work on all keyboards.  Same
for the other Shift and Control combinations.

You can also use the mouse to move the cursor.


DELETING

As mentioned, <BS> deletes the character before the cursor.  To delete a whole
word use CTRL-W.

/the fine pig ~

CTRL-W

/the fine ~

CTRL-U removes all text, thus allows you to start all over again.


OVERSTRIKE

The <Insert> key toggles between inserting characters and replacing the
existing ones.  Start with this text:

/the fine pig ~

Move the cursor to the start of "fine" with <S-Left> twice (or <Left> eight
times, if <S-Left> doesn't work).  Now press <Insert> to switch to overstrike
and type "great":

/the greatpig ~

Oops, we lost the space.  Now, don't use <BS>, because it would delete the
"t" (this is different from Replace mode).  Instead, press <Insert> to switch
from overstrike to inserting, and type the space:

/the great pig ~


CANCELLING

You thought of executing a : or / command, but changed your mind.  To get rid
of what you already typed, without executing it, press CTRL-C or <Esc>.

Note:

```
Esc> is the universal "get out" key.  Unfortunately, in the good old
Vi pressing <Esc> in a command line executed the command!  Since that
might be considered to be a bug, Vim uses <Esc> to cancel the command.
But with the 'cpoptions' option it can be made Vi compatible.  And
when using a mapping (which might be written for Vi) <Esc> also works
Vi compatible.  Therefore, using CTRL-C is a method that always works.

If you are at the start of the command line, pressing <BS> will cancel the
command.  It's like deleting the ":" or "/" that the line starts with.


## <a id="" class="section-title" href="#">*20.2*	Command Line Abbreviations</a> 

Some of the ":" commands are really long.  We already mentioned that
":substitute" can be abbreviated to ":s".  This is a generic mechanism, all
":" commands can be abbreviated.

How short can a command get?  There are 26 letters, and many more commands.
For example, ":set" also starts with ":s", but ":s" doesn't start a ":set"
command.  Instead ":set" can be abbreviated to ":se".
When the shorter form of a command could be used for two commands, it
stands for only one of them.  There is no logic behind which one, you have to
learn them.  In the help files the shortest form that works is mentioned.  For
example:
```

:s[ubstitute]

This means that the shortest form of ":substitute" is ":s".  The following
characters are optional.  Thus ":su" and ":sub" also work.

In the user manual we will either use the full name of command, or a short
version that is still readable.  For example, ":function" can be abbreviated
to ":fu".  But since most people don't understand what that stands for, we
will use ":fun".  (Vim doesn't have a ":funny" command, otherwise ":fun" would
be confusing too.)

It is recommended that in Vim scripts you write the full command name.  That
makes it easier to read back when you make later changes.  Except for some
often used commands like ":w" (":write") and ":r" (":read").
A particularly confusing one is ":end", which could stand for ":endif",
":endwhile" or ":endfunction".  Therefore, always use the full name.


SHORT OPTION NAMES

In the user manual the long version of the option names is used.  Many options
also have a short name.  Unlike ":" commands, there is only one short name
that works.  For example, the short name of 'autoindent' is 'ai'.  Thus these
two commands do the same thing:
```

:set autoindent
:set ai

You can find the full list of long and short names here: [option-list](#option-list).


## <a id="" class="section-title" href="#">*20.3*	Command Line Completion</a> 

This is one of those Vim features that, by itself, is a reason to switch from
Vi to Vim.  Once you have used this, you can't do without.

Suppose you have a directory that contains these files:

info.txt
intro.txt
bodyofthepaper.txt

To edit the last one, you use the command:
```

:edit bodyofthepaper.txt

It's easy to type this wrong.  A much quicker way is:
```

:edit b<Tab>

Which will result in the same command.  What happened?  The <Tab> key does
completion of the word before the cursor.  In this case "b".  Vim looks in the
directory and finds only one file that starts with a "b".  That must be the
one you are looking for, thus Vim completes the file name for you.

Now type:
```

:edit i<Tab>

Vim will beep, and give you:
```

:edit info.txt

The beep means that Vim has found more than one match.  It then uses the first
match it found (alphabetically).  If you press <Tab> again, you get:
```

:edit intro.txt

Thus, if the first <Tab> doesn't give you the file you were looking for, press
it again.  If there are more matches, you will see them all, one at a time.
If you press <Tab> on the last matching entry, you will go back to what you
first typed:
```

:edit i

Then it starts all over again.  Thus Vim cycles through the list of matches.
Use CTRL-P to go through the list in the other direction:


```
------------------- <Tab> -------------------------+
|

```
Tab> -->		       <Tab> -->
:edit i		      :edit info.txt		   :edit intro.txt

```
-- CTRL-P		       <-- CTRL-P
|
+---------------------- CTRL-P ------------------------>


CONTEXT

When you type ":set i" instead of ":edit i" and press <Tab> you get:
```

:set icon

Hey, why didn't you get ":set info.txt"?  That's because Vim has context
sensitive completion.  The kind of words Vim will look for depends on the
command before it.  Vim knows that you cannot use a file name just after a
":set" command, but you can use an option name.
Again, if you repeat typing the <Tab>, Vim will cycle through all matches.
There are quite a few, it's better to type more characters first:
```

:set isk<Tab>

Gives:
```

:set iskeyword

Now type "=" and press <Tab>:
```

:set iskeyword=@,48-57,_,192-255

What happens here is that Vim inserts the old value of the option.  Now you
can edit it.
What is completed with <Tab> is what Vim expects in that place.  Just try
it out to see how it works.  In some situations you will not get what you
want.  That's either because Vim doesn't know what you want, or because
completion was not implemented for that situation.  In that case you will get
a <Tab> inserted (displayed as ^I).


LIST MATCHES

When there are many matches, you would like to see an overview.  Do this by
pressing CTRL-D.  For example, pressing CTRL-D after:
```

:set is

results in:
```

:set is
incsearch  isfname    isident    iskeyword  isprint
:set is

Vim lists the matches and then comes back with the text you typed.  You can
now check the list for the item you wanted.  If it isn't there, you can use

```
BS> to correct the word.  If there are many matches, type a few more
characters before pressing <Tab> to complete the rest.
If you have watched carefully, you will have noticed that "incsearch"
doesn't start with "is".  In this case "is" stands for the short name of
"incsearch".  (Many options have a short and a long name.)  Vim is clever
enough to know that you might have wanted to expand the short name of the
option into the long name.


THERE IS MORE

The CTRL-L command completes the word to the longest unambiguous string.  If
you type ":edit i" and there are files "info.txt" and "info_backup.txt" you
will get ":edit info".

The 'wildmode' option can be used to change the way completion works.
The 'wildmenu' option can be used to get a menu-like list of matches.
Use the 'suffixes' option to specify files that are less important and appear
at the end of the list of files.
The 'wildignore' option specifies files that are not listed at all.

More about all of this here: [cmdline-completion](#cmdline-completion)


## <a id="" class="section-title" href="#">*20.4*	Command Line History</a> 

In chapter 3 we briefly mentioned the history.  The basics are that you can
use the <Up> key to recall an older command line.  <Down> then takes you back
to newer commands.

There are actually five histories.  The ones we will mention here are for ":"
commands and for "/" and "?" search commands.  The "/" and "?" commands share
the same history, because they are both search commands.  The three other
histories are for expressions, debug mode commands and input lines for the
input() function.  [cmdline-history](#cmdline-history)

Suppose you have done a ":set" command, typed ten more colon commands and then
want to repeat that ":set" command again.  You could press ":" and then ten
times <Up>.  There is a quicker way:
```

:se<Up>

Vim will now go back to the previous command that started with "se".  You have
a good chance that this is the ":set" command you were looking for.  At least
you should not have to press <Up> very often (unless ":set" commands is all
you have done).

The <Up> key will use the text typed so far and compare it with the lines in
the history.  Only matching lines will be used.
If you do not find the line you were looking for, use <Down> to go back to
what you typed and correct that.  Or use CTRL-U to start all over again.

To see all the lines in the history:
```

:history

That's the history of ":" commands.  The search history is displayed with this
command:
```

:history /

CTRL-P will work like <Up>, except that it doesn't matter what you already
typed.  Similarly for CTRL-N and <Down>.  CTRL-P stands for previous, CTRL-N
for next.


## <a id="" class="section-title" href="#">*20.5*	Command Line Window</a> 

Typing the text in the command line works differently from typing text in
Insert mode.  It doesn't allow many commands to change the text.  For most
commands that's OK, but sometimes you have to type a complicated command.
That's where the command line window is useful.

Open the command line window with this command:
```

q:

Vim now opens a (small) window at the bottom.  It contains the command line
history, and an empty line at the end:

+-------------------------------------+
[other window			      ](#other window			      )
[~				      ](#~				      )
[file.txt=============================](#file.txt=============================)
[:e c				      ](#:e c				      )
[:e config.h.in			      ](#:e config.h.in			      )
[:set path=.,/usr/include,,	      ](#:set path=.,/usr/include,,	      )
[:set iskeyword=@,48-57,_,192-255     ](#:set iskeyword=@,48-57,_,192-255     )
[:set is			      ](#:set is			      )
[:q				      ](#:q				      )
[:				      ](#:				      )
[command-line=========================](#command-line=========================)
[				      ](#				      )
+-------------------------------------+

You are now in Normal mode.  You can use the "hjkl" keys to move around.  For
example, move up with "5k" to the ":e config.h.in" line.  Type "$h" to go to
the "i" of "in" and type "cwout".  Now you have changed the line to:

:e config.h.out ~

Now press <Enter> and this command will be executed.  The command line window
will close.
The <Enter> command will execute the line under the cursor.  It doesn't
matter whether Vim is in Insert mode or in Normal mode.
Changes in the command line window are lost.  They do not result in the
history to be changed.  Except that the command you execute will be added to
the end of the history, like with all executed commands.

The command line window is very useful when you want to have overview of the
history, lookup a similar command, change it a bit and execute it.  A search
command can be used to find something.
In the previous example the "?config" search command could have been used
to find the previous command that contains "config".  It's a bit strange,
because you are using a command line to search in the command line window.
While typing that search command you can't open another command line window,
there can be only one.


## <a id="Go away and come back" class="section-title" href="#Go away and come back">Next Chapter: |Usr_21.Txt|</a> 

Copyright: see [manual-copyright](#manual-copyright)  vim:tw=78:ts=8:noet:ft=help:norl:


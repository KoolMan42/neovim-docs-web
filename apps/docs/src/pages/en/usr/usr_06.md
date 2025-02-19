---
title: Tree Sitter
description: Some page
layout: "@layouts/MainLayout.astro"
---


## <a id="" class="section-title" href="#">*Usr_06.Txt*	Nvim</a> 

VIM USER MANUAL - by Bram Moolenaar

Using syntax highlighting


Black and white text is boring.  With colors your file comes to life.  This
not only looks nice, it also speeds up your work.  Change the colors used for
the different sorts of text.  Print your text, with the colors you see on the
screen.

[06.1](#06.1)	Switching it on
[06.2](#06.2)	No or wrong colors?
[06.3](#06.3)	Different colors
[06.4](#06.4)	With colors or without colors
[06.5](#06.5)	Printing with colors
[06.6](#06.6)	Further reading

Next chapter: [usr_07.txt](#usr_07.txt)  Editing more than one file
Previous chapter: [usr_05.txt](#usr_05.txt)  Set your settings
Table of contents: [usr_toc.txt](#usr_toc.txt)


## <a id="" class="section-title" href="#">*06.1*	Switching It On</a> 

Syntax highlighting is enabled by default.  Nvim will automagically detect the
type of file and load the right syntax highlighting.


## <a id="" class="section-title" href="#">*06.2*	No or Wrong Colors?</a> 

There can be a number of reasons why you don't see colors:

- Your terminal does not support colors.
Vim will use bold, italic and underlined text, but this doesn't look
very nice.  You probably will want to try to get a terminal with
colors.

- Your terminal does support colors, but Vim doesn't know this.
Make sure your $TERM setting is correct.  For example, when using an
xterm that supports colors:
```

setenv TERM xterm-color

```

or (depending on your shell):
```

TERM=xterm-color; export TERM


```
	The terminal name must match the terminal you are using.

- The file type is not recognized.
Vim doesn't know all file types, and sometimes it's near to impossible
to tell what language a file uses.  Try this command:
```

:set filetype

```

If the result is "filetype=" then the problem is indeed that Vim
doesn't know what type of file this is.  You can set the type
manually:
```

:set filetype=fortran


```
	To see which types are available, look in the directory
$VIMRUNTIME/syntax.  For the GUI you can use the Syntax menu.
Setting the filetype can also be done with a [modeline](#modeline), so that the
file will be highlighted each time you edit it.  For example, this
line can be used in a Makefile (put it near the start or end of the
file):
```

# vim: syntax=make


```
	You might know how to detect the file type yourself.  Often the file
name extension (after the dot) can be used.
See [new-filetype](#new-filetype) for how to tell Vim to detect that file type.

- There is no highlighting for your file type.
You could try using a similar file type by manually setting it as
mentioned above.  If that isn't good enough, you can write your own
syntax file, see [mysyntaxfile](#mysyntaxfile).


Or the colors could be wrong:

- The colored text is very hard to read.
Vim guesses the background color that you are using.  If it is black
(or another dark color) it will use light colors for text.  If it is
white (or another light color) it will use dark colors for text.  If
Vim guessed wrong the text will be hard to read.  To solve this, set
the 'background' option.  For a dark background:
```

:set background=dark


```
	And for a light background:
```

:set background=light


```
	Make sure you put this _before_ the ":syntax enable" command,
otherwise the colors will already have been set.  You could do
":syntax reset" after setting 'background' to make Vim set the default
colors again.

- The colors are wrong when scrolling bottom to top.
Vim doesn't read the whole file to parse the text.  It starts parsing
wherever you are viewing the file.  That saves a lot of time, but
sometimes the colors are wrong.  A simple fix is hitting CTRL-L.  Or
scroll back a bit and then forward again.
For a real fix, see [:syn-sync](#:syn-sync).  Some syntax files have a way to make
it look further back, see the help for the specific syntax file.  For
example, [tex.vim](#tex.vim) for the TeX syntax.


## <a id=":syn-default-override" class="section-title" href="#:syn-default-override">*06.3*	Different Colors</a> 

If you don't like the default colors, you can select another color scheme.  In
the GUI use the Edit/Color Scheme menu.  You can also type the command:
```

:colorscheme evening

"evening" is the name of the color scheme.  There are several others you might
want to try out.  Look in the directory $VIMRUNTIME/colors.

When you found the color scheme that you like, add the ":colorscheme" command
to your [init.vim](#init.vim) file.

You could also write your own color scheme.  This is how you do it:

1. Select a color scheme that comes close.  Copy this file to your own Vim
directory.  For Unix, this should work:
```

!mkdir -p ~/.config/nvim/colors
!cp $VIMRUNTIME/colors/morning.vim ~/.config/nvim/colors/mine.vim

```

This is done from Vim, because it knows the value of $VIMRUNTIME.

2. Edit the color scheme file.  These entries are useful:

cterm		attributes in a color terminal
ctermfg		foreground color in a color terminal
ctermbg		background color in a color terminal
gui		attributes in the GUI
guifg		foreground color in the GUI
guibg		background color in the GUI

For example, to make comments green:
```

:highlight Comment ctermfg=green guifg=green

```

Attributes you can use for "cterm" and "gui" are "bold" and "underline".
If you want both, use "bold,underline".  For details see the [:highlight](#:highlight)
command.

3. Tell Vim to always use your color scheme.  Put this line in your [vimrc](#vimrc):
```

colorscheme mine

If you want to see what the most often used color combinations look like, use
this command:
```

:runtime syntax/colortest.vim

You will see text in various color combinations.  You can check which ones are
readable and look nice.


## <a id="" class="section-title" href="#">*06.4*	With Colors or Without Colors</a> 

Displaying text in color takes a lot of effort.  If you find the displaying
too slow, you might want to disable syntax highlighting for a moment:
```

:syntax clear

When editing another file (or the same one) the colors will come back.

If you want to stop highlighting completely use:
```

:syntax off

This will completely disable syntax highlighting and remove it immediately for
all buffers.  See [:syntax-off](#:syntax-off) for more details.

### <a id=":syn-manual" class="section-title" href="#:syn-manual">Note:</a>
If you want syntax highlighting only for specific files, use this:
```

:syntax manual

This will enable the syntax highlighting, but not switch it on automatically
when starting to edit a buffer.  To switch highlighting on for the current
buffer, set the 'syntax' option:
```

:set syntax=ON

```



## <a id="syntax-printing" class="section-title" href="#syntax-printing">*06.5*	Printing With Colors</a> 

In the MS-Windows version you can print the current file with this command:
```

:hardcopy

You will get the usual printer dialog, where you can select the printer and a
few settings.  If you have a color printer, the paper output should look the
same as what you see inside Vim.  But when you use a dark background the
colors will be adjusted to look good on white paper.

There are several options that change the way Vim prints:
'printdevice'
'printheader'
'printfont'
'printoptions'

To print only a range of lines,  use Visual mode to select the lines and then
type the command:
```

v100j:hardcopy

"v" starts Visual mode.  "100j" moves a hundred lines down, they will be
highlighted.  Then ":hardcopy" will print those lines.  You can use other
commands to move in Visual mode, of course.

This also works on Unix, if you have a PostScript printer.  Otherwise, you
will have to do a bit more work.  You need to convert the text to HTML first,
and then print it from a web browser.

Convert the current file to HTML with this command:
```

:TOhtml

In case that doesn't work:
```

:source $VIMRUNTIME/syntax/2html.vim

You will see it crunching away, this can take quite a while for a large file.
Some time later another window shows the HTML code.  Now write this somewhere
(doesn't matter where, you throw it away later):
```
:write main.c.html

Open this file in your favorite browser and print it from there.  If all goes
well, the output should look exactly as it does in Vim.  See [2html.vim](#2html.vim) for
details.  Don't forget to delete the HTML file when you are done with it.

Instead of printing, you could also put the HTML file on a web server, and let
others look at the colored text.


## <a id="" class="section-title" href="#">*06.6*	Further Reading</a> 

[usr_44.txt](#usr_44.txt)  Your own syntax highlighted.
[syntax](#syntax)      All the details.


## <a id="Editing more than one file" class="section-title" href="#Editing more than one file">Next Chapter: |Usr_07.Txt|</a> 

Copyright: see [manual-copyright](#manual-copyright)  vim:tw=78:ts=8:noet:ft=help:norl:


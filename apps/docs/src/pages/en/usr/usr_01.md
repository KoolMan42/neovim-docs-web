---
title: Tree Sitter
description: Some page
layout: "@layouts/MainLayout.astro"
---


## <a id="" class="section-title" href="#">*Usr_01.Txt*	Nvim</a> 

VIM USER MANUAL - by Bram Moolenaar

About the manuals


This chapter introduces the manuals available with Vim.  Read this to know the
conditions under which the commands are explained.

[01.1](#01.1)	Two manuals
[01.2](#01.2)	Vim installed
[01.3](#01.3)	Using the Vim tutor
[01.4](#01.4)	Copyright

Next chapter: [usr_02.txt](#usr_02.txt)  The first steps in Vim
Table of contents: [usr_toc.txt](#usr_toc.txt)


## <a id="" class="section-title" href="#">*01.1*	Two Manuals</a> 

The Vim documentation consists of two parts:

1. The User manual
Task oriented explanations, from simple to complex.  Reads from start to
end like a book.

2. The Reference manual
Precise description of how everything in Vim works.

The notation used in these manuals is explained here: [notation](#notation)


JUMPING AROUND

The text contains hyperlinks between the two parts, allowing you to quickly
jump between the description of an editing task and a precise explanation of
the commands and options used for it.  Use these two commands:

Press  CTRL-]  to jump to a subject under the cursor.
Press  CTRL-O  to jump back (repeat to go further back).

Many links are in vertical bars, like this: [bars](#bars).  The bars themselves may
be hidden or invisible; see below.  An option name, like 'number', a command
in double quotes like ":write" and any other word can also be used as a link.
Try it out: Move the cursor to  CTRL-]  and press CTRL-] on it.

Other subjects can be found with the ":help" command; see [help.txt](#help.txt).

The bars and stars are usually hidden with the [conceal](#conceal) feature.  They also
use [hl-Ignore](#hl-Ignore), using the same color for the text as the background.  You can
make them visible with:
```
:set conceallevel=0
:hi link HelpBar Normal
:hi link HelpStar Normal


## <a id="setup-vimrc_example" class="section-title" href="#setup-vimrc_example">*01.2*	Vim Installed</a> 

To create an empty vimrc:
```

:call mkdir(stdpath('config'),'p')
:exe 'edit' stdpath('config').'/init.vim'
:write

For more info see [vimrc](#vimrc).


## <a id="tutor vimtutor" class="section-title" href="#tutor vimtutor">*01.3*	Using the Vim Tutor</a> 

Instead of reading the text (boring!) you can use :Tutor to learn your first
Vim commands.  This is a 30-minute tutorial that teaches the most basic Vim
functionality hands-on.

To start the tutorial, execute
```

:Tutor

```

from within nvim. The tutorial will lead you from that point. Have fun!


## <a id="manual-copyright" class="section-title" href="#manual-copyright">*01.4*	Copyright</a> 

The Vim user manual and reference manual are Copyright (c) 1988-2003 by Bram
Moolenaar.  This material may be distributed only subject to the terms and
conditions set forth in the Open Publication License, v1.0 or later.  The
latest version is presently available at:
https://www.opencontent.org/openpub/

People who contribute to the manuals must agree with the above copyright
notice.
### <a id="frombook" class="section-title" href="#frombook">Note:</a>
Parts of the user manual come from the book "Vi IMproved - Vim" by Steve
Oualline (published by New Riders Publishing, ISBN: 0735710015).  The Open
Publication License applies to this book.  Only selected parts are included
and these have been modified (e.g., by removing the pictures, updating the
text for Vim 6.0 and later, fixing mistakes).  The omission of the [frombook](#frombook)
tag does not mean that the text does not come from the book.

Many thanks to Steve Oualline and New Riders for creating this book and
publishing it under the OPL!  It has been a great help while writing the user
manual.  Not only by providing literal text, but also by setting the tone and
style.

If you make money through selling the manuals, you are strongly encouraged to
donate part of the profit to help AIDS victims in Uganda.  See [iccf](#iccf).


## <a id="The first steps in Vim" class="section-title" href="#The first steps in Vim">Next Chapter: |Usr_02.Txt|</a> 

Copyright: see [manual-copyright](#manual-copyright)  vim:tw=78:ts=8:noet:ft=help:norl:


---
title: Tree Sitter
description: Some page
layout: "@layouts/MainLayout.astro"
---


## <a id="Nvim" class="section-title" href="#Nvim"> Gui Txt</a> 

VIM REFERENCE MANUAL    by Bram Moolenaar


### <a id="gui GUI" class="section-title" href="#gui GUI">Nvim Graphical User Interface</a>

Type [gO](#gO) to see the table of contents.


## <a id="gui-start E229 E233" class="section-title" href="#gui-start E229 E233">Starting the GUI</a> 

### <a id="ginit.vim gui-init gvimrc $MYGVIMRC" class="section-title" href="#ginit.vim gui-init gvimrc $MYGVIMRC">Note:</a>
For GUI-specific configuration Nvim provides the [UIEnter](#UIEnter) event.  This
happens after other [initialization](#initialization)s, like reading your vimrc file.

Example: this sets "g:gui" to the value of the UI's "rgb" field:
```
:autocmd UIEnter * let g:gui = filter(nvim_list_uis(),{k,v-> v.chan==v:event.chan})[0].rgb

```


### <a id=":winp :winpos E188" class="section-title" href="#:winp :winpos E188">Note:</a>
:winp[os]
Display current position of the top left corner of the GUI vim
window in pixels.  Does not work in all versions.
Also see [getwinpos()|, |getwinposx()| and |getwinposy()](#getwinpos()|, |getwinposx()| and |getwinposy()).

### <a id="E466" class="section-title" href="#E466">:winp[os] {X} {Y}</a>
Put the GUI vim window at the given {X} and {Y} coordinates.
The coordinates should specify the position in pixels of the
top left corner of the window.
When the GUI window has not been opened yet, the values are
remembered until the window is opened.  The position is
adjusted to make the window fit on the screen (if possible).

### <a id=":win :winsize E465" class="section-title" href="#:win :winsize E465">Note:</a>
:win[size] {width} {height}
Set the window height to {width} by {height} characters.
Obsolete, use ":set lines=11 columns=22".


## <a id="gui-scrollbars" class="section-title" href="#gui-scrollbars">Scrollbars</a> 

There are vertical scrollbars and a horizontal scrollbar.  You may
configure which ones appear with the 'guioptions' option.

The interface looks like this (with ":set guioptions=mlrb"):

+------------------------------+ `
[ File  Edit		 Help ](# File  Edit		 Help ) <- Menu bar (m) `
+-+--------------------------+-+ `
[^|			    |^](#^|			    |^) `
[#| Text area.		    |#](##| Text area.		    |#) `
[ |			    | ](# |			    | ) `
[v|__________________________|v](#v|__________________________|v) `
Normal status line -> [-+ File.c	       5,2  +-](#-+ File.c	       5,2  +-) `
between Vim windows   [^|""""""""""""""""""""""""""|^](#^|""""""""""""""""""""""""""|^) `
[ |			    | ](# |			    | ) `
[ | Another file buffer.     | ](# | Another file buffer.     | ) `
[ |			    | ](# |			    | ) `
[#|			    |#](##|			    |#) `
Left scrollbar (l) -> [#|			    |#](##|			    |#) <- Right `
[#|			    |#](##|			    |#)    scrollbar (r) `
[ |			    | ](# |			    | ) `
[v|			    |v](#v|			    |v) `
+-+--------------------------+-+ `
[ |< ####		   >| ](# |< ####		   >| ) <- Bottom `
+-+--------------------------+-+    scrollbar (b) `

Any of the scrollbar or menu components may be turned off by not putting the
appropriate letter in the 'guioptions' string.  The bottom scrollbar is
only useful when 'nowrap' is set.


### <a id="gui-vert-scroll" class="section-title" href="#gui-vert-scroll">Vertical Scrollbars</a>

Each Vim window has a scrollbar next to it which may be scrolled up and down
to move through the text in that buffer.  The size of the scrollbar-thumb
indicates the fraction of the buffer which can be seen in the window.
When the scrollbar is dragged all the way down, the last line of the file
will appear in the top of the window.

If a window is shrunk to zero height (by the growth of another window) its
scrollbar disappears.  It reappears when the window is restored.

If a window is vertically split, it will get a scrollbar when it is the
current window and when, taking the middle of the current window and drawing a
vertical line, this line goes through the window.
When there are scrollbars on both sides, and the middle of the current window
is on the left half, the right scrollbar column will contain scrollbars for
the rightmost windows.  The same happens on the other side.


### <a id="gui-horiz-scroll" class="section-title" href="#gui-horiz-scroll">Horizontal Scrollbars</a>

The horizontal scrollbar (at the bottom of the Vim GUI) may be used to
scroll text sideways when the 'wrap' option is turned off.  The
scrollbar-thumb size is such that the text of the longest visible line may be
scrolled as far as possible left and right.  The cursor is moved when
necessary, it must remain on a visible character (unless 'virtualedit' is
set).

Computing the length of the longest visible line takes quite a bit of
computation, and it has to be done every time something changes.  If this
takes too much time or you don't like the cursor jumping to another line,
include the 'h' flag in 'guioptions'.  Then the scrolling is limited by the
text of the current cursor line.


## <a id="drag-n-drop" class="section-title" href="#drag-n-drop">Drag and Drop</a> 

You can drag and drop one or more files into the Vim window, where they will
be opened as if a [:drop](#:drop) command was used.

If you hold down Shift while doing this, Vim changes to the first dropped
file's directory.  If you hold Ctrl Vim will always split a new window for the
file.  Otherwise it's only done if the current buffer has been changed.

You can also drop a directory on Vim.  This starts the explorer plugin for
that directory (assuming it was enabled, otherwise you'll get an error
message).  Keep Shift pressed to change to the directory instead.

If Vim happens to be editing a command line, the names of the dropped files
and directories will be inserted at the cursor.  This allows you to use these
names with any Ex command.  Special characters (space, tab, double quote and
'|'; backslash on non-MS-Windows systems) will be escaped.


## <a id="menus" class="section-title" href="#menus">Menus</a> 

For an introduction see [usr_42.txt](#usr_42.txt) in the user manual.


### <a id="using-menus" class="section-title" href="#using-menus">Using Menus</a>

Basically, menus can be used just like mappings.  You can define your own
menus, as many as you like.
Long-time Vim users won't use menus much.  But the power is in adding your own
menus and menu items.  They are most useful for things that you can't remember
what the key sequence was.

For creating menus in a different language, see [:menutrans](#:menutrans).
If you don't want to use menus at all, see ['go-M'](#'go-M').

### <a id="menu.vim" class="section-title" href="#menu.vim">Note:</a>
The default menus are read from the file "$VIMRUNTIME/menu.vim".  See
[$VIMRUNTIME](#$VIMRUNTIME) for where the path comes from.  You can set up your own menus.
Starting off with the default set is a good idea.  You can add more items, or,
if you don't like the defaults at all, start with removing all menus
[:unmenu-all](#:unmenu-all).  You can also avoid the default menus being loaded by adding
this line to your vimrc file (NOT your gvimrc file!):
```
:let did_install_default_menus = 1
If you also want to avoid the Syntax menu:
```
:let did_install_syntax_menu = 1
The first item in the Syntax menu can be used to show all available filetypes
in the menu (which can take a bit of time to load).  If you want to have all
filetypes already present at startup, add:
```
:let do_syntax_sel_menu = 1

Note that the menu.vim is sourced when `:syntax on` or `:filetype on` is
executed or after your .vimrc file is sourced.  This means that the 'encoding'
option and the language of messages (`:language messages`) must be set before
that (if you want to change them).

### <a id="console-menus" class="section-title" href="#console-menus">Note:</a>
Although this documentation is in the GUI section, you can actually use menus
in console mode too.  You will have to load [menu.vim](#menu.vim) explicitly then, it is
not done by default.  You can use the [:emenu](#:emenu) command and command-line
completion with 'wildmenu' to access the menu entries almost like a real menu
system.  To do this, put these commands in your vimrc file:
```
:source $VIMRUNTIME/menu.vim
:set wildmenu
:set cpo-=<
:set wcm=<C-Z>
:map <F4> :emenu <C-Z>
Pressing <F4> will start the menu.  You can now use the cursor keys to select
a menu entry.  Hit <Enter> to execute it.  Hit <Esc> if you want to cancel.

### <a id="creating-menus" class="section-title" href="#creating-menus">Creating New Menus</a>

### <a id=":me" class="section-title" href="#:me">Note:</a>
### <a id="E330 E327 E331 E336 E333" class="section-title" href="#E330 E327 E331 E336 E333">Note:</a>
### <a id="E328 E329 E337 E792" class="section-title" href="#E328 E329 E337 E792">Note:</a>
To create a new menu item, use the ":menu" commands.  They are mostly like
the ":map" set of commands (see [map-modes](#map-modes)), but the first argument is a menu
item name, given as a path of menus and submenus with a '.' between them,
e.g.:
```

:menu File.Save  :w<CR>
:inoremenu File.Save  <C-O>:w<CR>
:menu Edit.Big\ Changes.Delete\ All\ Spaces  :%s/[ ^I]//g<CR>

This last one will create a new item in the menu bar called "Edit", holding
the mouse button down on this will pop up a menu containing the item
"Big Changes", which is a sub-menu containing the item "Delete All Spaces",
which when selected, performs the operation.

To create a menu for terminal mode, use [:tlmenu| instead of |:tmenu](#:tlmenu| instead of |:tmenu) unlike
key mapping ([:tmap|). This is because |:tmenu](#:tmap|). This is because |:tmenu) is already used for defining
tooltips for menus. See [terminal-input](#terminal-input).

Special characters in a menu name:

### <a id="menu-shortcut" class="section-title" href="#menu-shortcut">Note:</a>
&	The next character is the shortcut key.  Make sure each
shortcut key is only used once in a (sub)menu.  If you want to
insert a literal "&" in the menu name use "&&".
### <a id="menu-text" class="section-title" href="#menu-text">Note:</a>

```
Tab>	Separates the menu name from right-aligned text.  This can be
used to show the equivalent typed command.  The text "<Tab>"
can be used here for convenience.  If you are using a real
tab, don't forget to put a backslash before it!
Example:
```

:amenu &File.&Open<Tab>:e  :browse e<CR>

[typed literally]
With the shortcut "F" (while keeping the <Alt> key pressed), and then "O",
this menu can be used.  The second part is shown as "Open     :e".  The ":e"
is right aligned, and the "O" is underlined, to indicate it is the shortcut.

### <a id=":am" class="section-title" href="#:am">Note:</a>
The ":amenu" command can be used to define menu entries for all modes at once,
expect for Terminal mode.  To make the command work correctly, a character is
automatically inserted for some modes:
mode		inserted	appended	~
Normal		nothing		nothing
Visual		<C-C>		<C-\><C-G>
Insert		<C-\><C-O>
Cmdline		<C-C>		<C-\><C-G>
Op-pending	<C-C>		<C-\><C-G>

Example:
```

:amenu File.Next	:next^M

is equal to:
```

:nmenu File.Next	:next^M
:vmenu File.Next	^C:next^M^\^G
:imenu File.Next	^\^O:next^M
:cmenu File.Next	^C:next^M^\^G
:omenu File.Next	^C:next^M^\^G

Careful: In Insert mode this only works for a SINGLE Normal mode command,
because of the CTRL-O.  If you have two or more commands, you will need to use
the ":imenu" command.  For inserting text in any mode, you can use the
expression register:
```

:amenu Insert.foobar   "='foobar'<CR>P

The special text <Cmd> begins a "command menu", it executes the command
directly without changing modes.  Where you might use ":...<CR>" you can
instead use "<Cmd>...<CR>".  See [<Cmd>](#<Cmd>) for more info.  Example:
```
anoremenu File.Next <Cmd>next<CR>

Note that <Esc> in Cmdline mode executes the command, like in a mapping.  This
is Vi compatible.  Use CTRL-C to quit Cmdline mode.

### <a id=":nme :nmenu" class="section-title" href="#:nme :nmenu">Note:</a>
Menu commands starting with "n" work in Normal mode. [mapmode-n](#mapmode-n)

### <a id=":ome :omenu" class="section-title" href="#:ome :omenu">Note:</a>
Menu commands starting with "o" work in Operator-pending mode. [mapmode-o](#mapmode-o)

### <a id=":vme :vmenu" class="section-title" href="#:vme :vmenu">Note:</a>
Menu commands starting with "v" work in Visual mode. [mapmode-v](#mapmode-v)

### <a id=":xme :xmenu" class="section-title" href="#:xme :xmenu">Note:</a>
Menu commands starting with "x" work in Visual and Select mode. [mapmode-x](#mapmode-x)

### <a id=":sme :smenu" class="section-title" href="#:sme :smenu">Note:</a>
Menu commands starting with "s" work in Select mode. [mapmode-s](#mapmode-s)

### <a id=":ime :imenu" class="section-title" href="#:ime :imenu">Note:</a>
Menu commands starting with "i" work in Insert mode. [mapmode-i](#mapmode-i)

### <a id=":cme :cmenu" class="section-title" href="#:cme :cmenu">Note:</a>
Menu commands starting with "c" work in Cmdline mode. [mapmode-c](#mapmode-c)

### <a id=":tlm :tlmenu :tln" class="section-title" href="#:tlm :tlmenu :tln">Note:</a>
Menu commands starting with "tl" work in Terminal mode. [mapmode-t](#mapmode-t)

### <a id=":menu-<silent> :menu-silent" class="section-title" href="#:menu-<silent> :menu-silent">Note:</a>
To define a menu which will not be echoed on the command line, add
"<silent>" as the first argument.  Example:
```
:menu <silent> Settings.Ignore\ case  :set ic<CR>
The ":set ic" will not be echoed when using this menu.  Messages from the
executed command are still given though.  To shut them up too, add a ":silent"
in the executed command:
```
:menu <silent> Search.Header :exe ":silent normal /Header\r"<CR>
"<silent>" may also appear just after "<script>".

### <a id=":menu-<script> :menu-script" class="section-title" href="#:menu-<script> :menu-script">Note:</a>
The "to" part of the menu will be inspected for mappings.  If you don't want
this, use the ":noremenu" command (or the similar one for a specific mode).
If you do want to use script-local mappings, add "<script>" as the very first
argument to the ":menu" command or just after "<silent>".

### <a id="menu-priority" class="section-title" href="#menu-priority">Note:</a>
You can give a priority to a menu.  Menus with a higher priority go more to
the right.  The priority is given as a number before the ":menu" command.
Example:
```
:80menu Buffer.next :bn<CR>

The default menus have these priorities:
File		10
Edit		20
Tools		40
Syntax		50
Buffers		60
Window		70
Help		9999

When no or zero priority is given, 500 is used.
The priority for the PopUp menu is not used.

You can use a priority higher than 9999, to make it go after the Help menu,
but that is non-standard and is discouraged.  The highest possible priority is
about 32000.  The lowest is 1.

### <a id="sub-menu-priority" class="section-title" href="#sub-menu-priority">Note:</a>
The same mechanism can be used to position a sub-menu.  The priority is then
given as a dot-separated list of priorities, before the menu name:
```
:menu 80.500 Buffer.next :bn<CR>
Giving the sub-menu priority is only needed when the item is not to be put
in a normal position.  For example, to put a sub-menu before the other items:
```
:menu 80.100 Buffer.first :brew<CR>
Or to put a sub-menu after the other items, and further items with default
priority will be put before it:
```
:menu 80.900 Buffer.last :blast<CR>
When a number is missing, the default value 500 will be used:
```
:menu .900 myMenu.test :echo "text"<CR>
The menu priority is only used when creating a new menu.  When it already
existed, e.g., in another mode, the priority will not change.  Thus, the
priority only needs to be given the first time a menu is used.
An exception is the PopUp menu.  There is a separate menu for each mode
(Normal, Op-pending, Visual, Insert, Cmdline).  The order in each of these
menus can be different.  This is different from menu-bar menus, which have
the same order for all modes.
NOTE: sub-menu priorities currently don't work for all versions of the GUI.

### <a id="menu-separator E332" class="section-title" href="#menu-separator E332">Note:</a>
Menu items can be separated by a special item that inserts some space between
items.  Depending on the system this is displayed as a line or a dotted line.
These items must start with a '-' and end in a '-'.  The part in between is
used to give it a unique name.  Priorities can be used as with normal items.
Example:
```
:menu Example.item1	:do something
:menu Example.-Sep-	:
:menu Example.item2	:do something different
Note that the separator also requires a rhs.  It doesn't matter what it is,
because the item will never be selected.  Use a single colon to keep it
simple.

### <a id="gui-toolbar" class="section-title" href="#gui-toolbar">Note:</a>
The default toolbar is setup in menu.vim.  The display of the toolbar is
controlled by the 'guioptions' letter 'T'.  You can thus have menu & toolbar
together, or either on its own, or neither.  The appearance is controlled by
the 'toolbar' option.  You can choose between an image, text or both.

### <a id="toolbar-icon" class="section-title" href="#toolbar-icon">Note:</a>
The toolbar is defined as a special menu called ToolBar, which only has one
level.  Vim interprets the items in this menu as follows:
1)  If an "icon=" argument was specified, the file with this name is used.
The file can either be specified with the full path or with the base name.
In the last case it is searched for in the "bitmaps" directory in
'runtimepath', like in point 3.  Examples:
```
:amenu icon=/usr/local/pixmaps/foo_icon.xpm ToolBar.Foo :echo "Foo"<CR>
:amenu icon=FooIcon ToolBar.Foo :echo "Foo"<CR>

```
   Note that in the first case the extension is included, while in the second
case it is omitted.
If the file cannot be opened the next points are tried.
A space in the file name must be escaped with a backslash.
A menu priority must come _after_ the icon argument:
```
:amenu icon=foo 1.42 ToolBar.Foo :echo "42!"<CR>
2)  An item called 'BuiltIn##', where ## is a number, is taken as number ## of
the built-in bitmaps available in Vim.  Currently there are 31 numbered
from 0 to 30 which cover most common editing operations [builtin-tools](#builtin-tools).
```
:amenu ToolBar.BuiltIn22 :call SearchNext("back")<CR>
3)  An item with another name is first searched for in the directory
"bitmaps" in 'runtimepath'.  If found, the bitmap file is used as the
toolbar button image.  Note that the exact filename is OS-specific: For
example, under Win32 the command
```
:amenu ToolBar.Hello :echo "hello"<CR>

```
   would find the file 'hello.bmp'.  Under X11 it is 'Hello.xpm'.
For MS-Windows and the bitmap is scaled to fit the button.  For
MS-Windows a size of 18 by 18 pixels works best.
For MS-Windows the bitmap should have 16 colors with the standard palette.
The light grey pixels will be changed to the Window frame color and the
dark grey pixels to the window shadow color.  More colors might also work,
depending on your system.
4)  If the bitmap is still not found, Vim checks for a match against its list
of built-in names.  Each built-in button image has a name.
So the command
```
:amenu ToolBar.Open :e

```
   will show the built-in "open a file" button image if no open.bmp exists.
All the built-in names can be seen used in menu.vim.
5)  If all else fails, a blank, but functioning, button is displayed.

### <a id="builtin-tools" class="section-title" href="#builtin-tools">Note:</a>
nr  Name		Normal action  ~
00  New			open new window
01  Open		browse for file to open in current window
02  Save		write buffer to file
03  Undo		undo last change
04  Redo		redo last undone change
05  Cut			delete selected text to clipboard
06  Copy		copy selected text to clipboard
07  Paste		paste text from clipboard
08  Print		print current buffer
09  Help		open a buffer on Vim's builtin help
10  Find		start a search command
11  SaveAll		write all modified buffers to file
12  SaveSesn		write session file for current situation
13  NewSesn		write new session file
14  LoadSesn		load session file
15  RunScript		browse for file to run as a Vim script
16  Replace		prompt for substitute command
17  WinClose		close current window
18  WinMax		make current window use many lines
19  WinMin		make current window use few lines
20  WinSplit		split current window
21  Shell		start a shell
22  FindPrev		search again, backward
23  FindNext		search again, forward
24  FindHelp		prompt for word to search help for
25  Make		run make and jump to first error
26  TagJump		jump to tag under the cursor
27  RunCtags		build tags for files in current directory
28  WinVSplit		split current window vertically
29  WinMaxWidth		make current window use many columns
30  WinMinWidth		make current window use few columns

### <a id="hidden-menus win32-hidden-menus" class="section-title" href="#hidden-menus win32-hidden-menus">Note:</a>
In the Win32 GUI, starting a menu name with ']' excludes that menu from the
main menu bar.  You must then use the [:popup](#:popup) command to display it.

When splitting the window the window toolbar is not copied to the new window.

### <a id="popup-menu" class="section-title" href="#popup-menu">Note:</a>
You can define the special menu "PopUp".  This is the menu that is displayed
when the right mouse button is pressed, if 'mousemodel' is set to popup or
popup_setpos.

The default "PopUp" menu is:
```
aunmenu PopUp
vnoremenu PopUp.Cut                         "+x
vnoremenu PopUp.Copy                        "+y
anoremenu PopUp.Paste                       "+gP
vnoremenu PopUp.Paste                       "+P
vnoremenu PopUp.Delete                      "_x
nnoremenu PopUp.Select\ All>                ggVG
vnoremenu PopUp.Select\ All>                gg0oG$
inoremenu PopUp.Select\ All                 <C-Home><C-O>VG
anoremenu PopUp.-1-                         <Nop>
anoremenu PopUp.How-to\ disable\ mouse      <Cmd>help disable-mouse<CR>

```


### <a id="showing-menus" class="section-title" href="#showing-menus">Showing What Menus Are Mapped To</a>

To see what an existing menu is mapped to, use just one argument after the
menu commands (just like you would with the ":map" commands).  If the menu
specified is a submenu, then all menus under that hierarchy will be shown.
If no argument is given after :menu at all, then ALL menu items are shown
for the appropriate mode (e.g., Command-line mode for :cmenu).

Special characters in the list, just before the rhs:
*	The menu was defined with "nore" to disallow remapping.
&	The menu was defined with "<script>" to allow remapping script-local
mappings only.
s	The menu was defined with "<silent>" to avoid showing what it is
mapped to when triggered.
-	The menu was disabled.

Note that hitting <Tab> while entering a menu name after a menu command may
be used to complete the name of the menu item.


### <a id="execute-menus" class="section-title" href="#execute-menus">Executing Menus</a>

### <a id=":em" class="section-title" href="#:em">Note:</a>
:[range]em[enu] {menu}		Execute {menu} from the command line.
The default is to execute the Normal mode
menu.  If a range is specified, it executes
the Visual mode menu.
If used from <c-o>, it executes the
insert-mode menu Eg:
```
:emenu File.Exit

:[range]em[enu] {mode} {menu}	Like above, but execute the menu for {mode}:
'n': [:nmenu](#:nmenu)  Normal mode
'v': [:vmenu](#:vmenu)  Visual mode
's': [:smenu](#:smenu)  Select mode
'o': [:omenu](#:omenu)  Operator-pending mode
't': [:tlmenu](#:tlmenu) Terminal mode
'i': [:imenu](#:imenu)  Insert mode
'c': [:cmenu](#:cmenu)  Cmdline mode


You can use :emenu to access useful menu items you may have got used to from
GUI mode.  See 'wildmenu' for an option that works well with this.  See
[console-menus](#console-menus) for an example.

When using a range, if the lines match with '<,'>, then the menu is executed
using the last visual selection.


### <a id="delete-menus" class="section-title" href="#delete-menus">Deleting Menus</a>

### <a id=":unme" class="section-title" href="#:unme">Note:</a>
### <a id=":aun" class="section-title" href="#:aun">Note:</a>
To delete a menu item or a whole submenu, use the unmenu commands, which are
analogous to the unmap commands.  Eg:
```
:unmenu! Edit.Paste

This will remove the Paste item from the Edit menu for Insert and
Command-line modes.

Note that hitting <Tab> while entering a menu name after an umenu command
may be used to complete the name of the menu item for the appropriate mode.

### <a id=":unmenu-all" class="section-title" href="#:unmenu-all">To remove all menus use:</a>
:unmenu *	" remove all menus in Normal and visual mode
:unmenu! *	" remove all menus in Insert and Command-line mode
:aunmenu *	" remove all menus in all modes, except for Terminal
" mode
:tlunmenu *	" remove all menus in Terminal mode

If you want to get rid of the menu bar:
```
:set guioptions-=m


### <a id="disable-menus" class="section-title" href="#disable-menus">Disabling Menus</a>

### <a id=":menu-disable :menu-enable" class="section-title" href="#:menu-disable :menu-enable">Note:</a>
If you do not want to remove a menu, but disable it for a moment, this can be
done by adding the "enable" or "disable" keyword to a ":menu" command.
Examples:
```
:menu disable &File.&Open\.\.\.
:amenu enable *
:amenu disable &Tools.*

The command applies to the modes as used with all menu commands.  Note that
characters like "&" need to be included for translated names to be found.
When the argument is "*", all menus are affected.  Otherwise the given menu
name and all existing submenus below it are affected.


### <a id="menu-examples" class="section-title" href="#menu-examples">Examples for Menus</a>

Here is an example on how to add menu items with menu's!  You can add a menu
item for the keyword under the cursor.  The register "z" is used.
```

:nmenu Words.Add\ Var		wb"zye:menu! Words.<C-R>z <C-R>z<CR>
:nmenu Words.Remove\ Var	wb"zye:unmenu! Words.<C-R>z<CR>
:vmenu Words.Add\ Var		"zy:menu! Words.<C-R>z <C-R>z <CR>
:vmenu Words.Remove\ Var	"zy:unmenu! Words.<C-R>z<CR>
:imenu Words.Add\ Var		<Esc>wb"zye:menu! Words.<C-R>z <C-R>z<CR>a
:imenu Words.Remove\ Var	<Esc>wb"zye:unmenu! Words.<C-R>z<CR>a

(the rhs is in <> notation, you can copy/paste this text to try out the
mappings, or put these lines in your gvimrc; "<C-R>" is CTRL-R, "<CR>" is
the <CR> key.  [<>](#<>))

### <a id="tooltips menu-tips" class="section-title" href="#tooltips menu-tips">Note:</a>
Tooltips & Menu tips

See section [42.4](#42.4) in the user manual.

### <a id=":tmenu" class="section-title" href="#:tmenu">Note:</a>
:tm[enu] {menupath} {rhs}	Define a tip for a menu or tool.  {only in
X11 and Win32 GUI}

:tm[enu] [menupath]		List menu tips. {only in X11 and Win32 GUI}

### <a id=":tunmenu" class="section-title" href="#:tunmenu">Note:</a>
:tu[nmenu] {menupath}		Remove a tip for a menu or tool.
{only in X11 and Win32 GUI}

Note: To create menus for terminal mode, use [:tlmenu](#:tlmenu) instead.

When a tip is defined for a menu item, it appears in the command-line area
when the mouse is over that item, much like a standard Windows menu hint in
the status bar.  (Except when Vim is in Command-line mode, when of course
nothing is displayed.)
When a tip is defined for a ToolBar item, it appears as a tooltip when the
mouse pauses over that button, in the usual fashion.  Use the [hl-Tooltip](#hl-Tooltip)
highlight group to change its colors.

A "tip" can be defined for each menu item.  For example, when defining a menu
item like this:
```
:amenu MyMenu.Hello :echo "Hello"<CR>
The tip is defined like this:
```
:tmenu MyMenu.Hello Displays a greeting.
And delete it with:
```
:tunmenu MyMenu.Hello

Tooltips are currently only supported for the X11 and Win32 GUI.  However, they
should appear for the other gui platforms in the not too distant future.

The ":tmenu" command works just like other menu commands, it uses the same
arguments.  ":tunmenu" deletes an existing menu tip, in the same way as the
other unmenu commands.

If a menu item becomes invalid (i.e. its actions in all modes are deleted) Vim
deletes the menu tip (and the item) for you.  This means that :aunmenu deletes
a menu item - you don't need to do a :tunmenu as well.


5.9 Popup Menus

You can cause a menu to popup at the cursor.  This behaves similarly to the
PopUp menus except that any menu tree can be popped up.

This command is for backwards compatibility, using it is discouraged, because
it behaves in a strange way.

### <a id=":popup :popu" class="section-title" href="#:popup :popu">Note:</a>
:popu[p] {name}			Popup the menu {name}.  The menu named must
have at least one subentry, but need not
appear on the menu-bar (see [hidden-menus](#hidden-menus)).

:popu[p]! {name}		Like above, but use the position of the mouse
pointer instead of the cursor.

Example:
```
:popup File
will make the "File" menu (if there is one) appear at the text cursor (mouse
pointer if ! was used).
```

:amenu ]Toolbar.Make	:make<CR>
:popup ]Toolbar
This creates a popup menu that doesn't exist on the main menu-bar.

Note that a menu that starts with ']' will not be displayed.


vim:tw=78:sw=4:ts=8:noet:ft=help:norl:


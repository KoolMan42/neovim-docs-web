---
title: Tree Sitter
description: Some page
layout: "@layouts/MainLayout.astro"
---


## <a id="Nvim" class="section-title" href="#Nvim"> Quickfix Txt</a> 

VIM REFERENCE MANUAL    by Bram Moolenaar


This subject is introduced in section [30.1](#30.1) of the user manual.

Type [gO](#gO) to see the table of contents.


## <a id="quickfix Quickfix E42" class="section-title" href="#quickfix Quickfix E42">1. Using QuickFix Commands</a> 

Vim has a special mode to speedup the edit-compile-edit cycle.  This is
inspired by the quickfix option of the Manx's Aztec C compiler on the Amiga.
The idea is to save the error messages from the compiler in a file and use Vim
to jump to the errors one by one.  You can examine each problem and fix it,
without having to remember all the error messages.

In Vim the quickfix commands are used more generally to find a list of
positions in files.  For example, [:vimgrep](#:vimgrep) finds pattern matches.  You can
use the positions in a script with the [getqflist()](#getqflist()) function.  Thus you can
do a lot more than the edit/compile/fix cycle!

If you have the error messages in a file you can start Vim with:
```
vim -q filename

From inside Vim an easy way to run a command and handle the output is with the
[:make](#:make) command (see below).

The 'errorformat' option should be set to match the error messages from your
compiler (see [errorformat](#errorformat) below).

### <a id="quickfix-ID" class="section-title" href="#quickfix-ID">Note:</a>
Each quickfix list has a unique identifier called the quickfix ID and this
number will not change within a Vim session. The [getqflist()](#getqflist()) function can be
used to get the identifier assigned to a list. There is also a quickfix list
number which may change whenever more than ten lists are added to a quickfix
stack.

### <a id="location-list E776" class="section-title" href="#location-list E776">Note:</a>
A location list is a window-local quickfix list. You get one after commands
like `:lvimgrep`, `:lgrep`, `:lhelpgrep`, `:lmake`, etc., which create a
location list instead of a quickfix list as the corresponding `:vimgrep`,
`:grep`, `:helpgrep`, `:make` do.
### <a id="location-list-file-window" class="section-title" href="#location-list-file-window">Note:</a>
A location list is associated with a window and each window can have a
separate location list.  A location list can be associated with only one
window.  The location list is independent of the quickfix list.

When a window with a location list is split, the new window gets a copy of the
location list.  When there are no longer any references to a location list,
the location list is destroyed.

### <a id="quickfix-changedtick" class="section-title" href="#quickfix-changedtick">Note:</a>
Every quickfix and location list has a read-only changedtick variable that
tracks the total number of changes made to the list.  Every time the quickfix
list is modified, this count is incremented. This can be used to perform an
action only when the list has changed.  The [getqflist()| and |getloclist()](#getqflist()| and |getloclist())
functions can be used to query the current value of changedtick.  You cannot
change the changedtick variable.

The following quickfix commands can be used.  The location list commands are
similar to the quickfix commands, replacing the 'c' prefix in the quickfix
command with 'l'.

### <a id="E924" class="section-title" href="#E924">Note:</a>
If the current window was closed by an [autocommand](#autocommand) while processing a
location list command, it will be aborted.

### <a id="E925 E926" class="section-title" href="#E925 E926">Note:</a>
If the current quickfix or location list was changed by an [autocommand](#autocommand) while
processing a quickfix or location list command, it will be aborted.

### <a id=":cc" class="section-title" href="#:cc">Note:</a>
:cc[!] [nr]		Display error [nr].  If [nr] is omitted, the same
:[nr]cc[!]		error is displayed again.  Without [!] this doesn't
work when jumping to another buffer, the current buffer
has been changed, there is the only window for the
buffer and both 'hidden' and 'autowrite' are off.
When jumping to another buffer with [!] any changes to
the current buffer are lost, unless 'hidden' is set or
there is another window for this buffer.
The 'switchbuf' settings are respected when jumping
to a buffer.
When used in the quickfix window the line number can
be used, including "." for the current line and "$"
for the last line.

### <a id=":ll" class="section-title" href="#:ll">Note:</a>
:ll[!] [nr]		Same as ":cc", except the location list for the
:[nr]ll[!]		current window is used instead of the quickfix list.

### <a id=":cn :cne :cnext E553" class="section-title" href="#:cn :cne :cnext E553">Note:</a>
:[count]cn[ext][!]	Display the [count] next error in the list that
includes a file name.  If there are no file names at
all, go to the [count] next error.  See [:cc](#:cc) for
[!] and 'switchbuf'.

### <a id=":lne :lnext" class="section-title" href="#:lne :lnext">Note:</a>
:[count]lne[xt][!]	Same as ":cnext", except the location list for the
current window is used instead of the quickfix list.

### <a id=":cp :cprevious" class="section-title" href="#:cp :cprevious">:[count]cN[ext][!]</a>
:[count]cp[revious][!]	Display the [count] previous error in the list that
includes a file name.  If there are no file names at
all, go to the [count] previous error.  See [:cc](#:cc) for
[!] and 'switchbuf'.


### <a id=":lp :lprevious :lprev :lN :lNext" class="section-title" href="#:lp :lprevious :lprev :lN :lNext">:[count]lN[ext][!]</a>
:[count]lp[revious][!]	Same as ":cNext" and ":cprevious", except the location
list for the current window is used instead of the
quickfix list.

### <a id=":cabo :cabove" class="section-title" href="#:cabo :cabove">Note:</a>
:[count]cabo[ve]	Go to the [count] error above the current line in the
current buffer.  If [count] is omitted, then 1 is
used.  If there are no errors, then an error message
is displayed.  Assumes that the entries in a quickfix
list are sorted by their buffer number and line
number. If there are multiple errors on the same line,
then only the first entry is used.  If [count] exceeds
the number of entries above the current line, then the
first error in the file is selected.

### <a id=":lab :labove" class="section-title" href="#:lab :labove">Note:</a>
:[count]lab[ove]	Same as ":cabove", except the location list for the
current window is used instead of the quickfix list.

### <a id=":cbel :cbelow" class="section-title" href="#:cbel :cbelow">Note:</a>
:[count]cbel[ow]	Go to the [count] error below the current line in the
current buffer.  If [count] is omitted, then 1 is
used.  If there are no errors, then an error message
is displayed.  Assumes that the entries in a quickfix
list are sorted by their buffer number and line
number.  If there are multiple errors on the same
line, then only the first entry is used.  If [count]
exceeds the number of entries below the current line,
then the last error in the file is selected.

### <a id=":lbel :lbelow" class="section-title" href="#:lbel :lbelow">Note:</a>
:[count]lbel[ow]	Same as ":cbelow", except the location list for the
current window is used instead of the quickfix list.

### <a id=":cbe :cbefore" class="section-title" href="#:cbe :cbefore">Note:</a>
:[count]cbe[fore]	Go to the [count] error before the current cursor
position in the current buffer.  If [count] is
omitted, then 1 is used.  If there are no errors, then
an error message is displayed.  Assumes that the
entries in a quickfix list are sorted by their buffer,
line and column numbers.  If [count] exceeds the
number of entries before the current position, then
the first error in the file is selected.

### <a id=":lbe :lbefore" class="section-title" href="#:lbe :lbefore">Note:</a>
:[count]lbe[fore]	Same as ":cbefore", except the location list for the
current window is used instead of the quickfix list.

### <a id=":caf :cafter" class="section-title" href="#:caf :cafter">Note:</a>
:[count]caf[ter]	Go to the [count] error after the current cursor
position in the current buffer.  If [count] is
omitted, then 1 is used.  If there are no errors, then
an error message is displayed.  Assumes that the
entries in a quickfix list are sorted by their buffer,
line and column numbers.  If [count] exceeds the
number of entries after the current position, then
the last error in the file is selected.

### <a id=":laf :lafter" class="section-title" href="#:laf :lafter">Note:</a>
:[count]laf[ter]	Same as ":cafter", except the location list for the
current window is used instead of the quickfix list.

### <a id=":cnf :cnfile" class="section-title" href="#:cnf :cnfile">Note:</a>
:[count]cnf[ile][!]	Display the first error in the [count] next file in
the list that includes a file name.  If there are no
file names at all or if there is no next file, go to
the [count] next error.  See [:cc](#:cc) for [!] and
'switchbuf'.

### <a id=":lnf :lnfile" class="section-title" href="#:lnf :lnfile">Note:</a>
:[count]lnf[ile][!]	Same as ":cnfile", except the location list for the
current window is used instead of the quickfix list.

### <a id=":cpf :cpfile :cNf :cNfile" class="section-title" href="#:cpf :cpfile :cNf :cNfile">:[count]cNf[ile][!]</a>
:[count]cpf[ile][!]	Display the last error in the [count] previous file in
the list that includes a file name.  If there are no
file names at all or if there is no next file, go to
the [count] previous error.  See [:cc](#:cc) for [!] and
'switchbuf'.


### <a id=":lpf :lpfile :lNf :lNfile" class="section-title" href="#:lpf :lpfile :lNf :lNfile">:[count]lNf[ile][!]</a>
:[count]lpf[ile][!]	Same as ":cNfile" and ":cpfile", except the location
list for the current window is used instead of the
quickfix list.

### <a id=":crewind :cr" class="section-title" href="#:crewind :cr">Note:</a>
:cr[ewind][!] [nr]	Display error [nr].  If [nr] is omitted, the FIRST
error is displayed.  See [:cc](#:cc).

### <a id=":lrewind :lr" class="section-title" href="#:lrewind :lr">Note:</a>
:lr[ewind][!] [nr]	Same as ":crewind", except the location list for the
current window is used instead of the quickfix list.

### <a id=":cfirst :cfir" class="section-title" href="#:cfirst :cfir">Note:</a>
:cfir[st][!] [nr]	Same as ":crewind".

### <a id=":lfirst :lfir" class="section-title" href="#:lfirst :lfir">Note:</a>
:lfir[st][!] [nr]	Same as ":lrewind".

### <a id=":clast :cla" class="section-title" href="#:clast :cla">Note:</a>
:cla[st][!] [nr]	Display error [nr].  If [nr] is omitted, the LAST
error is displayed.  See [:cc](#:cc).

### <a id=":llast :lla" class="section-title" href="#:llast :lla">Note:</a>
:lla[st][!] [nr]	Same as ":clast", except the location list for the
current window is used instead of the quickfix list.

### <a id=":cq :cquit" class="section-title" href="#:cq :cquit">Note:</a>
:cq[uit][!]
:{N}cq[uit][!]
:cq[uit][!] {N}		Quit Vim with error code {N}.  {N} defaults to one.
Useful when Vim is called from another program:
e.g., a compiler will not compile the same file again,
`git commit` will abort the committing process, `fc`
(built-in for shells like bash and zsh) will not
execute the command, etc.
{N} can also be zero, in which case Vim exits
normally.
WARNING: All changes in files are lost.  It works like
":qall!" [:qall](#:qall), except that Nvim exits non-zero or
[count].

### <a id=":cf :cfi :cfile" class="section-title" href="#:cf :cfi :cfile">Note:</a>
:cf[ile][!] [errorfile]	Read the error file and jump to the first error.
This is done automatically when Vim is started with
the -q option.  You can use this command when you
keep Vim running while compiling.  If you give the
name of the errorfile, the 'errorfile' option will
be set to [errorfile].  See [:cc](#:cc) for [!].
If the encoding of the error file differs from the
'encoding' option, you can use the 'makeencoding'
option to specify the encoding.

### <a id=":lf :lfi :lfile" class="section-title" href="#:lf :lfi :lfile">Note:</a>
:lf[ile][!] [errorfile]	Same as ":cfile", except the location list for the
current window is used instead of the quickfix list.
You can not use the -q command-line option to set
the location list.


### <a id=":cg :cgetfile" class="section-title" href="#:cg :cgetfile">:cg[etfile] [errorfile]</a>
Read the error file.  Just like ":cfile" but don't
jump to the first error.
If the encoding of the error file differs from the
'encoding' option, you can use the 'makeencoding'
option to specify the encoding.


### <a id=":lg :lge :lgetfile" class="section-title" href="#:lg :lge :lgetfile">:lg[etfile] [errorfile]</a>
Same as ":cgetfile", except the location list for the
current window is used instead of the quickfix list.

### <a id=":caddf :caddfile" class="section-title" href="#:caddf :caddfile">Note:</a>
:caddf[ile] [errorfile]	Read the error file and add the errors from the
errorfile to the current quickfix list. If a quickfix
list is not present, then a new list is created.
If the encoding of the error file differs from the
'encoding' option, you can use the 'makeencoding'
option to specify the encoding.

### <a id=":laddf :laddfile" class="section-title" href="#:laddf :laddfile">Note:</a>
:laddf[ile] [errorfile]	Same as ":caddfile", except the location list for the
current window is used instead of the quickfix list.

### <a id=":cb :cbuffer E681" class="section-title" href="#:cb :cbuffer E681">Note:</a>
:cb[uffer][!] [bufnr]	Read the error list from the current buffer.
When [bufnr] is given it must be the number of a
loaded buffer.  That buffer will then be used instead
of the current buffer.
A range can be specified for the lines to be used.
Otherwise all lines in the buffer are used.
See [:cc](#:cc) for [!].

### <a id=":lb :lbuffer" class="section-title" href="#:lb :lbuffer">Note:</a>
:lb[uffer][!] [bufnr]	Same as ":cbuffer", except the location list for the
current window is used instead of the quickfix list.

### <a id=":cgetb :cgetbuffer" class="section-title" href="#:cgetb :cgetbuffer">Note:</a>
:cgetb[uffer] [bufnr]	Read the error list from the current buffer.  Just
like ":cbuffer" but don't jump to the first error.

### <a id=":lgetb :lgetbuffer" class="section-title" href="#:lgetb :lgetbuffer">Note:</a>
:lgetb[uffer] [bufnr]	Same as ":cgetbuffer", except the location list for
the current window is used instead of the quickfix
list.

### <a id=":cad :cadd :caddbuffer" class="section-title" href="#:cad :cadd :caddbuffer">Note:</a>
:cad[dbuffer] [bufnr]	Read the error list from the current buffer and add
the errors to the current quickfix list.  If a
quickfix list is not present, then a new list is
created. Otherwise, same as ":cbuffer".

### <a id=":laddb :laddbuffer" class="section-title" href="#:laddb :laddbuffer">Note:</a>
:laddb[uffer] [bufnr]	Same as ":caddbuffer", except the location list for
the current window is used instead of the quickfix
list.

### <a id=":cex :cexpr E777" class="section-title" href="#:cex :cexpr E777">Note:</a>
:cex[pr][!] {expr}	Create a quickfix list using the result of {expr} and
jump to the first error.
If {expr} is a String, then each newline terminated
line in the String is processed using the global value
of 'errorformat' and the result is added to the
quickfix list.
If {expr} is a List, then each String item in the list
is processed and added to the quickfix list.  Non
String items in the List are ignored.
See [:cc](#:cc) for [!].
Examples:
```
### <a id=":cexpr system('grep -n xyz ')" class="section-title" href="#:cexpr system('grep -n xyz ')">Note:</a>
:cexpr getline(1, '$')

```

### <a id=":lex :lexpr" class="section-title" href="#:lex :lexpr">Note:</a>
:lex[pr][!] {expr}	Same as [:cexpr](#:cexpr), except the location list for the
current window is used instead of the quickfix list.

### <a id=":cgete :cgetexpr" class="section-title" href="#:cgete :cgetexpr">Note:</a>
:cgete[xpr] {expr}	Create a quickfix list using the result of {expr}.
Just like [:cexpr](#:cexpr), but don't jump to the first error.

### <a id=":lgete :lgetexpr" class="section-title" href="#:lgete :lgetexpr">Note:</a>
:lgete[xpr] {expr}	Same as [:cgetexpr](#:cgetexpr), except the location list for the
current window is used instead of the quickfix list.

### <a id=":cadde :caddexpr" class="section-title" href="#:cadde :caddexpr">Note:</a>
:cadde[xpr] {expr}	Evaluate {expr} and add the resulting lines to the
current quickfix list. If a quickfix list is not
present, then a new list is created. The current
cursor position will not be changed. See [:cexpr](#:cexpr) for
more information.
Example:
```
:g/mypattern/caddexpr expand("%") .. ":" .. line(".") ..  ":" .. getline(".")

```

### <a id=":lad :addd :laddexpr" class="section-title" href="#:lad :addd :laddexpr">Note:</a>
:lad[dexpr] {expr}	Same as ":caddexpr", except the location list for the
current window is used instead of the quickfix list.

### <a id=":cl :clist" class="section-title" href="#:cl :clist">Note:</a>
:cl[ist] [from] [, [to]]
List all errors that are valid [quickfix-valid](#quickfix-valid).
If numbers [from] and/or [to] are given, the respective
range of errors is listed.  A negative number counts
from the last error backwards, -1 being the last error.
The 'switchbuf' settings are respected when jumping
to a buffer.
The [:filter](#:filter) command can be used to display only the
quickfix entries matching a supplied pattern. The
pattern is matched against the filename, module name,
pattern and text of the entry.

:cl[ist] +{count}	List the current and next {count} valid errors.  This
is similar to ":clist from from+count", where "from"
is the current error position.

:cl[ist]! [from] [, [to]]
List all errors.

:cl[ist]! +{count}	List the current and next {count} error lines.  This
is useful to see unrecognized lines after the current
one.  For example, if ":clist" shows:
8384 testje.java:252: error: cannot find symbol ~
Then using ":cl! +3" shows the reason:
8384 testje.java:252: error: cannot find symbol ~
8385:   ZexitCode = Fmainx(); ~
8386:               ^ ~
8387:   symbol:   method Fmainx() ~

### <a id=":lli :llist" class="section-title" href="#:lli :llist">:lli[st] [from] [, [to]]</a>
Same as ":clist", except the location list for the
current window is used instead of the quickfix list.

:lli[st]! [from] [, [to]]
List all the entries in the location list for the
current window.

If you insert or delete lines, mostly the correct error location is still
found because hidden marks are used.  Sometimes, when the mark has been
deleted for some reason, the message "line changed" is shown to warn you that
the error location may not be correct.  If you quit Vim and start again the
marks are lost and the error locations may not be correct anymore.

Two autocommands are available for running commands before and after a
quickfix command (':make', ':grep' and so on) is executed. See
[QuickFixCmdPre| and |QuickFixCmdPost](#QuickFixCmdPre| and |QuickFixCmdPost) for details.

### <a id="QuickFixCmdPost-example" class="section-title" href="#QuickFixCmdPost-example">Note:</a>
When 'encoding' differs from the locale, the error messages may have a
different encoding from what Vim is using.  To convert the messages you can
use this code:
```
function QfMakeConv()
let qflist = getqflist()
for i in qflist
let i.text = iconv(i.text, "cp936", "utf-8")
endfor
call setqflist(qflist)
endfunction

au QuickfixCmdPost make call QfMakeConv()
Another option is using 'makeencoding'.

### <a id="quickfix-title" class="section-title" href="#quickfix-title">Note:</a>
Every quickfix and location list has a title. By default the title is set to
the command that created the list. The [getqflist()| and |getloclist()](#getqflist()| and |getloclist())
functions can be used to get the title of a quickfix and a location list
respectively. The [setqflist()| and |setloclist()](#setqflist()| and |setloclist()) functions can be used to
modify the title of a quickfix and location list respectively. Examples:
```
call setqflist([], 'a', {'title' : 'Cmd output'})
echo getqflist({'title' : 1})
call setloclist(3, [], 'a', {'title' : 'Cmd output'})
echo getloclist(3, {'title' : 1})

```

### <a id="quickfix-index" class="section-title" href="#quickfix-index">Note:</a>
When you jump to a quickfix/location list entry using any of the quickfix
commands (e.g. [:cc|, |:cnext|, |:cprev](#:cc|, |:cnext|, |:cprev), etc.), that entry becomes the
currently selected entry. The index of the currently selected entry in a
quickfix/location list can be obtained using the getqflist()/getloclist()
functions. Examples:
```
echo getqflist({'idx' : 0}).idx
echo getqflist({'id' : qfid, 'idx' : 0}).idx
echo getloclist(2, {'idx' : 0}).idx

```

For a new quickfix list, the first entry is selected and the index is 1.  Any
entry in any quickfix/location list can be set as the currently selected entry
using the setqflist() function. Examples:
```
call setqflist([], 'a', {'idx' : 12})
call setqflist([], 'a', {'id' : qfid, 'idx' : 7})
call setloclist(1, [], 'a', {'idx' : 7})

```

### <a id="quickfix-size" class="section-title" href="#quickfix-size">Note:</a>
You can get the number of entries (size) in a quickfix and a location list
using the [getqflist()| and |getloclist()](#getqflist()| and |getloclist()) functions respectively. Examples:
```
echo getqflist({'size' : 1})
echo getloclist(5, {'size' : 1})

```

### <a id="quickfix-context" class="section-title" href="#quickfix-context">Note:</a>
Any Vim type can be associated as a context with a quickfix or location list.
The [setqflist()| and the |setloclist()](#setqflist()| and the |setloclist()) functions can be used to associate a
context with a quickfix and a location list respectively. The [getqflist()](#getqflist())
and the [getloclist()](#getloclist()) functions can be used to retrieve the context of a
quickfix and a location list respectively. This is useful for a Vim plugin
dealing with multiple quickfix/location lists.
Examples:
```

let somectx = {'name' : 'Vim', 'type' : 'Editor'}
call setqflist([], 'a', {'context' : somectx})
echo getqflist({'context' : 1})

let newctx = ['red', 'green', 'blue']
call setloclist(2, [], 'a', {'id' : qfid, 'context' : newctx})
echo getloclist(2, {'id' : qfid, 'context' : 1})

```

### <a id="quickfix-parse" class="section-title" href="#quickfix-parse">Note:</a>
You can parse a list of lines using 'errorformat' without creating or
modifying a quickfix list using the [getqflist()](#getqflist()) function. Examples:
```
echo getqflist({'lines' : ["F1:10:Line10", "F2:20:Line20"]})
echo getqflist({'lines' : systemlist('grep -Hn quickfix *')})
This returns a dictionary where the "items" key contains the list of quickfix
entries parsed from lines. The following shows how to use a custom
'errorformat' to parse the lines without modifying the 'errorformat' option:
```
echo getqflist({'efm' : '%f#%l#%m', 'lines' : ['F1#10#Line']})

```


EXECUTE A COMMAND IN ALL THE BUFFERS IN QUICKFIX OR LOCATION LIST:
### <a id=":cdo" class="section-title" href="#:cdo">Note:</a>
:cdo[!] {cmd}		Execute {cmd} in each valid entry in the quickfix list.
It works like doing this:
```
:cfirst
:{cmd}
:cnext
:{cmd}
etc.

```
			When the current file can't be [abandon](#abandon)ed and the [!]
is not present, the command fails.
When going to the next entry fails execution stops.
The last buffer (or where an error occurred) becomes
the current buffer.
{cmd} can contain '|' to concatenate several commands.

Only valid entries in the quickfix list are used.
A range can be used to select entries, e.g.:
```
:10,$cdo cmd

```
			To skip entries 1 to 9.

Note: While this command is executing, the Syntax
autocommand event is disabled by adding it to
'eventignore'.  This considerably speeds up editing
each buffer.
Also see [:bufdo|, |:tabdo|, |:argdo|, |:windo](#:bufdo|, |:tabdo|, |:argdo|, |:windo),
[:ldo|, |:cfdo| and |:lfdo](#:ldo|, |:cfdo| and |:lfdo).

### <a id=":cfdo" class="section-title" href="#:cfdo">Note:</a>
:cfdo[!] {cmd}		Execute {cmd} in each file in the quickfix list.
It works like doing this:
```
:cfirst
:{cmd}
:cnfile
:{cmd}
etc.

```
			Otherwise it works the same as `:cdo`.

### <a id=":ldo" class="section-title" href="#:ldo">Note:</a>
:ld[o][!] {cmd}		Execute {cmd} in each valid entry in the location list
for the current window.
It works like doing this:
```
:lfirst
:{cmd}
:lnext
:{cmd}
etc.

```
			Only valid entries in the location list are used.
Otherwise it works the same as `:cdo`.

### <a id=":lfdo" class="section-title" href="#:lfdo">Note:</a>
:lfdo[!] {cmd}		Execute {cmd} in each file in the location list for
the current window.
It works like doing this:
```
:lfirst
:{cmd}
:lnfile
:{cmd}
etc.

```
			Otherwise it works the same as `:ldo`.

FILTERING A QUICKFIX OR LOCATION LIST:
### <a id="cfilter-plugin :Cfilter :Lfilter" class="section-title" href="#cfilter-plugin :Cfilter :Lfilter">Note:</a>
If you have too many entries in a quickfix list, you can use the cfilter
plugin to reduce the number of entries.  Load the plugin with:
```

packadd cfilter

Then you can use the following commands to filter a quickfix/location list:
```

:Cfilter[!] /{pat}/
:Lfilter[!] /{pat}/

The [:Cfilter](#:Cfilter) command creates a new quickfix list from the entries matching
{pat} in the current quickfix list. {pat} is a Vim [regular-expression](#regular-expression)
pattern. Both the file name and the text of the entries are matched against
{pat}. If the optional ! is supplied, then the entries not matching {pat} are
used. The pattern can be optionally enclosed using one of the following
characters: ', ", /. If the pattern is empty, then the last used search
pattern is used.

The [:Lfilter| command does the same as |:Cfilter](#:Lfilter| command does the same as |:Cfilter) but operates on the current
location list.

The current quickfix/location list is not modified by these commands, so you
can go back to the unfiltered list using the [:colder|/|:lolder](#:colder|/|:lolder) command.


## <a id="quickfix-window" class="section-title" href="#quickfix-window">2. the Error Window</a> 

### <a id=":cope :copen w:quickfix_title" class="section-title" href="#:cope :copen w:quickfix_title">Note:</a>
:cope[n] [height]	Open a window to show the current list of errors.

When [height] is given, the window becomes that high
(if there is room).  When [height] is omitted the
window is made ten lines high.

If there already is a quickfix window, it will be made
the current window.  It is not possible to open a
second quickfix window.  If [height] is given the
existing window will be resized to it.

### <a id="quickfix-buffer" class="section-title" href="#quickfix-buffer">Note:</a>
The window will contain a special buffer, with
'buftype' equal to "quickfix".  Don't change this!
The window will have the w:quickfix_title variable set
which will indicate the command that produced the
quickfix list. This can be used to compose a custom
status line if the value of 'statusline' is adjusted
properly. Whenever this buffer is modified by a
quickfix command or function, the [b:changedtick](#b:changedtick)
variable is incremented.  You can get the number of
this buffer using the getqflist() and getloclist()
functions by passing the "qfbufnr" item. For a
location list, this buffer is wiped out when the
location list is removed.

### <a id=":lop :lopen" class="section-title" href="#:lop :lopen">Note:</a>
:lop[en] [height]	Open a window to show the location list for the
current window. Works only when the location list for
the current window is present.  You can have more than
one location window opened at a time.  Otherwise, it
acts the same as ":copen".

### <a id=":ccl :cclose" class="section-title" href="#:ccl :cclose">Note:</a>
:ccl[ose]		Close the quickfix window.

### <a id=":lcl :lclose" class="section-title" href="#:lcl :lclose">Note:</a>
:lcl[ose]		Close the window showing the location list for the
current window.

### <a id=":cw :cwindow" class="section-title" href="#:cw :cwindow">Note:</a>
:cw[indow] [height]	Open the quickfix window when there are recognized
errors.  If the window is already open and there are
no recognized errors, close the window.

### <a id=":lw :lwindow" class="section-title" href="#:lw :lwindow">Note:</a>
:lw[indow] [height]	Same as ":cwindow", except use the window showing the
location list for the current window.

### <a id=":cbo :cbottom" class="section-title" href="#:cbo :cbottom">Note:</a>
:cbo[ttom]		Put the cursor in the last line of the quickfix window
and scroll to make it visible.  This is useful for
when errors are added by an asynchronous callback.
Only call it once in a while if there are many
updates to avoid a lot of redrawing.

### <a id=":lbo :lbottom" class="section-title" href="#:lbo :lbottom">Note:</a>
:lbo[ttom]		Same as ":cbottom", except use the window showing the
location list for the current window.

Normally the quickfix window is at the bottom of the screen.  If there are
vertical splits, it's at the bottom of the rightmost column of windows.  To
make it always occupy the full width:
```
:botright cwindow
You can move the window around with [window-moving](#window-moving) commands.
For example, to move it to the top: CTRL-W K
The 'winfixheight' option will be set, which means that the window will mostly
keep its height, ignoring 'winheight' and 'equalalways'.  You can change the
height manually (e.g., by dragging the status line above it with the mouse).

In the quickfix window, each line is one error.  The line number is equal to
the error number.  The current entry is highlighted with the QuickFixLine
highlighting.  You can change it to your liking, e.g.:
```
:hi QuickFixLine ctermbg=Yellow guibg=Yellow

You can use ":.cc" to jump to the error under the cursor.
Hitting the <Enter> key or double-clicking the mouse on a line has the same
effect.  The file containing the error is opened in the window above the
quickfix window.  If there already is a window for that file, it is used
instead.  If the buffer in the used window has changed, and the error is in
another file, jumping to the error will fail.  You will first have to make
sure the window contains a buffer which can be abandoned.

When you select a file from the quickfix window, the following steps are used
to find a window to edit the file:

1. If a window displaying the selected file is present in the current tabpage
(starting with the window before the quickfix window), then that window is
used.
2. If the above step fails and if 'switchbuf' contains "usetab" and a window
displaying the selected file is present in any one of the tabpages
(starting with the first tabpage) then that window is used.
3. If the above step fails then a window in the current tabpage displaying a
buffer with 'buftype' not set (starting with the window before the quickfix
window) is used.
4. If the above step fails and if 'switchbuf' contains "uselast", then the
previously accessed window is used.
5. If the above step fails then the window before the quickfix window is used.
If there is no previous window, then the window after the quickfix window
is used.
6. If the above step fails, then a new horizontally split window above the
quickfix window is used.

### <a id="CTRL-W_<Enter> CTRL-W_<CR>" class="section-title" href="#CTRL-W_<Enter> CTRL-W_<CR>">Note:</a>
You can use CTRL-W <Enter> to open a new window and jump to the error there.

When the quickfix window has been filled, two autocommand events are
triggered.  First the 'filetype' option is set to "qf", which triggers the
FileType event (also see [qf.vim](#qf.vim)).  Then the BufReadPost event is triggered,
using "quickfix" for the buffer name.  This can be used to perform some action
on the listed errors.  Example:
```
au BufReadPost quickfix  setlocal modifiable
\ | silent exe 'g/^/s//\=line(".") .. " "/'
\ | setlocal nomodifiable
This prepends the line number to each line.  Note the use of "\=" in the
substitute string of the ":s" command, which is used to evaluate an
expression.
The BufWinEnter event is also triggered, again using "quickfix" for the buffer
name.

Note: When adding to an existing quickfix list the autocommand are not
triggered.

Note: Making changes in the quickfix window has no effect on the list of
errors.  'modifiable' is off to avoid making changes.  If you delete or insert
lines anyway, the relation between the text and the error number is messed up.
If you really want to do this, you could write the contents of the quickfix
window to a file and use ":cfile" to have it parsed and used as the new error
list.

### <a id="location-list-window" class="section-title" href="#location-list-window">Note:</a>
The location list window displays the entries in a location list.  When you
open a location list window, it is created below the current window and
displays the location list for the current window.  The location list window
is similar to the quickfix window, except that you can have more than one
location list window open at a time. When you use a location list command in
this window, the displayed location list is used.

When you select a file from the location list window, the following steps are
used to find a window to edit the file:

1. If a non-quickfix window associated with the location list is present in
the current tabpage, then that window is used.
2. If the above step fails and if the file is already opened in another window
in the current tabpage, then that window is used.
3. If the above step fails and 'switchbuf' contains "usetab" and if the file
is opened in a window in any one of the tabpages, then that window is used.
4. If the above step fails then a window in the current tabpage showing a
buffer with 'buftype' not set is used.
5. If the above step fails, then the file is edited in a new window.

In all of the above cases, if the location list for the selected window is not
yet set, then it is set to the location list displayed in the location list
window.

### <a id="quickfix-window-ID" class="section-title" href="#quickfix-window-ID">Note:</a>
You can use the [getqflist()| and |getloclist()](#getqflist()| and |getloclist()) functions to obtain the
window ID of the quickfix window and location list window respectively (if
present).  Examples:
```
echo getqflist({'winid' : 1}).winid
echo getloclist(2, {'winid' : 1}).winid

```

### <a id="getqflist-examples" class="section-title" href="#getqflist-examples">Note:</a>
The [getqflist()| and |getloclist()](#getqflist()| and |getloclist()) functions can be used to get the various
attributes of a quickfix and location list respectively. Some examples for
using these functions are below:
```
" get the title of the current quickfix list
:echo getqflist({'title' : 0}).title

" get the identifier of the current quickfix list
:let qfid = getqflist({'id' : 0}).id

" get the identifier of the fourth quickfix list in the stack
:let qfid = getqflist({'nr' : 4, 'id' : 0}).id

" check whether a quickfix list with a specific identifier exists
:if getqflist({'id' : qfid}).id == qfid

" get the index of the current quickfix list in the stack
:let qfnum = getqflist({'nr' : 0}).nr

" get the items of a quickfix list specified by an identifier
:echo getqflist({'id' : qfid, 'items' : 0}).items

" get the number of entries in a quickfix list specified by an id
:echo getqflist({'id' : qfid, 'size' : 0}).size

" get the context of the third quickfix list in the stack
:echo getqflist({'nr' : 3, 'context' : 0}).context

" get the number of quickfix lists in the stack
:echo getqflist({'nr' : '$'}).nr

" get the number of times the current quickfix list is changed
:echo getqflist({'changedtick' : 0}).changedtick

" get the current entry in a quickfix list specified by an identifier
:echo getqflist({'id' : qfid, 'idx' : 0}).idx

" get all the quickfix list attributes using an identifier
:echo getqflist({'id' : qfid, 'all' : 0})

" parse text from a List of lines and return a quickfix list
:let myList = ["a.java:10:L10", "b.java:20:L20"]
:echo getqflist({'lines' : myList}).items

" parse text using a custom 'efm' and return a quickfix list
:echo getqflist({'lines' : ['a.c#10#Line 10'], 'efm':'%f#%l#%m'}).items

" get the quickfix list window id
:echo getqflist({'winid' : 0}).winid

" get the quickfix list window buffer number
:echo getqflist({'qfbufnr' : 0}).qfbufnr

" get the context of the current location list
:echo getloclist(0, {'context' : 0}).context

" get the location list window id of the third window
:echo getloclist(3, {'winid' : 0}).winid

" get the location list window buffer number of the third window
:echo getloclist(3, {'qfbufnr' : 0}).qfbufnr

" get the file window id of a location list window (winnr: 4)
:echo getloclist(4, {'filewinid' : 0}).filewinid

```

### <a id="setqflist-examples" class="section-title" href="#setqflist-examples">Note:</a>
The [setqflist()| and |setloclist()](#setqflist()| and |setloclist()) functions can be used to set the various
attributes of a quickfix and location list respectively. Some examples for
using these functions are below:
```
" create an empty quickfix list with a title and a context
:let t = 'Search results'
:let c = {'cmd' : 'grep'}
:call setqflist([], ' ', {'title' : t, 'context' : c})

" set the title of the current quickfix list
:call setqflist([], 'a', {'title' : 'Mytitle'})

" change the current entry in the list specified by an identifier
:call setqflist([], 'a', {'id' : qfid, 'idx' : 10})

" set the context of a quickfix list specified by an identifier
:call setqflist([], 'a', {'id' : qfid, 'context' : {'val' : 100}})

" create a new quickfix list from a command output
### <a id=":call setqflist([], ' ', {'lines' : systemlist('grep -Hn main .c')})" class="section-title" href="#:call setqflist([], ' ', {'lines' : systemlist('grep -Hn main .c')})">Note:</a>

" parse text using a custom efm and add to a particular quickfix list
:call setqflist([], 'a', {'id' : qfid,
\ 'lines' : ["a.c#10#L10", "b.c#20#L20"], 'efm':'%f#%l#%m'})

" add items to the quickfix list specified by an identifier
:let newItems = [{'filename' : 'a.txt', 'lnum' : 10, 'text' : "Apple"},
\ {'filename' : 'b.txt', 'lnum' : 20, 'text' : "Orange"}]
:call setqflist([], 'a', {'id' : qfid, 'items' : newItems})

" empty a quickfix list specified by an identifier
:call setqflist([], 'r', {'id' : qfid, 'items' : []})

" free all the quickfix lists in the stack
:call setqflist([], 'f')

" set the title of the fourth quickfix list
:call setqflist([], 'a', {'nr' : 4, 'title' : 'SomeTitle'})

" create a new quickfix list at the end of the stack
:call setqflist([], ' ', {'nr' : '$',
### <a id="\ 'lines' : systemlist('grep -Hn class .java')})" class="section-title" href="#\ 'lines' : systemlist('grep -Hn class .java')})">Note:</a>

" create a new location list from a command output
### <a id=":call setloclist(0, [], ' ', {'lines' : systemlist('grep -Hn main .c')})" class="section-title" href="#:call setloclist(0, [], ' ', {'lines' : systemlist('grep -Hn main .c')})">Note:</a>

" replace the location list entries for the third window
:call setloclist(3, [], 'r', {'items' : newItems})

```



## <a id="quickfix-error-lists" class="section-title" href="#quickfix-error-lists">3. Using More Than One List of Errors</a> 

So far has been assumed that there is only one list of errors.  Actually the
ten last used lists are remembered.  When starting a new list, the previous
ones are automatically kept.  Two commands can be used to access older error
lists.  They set one of the existing error lists as the current one.

### <a id=":colder :col E380" class="section-title" href="#:colder :col E380">Note:</a>
:col[der] [count]	Go to older error list.  When [count] is given, do
this [count] times.  When already at the oldest error
list, an error message is given.

### <a id=":lolder :lol" class="section-title" href="#:lolder :lol">Note:</a>
:lol[der] [count]	Same as `:colder`, except use the location list for
the current window instead of the quickfix list.

### <a id=":cnewer :cnew E381" class="section-title" href="#:cnewer :cnew E381">Note:</a>
:cnew[er] [count]	Go to newer error list.  When [count] is given, do
this [count] times.  When already at the newest error
list, an error message is given.

### <a id=":lnewer :lnew" class="section-title" href="#:lnewer :lnew">Note:</a>
:lnew[er] [count]	Same as `:cnewer`, except use the location list for
the current window instead of the quickfix list.

### <a id=":chistory :chi" class="section-title" href="#:chistory :chi">Note:</a>
:[count]chi[story]	Show the list of error lists.  The current list is
marked with ">".  The output looks like:
error list 1 of 3; 43 errors   :make  ~
> error list 2 of 3; 0 errors    :helpgrep tag  ~
error list 3 of 3; 15 errors   :grep ex_help *.c ~

When [count] is given, then the count'th quickfix
list is made the current list. Example:
```
" Make the 4th quickfix list current
:4chistory

```

### <a id=":lhistory :lhi" class="section-title" href="#:lhistory :lhi">Note:</a>
:[count]lhi[story]	Show the list of location lists, otherwise like
`:chistory`.

When adding a new error list, it becomes the current list.

When ":colder" has been used and ":make" or ":grep" is used to add a new error
list, one newer list is overwritten.  This is especially useful if you are
browsing with ":grep" [grep](#grep).  If you want to keep the more recent error
lists, use ":cnewer 99" first.

To get the number of lists in the quickfix and location list stack, you can
use the [getqflist()| and |getloclist()](#getqflist()| and |getloclist()) functions respectively with the list
number set to the special value '$'. Examples:
```
echo getqflist({'nr' : '$'}).nr
echo getloclist(3, {'nr' : '$'}).nr
To get the number of the current list in the stack:
```
echo getqflist({'nr' : 0}).nr

```



## <a id=":make_makeprg" class="section-title" href="#:make_makeprg">4. Using :Make</a> 

### <a id=":mak :make" class="section-title" href="#:mak :make">Note:</a>
:mak[e][!] [arguments]	1. All relevant [QuickFixCmdPre](#QuickFixCmdPre) autocommands are
executed.
2. If the 'autowrite' option is on, write any changed
buffers
3. An errorfile name is made from 'makeef'.  If
'makeef' doesn't contain "##", and a file with this
name already exists, it is deleted.
4. The program given with the 'makeprg' option is
started (default "make") with the optional
[arguments] and the output is saved in the
errorfile (for Unix it is also echoed on the
screen).
5. The errorfile is read using 'errorformat'.
6. All relevant [QuickFixCmdPost](#QuickFixCmdPost) autocommands are
executed.  See example below.
7. If [!] is not given the first error is jumped to.
8. The errorfile is deleted.
9. You can now move through the errors with commands
like [:cnext| and |:cprevious](#:cnext| and |:cprevious), see above.
This command does not accept a comment, any "
characters are considered part of the arguments.
If the encoding of the program output differs from the
'encoding' option, you can use the 'makeencoding'
option to specify the encoding.

### <a id=":lmak :lmake" class="section-title" href="#:lmak :lmake">Note:</a>
:lmak[e][!] [arguments]
Same as ":make", except the location list for the
current window is used instead of the quickfix list.

The ":make" command executes the command given with the 'makeprg' option.
This is done by passing the command to the shell given with the 'shell'
option.  This works almost like typing

":!{makeprg} [arguments] {shellpipe} {errorfile}".

{makeprg} is the string given with the 'makeprg' option.  Any command can be
used, not just "make".  Characters '%' and '#' are expanded as usual on a
command-line.  You can use "%<" to insert the current file name without
extension, or "#<" to insert the alternate file name without extension, for
example:
```
:set makeprg=make\ #<.o

[arguments] is anything that is typed after ":make".
{shellpipe} is the 'shellpipe' option.
{errorfile} is the 'makeef' option, with ## replaced to make it unique.

The placeholder "$*" can be used for the argument list in {makeprg} if the
### <a id="The $ is" class="section-title" href="#The $ is">command needs some additional characters after its arguments.</a>
replaced then by all arguments.  Example:
```
### <a id=":set makeprg=latex\ \\\\nonstopmode\ \\\\input\\{$}" class="section-title" href="#:set makeprg=latex\ \\\\nonstopmode\ \\\\input\\{$}">Note:</a>
or simpler
```
### <a id=":let &mp = 'latex \\nonstopmode \\input\{$}'" class="section-title" href="#:let &mp = 'latex \\nonstopmode \\input\{$}'">Note:</a>
"$*" can be given multiple times, for example:
```
### <a id=":set makeprg=gcc\ -o\ $\ $" class="section-title" href="#:set makeprg=gcc\ -o\ $\ $">Note:</a>

The 'shellpipe' option defaults to ">%s 2>&1" for Win32.
This means that the output of the compiler is saved in a file and not shown on
the screen directly.  For Unix "| tee" is used.  The compiler output is shown
on the screen and saved in a file the same time.  Depending on the shell used
"[& tee" or "2>&1](#& tee" or "2>&1) tee" is the default, so stderr output will be included.

If 'shellpipe' is empty, the {errorfile} part will be omitted.  This is useful
for compilers that write to an errorfile themselves.


Using QuickFixCmdPost to fix the encoding ~

It may be that 'encoding' is set to an encoding that differs from the messages
your build program produces.  This example shows how to fix this after Vim has
read the error messages:
```

function QfMakeConv()
let qflist = getqflist()
for i in qflist
let i.text = iconv(i.text, "cp936", "utf-8")
endfor
call setqflist(qflist)
endfunction

au QuickfixCmdPost make call QfMakeConv()

(Example by Faque Cheng)
Another option is using 'makeencoding'.


## <a id="grep lid" class="section-title" href="#grep lid">5. Using :Vimgrep and :Grep</a> 

Vim has two ways to find matches for a pattern: Internal and external.  The
advantage of the internal grep is that it works on all systems and uses the
powerful Vim search patterns.  An external grep program can be used when the
Vim grep does not do what you want.

The internal method will be slower, because files are read into memory.  The
advantages are:
- Line separators and encoding are automatically recognized, as if a file is
being edited.
- Uses Vim search patterns.  Multi-line patterns can be used.
- When plugins are enabled: compressed and remote files can be searched.
[gzip| |netrw](#gzip| |netrw)

To be able to do this Vim loads each file as if it is being edited.  When
there is no match in the file the associated buffer is wiped out again.  The
'hidden' option is ignored here to avoid running out of memory or file
descriptors when searching many files.  However, when the [:hide](#:hide) command
modifier is used the buffers are kept loaded.  This makes following searches
in the same files a lot faster.

Note that [:copen| (or |:lopen| for |:lgrep](#:copen| (or |:lopen| for |:lgrep)) may be used to open a buffer
containing the search results in linked form.  The [:silent](#:silent) command may be
used to suppress the default full screen grep output.  The ":grep!" form of
the [:grep](#:grep) command doesn't jump to the first match automatically.  These
commands can be combined to create a NewGrep command:
```

command! -nargs=+ NewGrep execute 'silent grep! <args>' | copen 42


5.1 using Vim's internal grep

### <a id=":vim :vimgrep E682 E683" class="section-title" href="#:vim :vimgrep E682 E683">Note:</a>
:vim[grep][!] /{pattern}/[g][j][f] {file} ...
Search for {pattern} in the files {file} ... and set
the error list to the matches.  Files matching
'wildignore' are ignored; files in 'suffixes' are
searched last.

{pattern} is a Vim search pattern.  Instead of
enclosing it in / any non-ID character (see
['isident'](#'isident')) can be used, so long as it does not
appear in {pattern}.
'ignorecase' applies.  To overrule it put [/\c](#/\c) in the
pattern to ignore case or [/\C](#/\C) to match case.
'smartcase' is not used.
If {pattern} is empty (e.g. // is specified), the last
used search pattern is used. [last-pattern](#last-pattern)

Flags:
'g'  Without the 'g' flag each line is added only
once.  With 'g' every match is added.

'j'  Without the 'j' flag Vim jumps to the first
match.  With 'j' only the quickfix list is
updated.  With the [!] any changes in the current
buffer are abandoned.

'f'  When the 'f' flag is specified, fuzzy string
matching is used to find matching lines. In this
case, {pattern} is treated as a literal string
instead of a regular expression.  See
[fuzzy-matching](#fuzzy-matching) for more information about fuzzy
matching strings.

[QuickFixCmdPre| and |QuickFixCmdPost](#QuickFixCmdPre| and |QuickFixCmdPost) are triggered.
A file that is opened for matching may use a buffer
number, but it is reused if possible to avoid
consuming buffer numbers.

:{count}vim[grep] ...
When a number is put before the command this is used
as the maximum number of matches to find.  Use
":1vimgrep pattern file" to find only the first.
Useful if you only want to check if there is a match
and quit quickly when it's found.

Every second or so the searched file name is displayed
to give you an idea of the progress made.
Examples:
```
### <a id=":vimgrep /an error/ .c" class="section-title" href="#:vimgrep /an error/ .c">Note:</a>
### <a id=":vimgrep /\<FileName\>/ .h include/" class="section-title" href="#:vimgrep /\<FileName\>/ .h include/">Note:</a>
### <a id=":vimgrep /myfunc/ /.c" class="section-title" href="#:vimgrep /myfunc/ /.c">Note:</a>
### <a id="For the use of "" see [starstar-wildcard|." class="section-title" href="#For the use of "" see |starstar-wildcard](#starstar-wildcard|." class="section-title" href="#For the use of "" see |starstar-wildcard)."><</a>

:vim[grep][!] {pattern} {file} ...
Like above, but instead of enclosing the pattern in a
non-ID character use a white-separated pattern.  The
pattern must start with an ID character.
Example:
```
### <a id=":vimgrep Error .c" class="section-title" href="#:vimgrep Error .c">Note:</a>

```

### <a id=":lv :lvimgrep" class="section-title" href="#:lv :lvimgrep">Note:</a>
:lv[imgrep][!] /{pattern}/[g][j][f] {file} ...
:lv[imgrep][!] {pattern} {file} ...
Same as ":vimgrep", except the location list for the
current window is used instead of the quickfix list.

### <a id=":vimgrepa :vimgrepadd" class="section-title" href="#:vimgrepa :vimgrepadd">Note:</a>
:vimgrepa[dd][!] /{pattern}/[g][j][f] {file} ...
:vimgrepa[dd][!] {pattern} {file} ...
Just like ":vimgrep", but instead of making a new list
of errors the matches are appended to the current
list.

### <a id=":lvimgrepa :lvimgrepadd" class="section-title" href="#:lvimgrepa :lvimgrepadd">Note:</a>
:lvimgrepa[dd][!] /{pattern}/[g][j][f] {file} ...
:lvimgrepa[dd][!] {pattern} {file} ...
Same as ":vimgrepadd", except the location list for
the current window is used instead of the quickfix
list.

5.2 External grep

Vim can interface with "grep" and grep-like programs (such as the GNU
id-utils) in a similar way to its compiler integration (see [:make](#:make) above).

[Unix trivia: The name for the Unix "grep" command comes from ":g/re/p", where
"re" stands for Regular Expression.]

### <a id=":gr :grep" class="section-title" href="#:gr :grep">Note:</a>
:gr[ep][!] [arguments]	Just like ":make", but use 'grepprg' instead of
'makeprg' and 'grepformat' instead of 'errorformat'.
When 'grepprg' is "internal" this works like
[:vimgrep](#:vimgrep).  Note that the pattern needs to be
enclosed in separator characters then.
If the encoding of the program output differs from the
'encoding' option, you can use the 'makeencoding'
option to specify the encoding.

### <a id=":lgr :lgrep" class="section-title" href="#:lgr :lgrep">Note:</a>
:lgr[ep][!] [arguments]	Same as ":grep", except the location list for the
current window is used instead of the quickfix list.

### <a id=":grepa :grepadd" class="section-title" href="#:grepa :grepadd">Note:</a>
:grepa[dd][!] [arguments]
Just like ":grep", but instead of making a new list of
errors the matches are appended to the current list.
Example:
```
:call setqflist([])
:bufdo grepadd! something %

```
			The first command makes a new error list which is
empty.  The second command executes "grepadd" for each
listed buffer.  Note the use of ! to avoid that
":grepadd" jumps to the first error, which is not
allowed with [:bufdo](#:bufdo).
An example that uses the argument list and avoids
errors for files without matches:
```
:silent argdo try
\ | grepadd! something %
\ | catch /E480:/
\ | endtry"

```

If the encoding of the program output differs from the
'encoding' option, you can use the 'makeencoding'
option to specify the encoding.

### <a id=":lgrepa :lgrepadd" class="section-title" href="#:lgrepa :lgrepadd">Note:</a>
:lgrepa[dd][!] [arguments]
Same as ":grepadd", except the location list for the
current window is used instead of the quickfix list.

5.3 Setting up external grep

If you have a standard "grep" program installed, the :grep command may work
well with the defaults.  The syntax is very similar to the standard command:
```

:grep foo *.c

Will search all files with the .c extension for the substring "foo".  The
arguments to :grep are passed straight to the "grep" program, so you can use
whatever options your "grep" supports.

By default, :grep invokes grep with the -n option (show file and line
numbers).  You can change this with the 'grepprg' option.  You will need to set
'grepprg' if:

a)	You are using a program that isn't called "grep"
b)	You have to call grep with a full path
c)	You want to pass other options automatically (e.g. case insensitive
search.)

Once "grep" has executed, Vim parses the results using the 'grepformat'
option.  This option works in the same way as the 'errorformat' option - see
that for details.  You may need to change 'grepformat' from the default if
your grep outputs in a non-standard format, or you are using some other
program with a special format.

Once the results are parsed, Vim loads the first file containing a match and
jumps to the appropriate line, in the same way that it jumps to a compiler
error in [quickfix| mode.  You can then use the |:cnext|, |:clist](#quickfix| mode.  You can then use the |:cnext|, |:clist), etc.
commands to see the other matches.


5.4 Using :grep with id-utils

You can set up :grep to work with the GNU id-utils like this:
```

:set grepprg=lid\ -Rgrep\ -s
:set grepformat=%f:%l:%m

then
```
:grep (regexp)

works just as you'd expect.
(provided you remembered to mkid first :)


5.5 Browsing source code with :vimgrep or :grep

Using the stack of error lists that Vim keeps, you can browse your files to
look for functions and the functions they call.  For example, suppose that you
have to add an argument to the read_file() function.  You enter this command:
```

:vimgrep /\<read_file\>/ *.c

You use ":cn" to go along the list of matches and add the argument.  At one
place you have to get the new argument from a higher level function msg(), and
need to change that one too.  Thus you use:
```

:vimgrep /\<msg\>/ *.c

While changing the msg() functions, you find another function that needs to
get the argument from a higher level.  You can again use ":vimgrep" to find
these functions.  Once you are finished with one function, you can use
```

:colder

to go back to the previous one.

This works like browsing a tree: ":vimgrep" goes one level deeper, creating a
list of branches.  ":colder" goes back to the previous level.  You can mix
this use of ":vimgrep" and "colder" to browse all the locations in a tree-like
way.  If you do this consistently, you will find all locations without the
need to write down a "todo" list.


## <a id="compiler-select" class="section-title" href="#compiler-select">6. Selecting a Compiler</a> 

### <a id=":comp :compiler E666" class="section-title" href="#:comp :compiler E666">Note:</a>
:comp[iler][!] {name}		Set options to work with compiler {name}.
Without the "!" options are set for the
current buffer.  With "!" global options are
set.
If you use ":compiler foo" in "file.foo" and
then ":compiler! bar" in another buffer, Vim
will keep on using "foo" in "file.foo".


The Vim plugins in the "compiler" directory will set options to use the
selected compiler.  For `:compiler` local options are set, for `:compiler!`
global options.
### <a id="current_compiler" class="section-title" href="#current_compiler">Note:</a>
To support older Vim versions, the plugins always use "current_compiler" and
not "b:current_compiler".  What the command actually does is the following:

- Delete the "current_compiler" and "b:current_compiler" variables.
- Define the "CompilerSet" user command.  With "!" it does ":set", without "!"
it does ":setlocal".
- Execute ":runtime! compiler/{name}.(vim|lua)".  The plugins are expected to
set options with "CompilerSet" and set the "current_compiler" variable to the
name of the compiler.
- Delete the "CompilerSet" user command.
- Set "b:current_compiler" to the value of "current_compiler".
- Without "!" the old value of "current_compiler" is restored.


For writing a compiler plugin, see [write-compiler-plugin](#write-compiler-plugin).


### <a id="quickfix-gcc	compiler-gcc" class="section-title" href="#quickfix-gcc	compiler-gcc">GCC</a>

There's one variable you can set for the GCC compiler:

g:compiler_gcc_ignore_unmatched_lines
Ignore lines that don't match any patterns
defined for GCC.  Useful if output from
commands run from make are generating false
positives.


### <a id="quickfix-perl compiler-perl" class="section-title" href="#quickfix-perl compiler-perl">PERL</a>

The Perl compiler plugin doesn't actually compile, but invokes Perl's internal
syntax checking feature and parses the output for possible errors so you can
correct them in quick-fix mode.

Warnings are forced regardless of "no warnings" or "$^W = 0" within the file
being checked.  To disable this set g:perl_compiler_force_warnings to a zero
value.  For example:
```
let g:perl_compiler_force_warnings = 0


### <a id="compiler-pyunit" class="section-title" href="#compiler-pyunit">Pyunit Compiler</a>

This is not actually a compiler, but a unit testing framework for the
Python language.  It is included into standard Python distribution
starting from version 2.0.  For older versions, you can get it from
https://pyunit.sourceforge.net.

When you run your tests with the help of the framework, possible errors
are parsed by Vim and presented for you in quick-fix mode.

Unfortunately, there is no standard way to run the tests.
The alltests.py script seems to be used quite often, that's all.
Useful values for the 'makeprg' options therefore are:
setlocal makeprg=./alltests.py " Run a testsuite
setlocal makeprg=python\ %:S   " Run a single testcase


### <a id="compiler-tex" class="section-title" href="#compiler-tex">Tex Compiler</a>

Included in the distribution compiler for TeX ($VIMRUNTIME/compiler/tex.vim)
uses make command if possible.  If the compiler finds a file named "Makefile"
or "makefile" in the current directory, it supposes that you want to process
your *TeX files with make, and the makefile does the right work.  In this case
compiler sets 'errorformat' for *TeX output and leaves 'makeprg' untouched.  If
neither "Makefile" nor "makefile" is found, the compiler will not use make.
You can force the compiler to ignore makefiles by defining
b:tex_ignore_makefile or g:tex_ignore_makefile variable (they are checked for
existence only).

If the compiler chose not to use make, it needs to choose a right program for
processing your input.  If b:tex_flavor or g:tex_flavor (in this precedence)
variable exists, it defines TeX flavor for :make (actually, this is the name
of executed command), and if both variables do not exist, it defaults to
"latex".  For example, while editing chapter2.tex \input-ed from mypaper.tex
written in AMS-TeX:
```

:let b:tex_flavor = 'amstex'
:compiler tex

```
	[editing...]
```
:make mypaper

Note that you must specify a name of the file to process as an argument (to
process the right file when editing \input-ed or \include-ed file; portable
solution for substituting % for no arguments is welcome).  This is not in the
semantics of make, where you specify a target, not source, but you may specify
filename without extension ".tex" and mean this as "make filename.dvi or
filename.pdf or filename.some_result_extension according to compiler".

Note: tex command line syntax is set to usable both for MikTeX (suggestion
by Srinath Avadhanula) and teTeX (checked by Artem Chuprina).  Suggestion
from [errorformat-LaTeX](#errorformat-LaTeX) is too complex to keep it working for different
shells and OSes and also does not allow to use other available TeX options,
if any.  If your TeX doesn't support "-interaction=nonstopmode", please
report it with different means to express \nonstopmode from the command line.


## <a id="error-file-format" class="section-title" href="#error-file-format">7. the Error Format</a> 

### <a id="errorformat E372 E373 E374" class="section-title" href="#errorformat E372 E373 E374">Note:</a>
### <a id="E375 E376 E377 E378" class="section-title" href="#E375 E376 E377 E378">Note:</a>
The 'errorformat' option specifies a list of formats that are recognized.  The
first format that matches with an error message is used.  You can add several
formats for different messages your compiler produces, or even entries for
multiple compilers.  See [efm-entries](#efm-entries).

Each entry in 'errorformat' is a scanf-like string that describes the format.
First, you need to know how scanf works.  Look in the documentation of your
C compiler.  Below you find the % items that Vim understands.  Others are
invalid.

Special characters in 'errorformat' are comma and backslash.  See
[efm-entries](#efm-entries) for how to deal with them.  Note that a literal "%" is matched
by "%%", thus it is not escaped with a backslash.
Keep in mind that in the `:make` and `:grep` output all NUL characters are
replaced with SOH (0x01).

Note: By default the difference between upper and lowercase is ignored.  If
you want to match case, add "\C" to the pattern [/\C](#/\C).

Vim will read lines of any length, but only the first 4095 bytes are used, the
rest is ignored.  Items can only be 1023 bytes long.


Basic items

%f		file name (finds a string)
%o		module name (finds a string)
%l		line number (finds a number)
%e		end line number (finds a number)
%c		column number (finds a number representing character
column of the error, byte index, a <tab> is 1
character column)
%v		virtual column number (finds a number representing
screen column of the error (1 <tab> == 8 screen
columns))
%k		end column number (finds a number representing
the character column of the error, byte index, or a
number representing screen end column of the error if
it's used with %v)
%t		error type (finds a single character):
e - error message
w - warning message
i - info message
n - note message
%n		error number (finds a number)
%m		error message (finds a string)
%r		matches the "rest" of a single-line file message %O/P/Q
%p		pointer line (finds a sequence of '-', '.', ' ' or
tabs and uses the length for the column number)
%*{conv}	any scanf non-assignable conversion
%%		the single '%' character
%s		search text (finds a string)

The "%f" conversion may depend on the current 'isfname' setting.  "~/" is
expanded to the home directory and environment variables are expanded.

The "%f" and "%m" conversions have to detect the end of the string.  This
normally happens by matching following characters and items.  When nothing is
following the rest of the line is matched.  If "%f" is followed by a '%' or a
backslash, it will look for a sequence of 'isfname' characters.

On Windows a leading "C:" will be included in "%f", even when using "%f:".
This means that a file name which is a single alphabetical letter will not be
detected.

The "%p" conversion is normally followed by a "^".  It's used for compilers
that output a line like:
```
^
or
```
---------^
to indicate the column of the error.  This is to be used in a multi-line error
message.  See [errorformat-javac](#errorformat-javac) for a  useful example.

The "%s" conversion specifies the text to search for, to locate the error line.
The text is used as a literal string.  The anchors "^" and "$" are added to
the text to locate the error line exactly matching the search text and the
text is prefixed with the "\V" atom to make it "very nomagic".  The "%s"
conversion can be used to locate lines without a line number in the error
output.  Like the output of the "grep" shell command.
When the pattern is present the line number will not be used.

The "%o" conversion specifies the module name in quickfix entry.  If present
it will be used in quickfix error window instead of the filename.  The module
name is used only for displaying purposes, the file name is used when jumping
to the file.

Changing directory

The following uppercase conversion characters specify the type of special
format strings.  At most one of them may be given as a prefix at the beginning
of a single comma-separated format pattern.
Some compilers produce messages that consist of directory names that have to
be prepended to each file name read by %f (example: GNU make).  The following
codes can be used to scan these directory names; they will be stored in an
### <a id="E379" class="section-title" href="#E379">internal directory stack.</a>
%D		"enter directory" format string; expects a following
%f that finds the directory name
%X		"leave directory" format string; expects following %f

When defining an "enter directory" or "leave directory" format, the "%D" or
"%X" has to be given at the start of that substring.  Vim tracks the directory
changes and prepends the current directory to each erroneous file found with a
relative path.  See [quickfix-directory-stack](#quickfix-directory-stack) for details, tips and
limitations.


### <a id="errorformat-multi-line" class="section-title" href="#errorformat-multi-line">Multi-line messages</a>

It is possible to read the output of programs that produce multi-line
messages, i.e. error strings that consume more than one line.  Possible
prefixes are:
%E		start of a multi-line error message
%W		start of a multi-line warning message
%I		start of a multi-line informational message
%N		start of a multi-line note message
%A		start of a multi-line message (unspecified type)
%>		for next line start with current pattern again [efm-%>](#efm-%>)
%C		continuation of a multi-line message
%Z		end of a multi-line message
These can be used with '+' and '-', see [efm-ignore](#efm-ignore) below.

Using "\n" in the pattern won't work to match multi-line messages.

Example: Your compiler happens to write out errors in the following format
(leading line numbers not being part of the actual output):

1	Error 275 ~
2	line 42 ~
3	column 3 ~
4	' ' expected after '--' ~

The appropriate error format string has to look like this:
```
:set efm=%EError\ %n,%Cline\ %l,%Ccolumn\ %c,%Z%m

And the [:clist](#:clist) error message generated for this error is:

1:42 col 3 error 275:  ' ' expected after '--'

Another example: Think of a Python interpreter that produces the following
error message (line numbers are not part of the actual output):

1	==============================================================
2	FAIL: testGetTypeIdCachesResult (dbfacadeTest.DjsDBFacadeTest)
3	--------------------------------------------------------------
4	Traceback (most recent call last):
5	  File "unittests/dbfacadeTest.py", line 89, in testFoo
6	    self.assertEquals(34, dtid)
7	  File "/usr/lib/python3.8/unittest.py", line 286, in
8	 failUnlessEqual
9	    raise self.failureException, \
10	AssertionError: 34 != 33
11
12	--------------------------------------------------------------
13	Ran 27 tests in 0.063s

Say you want [:clist](#:clist) write the relevant information of this message only,
namely:
5 unittests/dbfacadeTest.py:89:  AssertionError: 34 != 33

Then the error format string could be defined as follows:
```
:set efm=%C\ %.%#,%A\ \ File\ \"%f\"\\,\ line\ %l%.%#,%Z%[%^\ ]%\\@=%m

Note that the %C string is given before the %A here: since the expression
' %.%#' (which stands for the regular expression ' .*') matches every line
starting with a space, followed by any characters to the end of the line,
it also hides line 7 which would trigger a separate error message otherwise.
Error format strings are always parsed pattern by pattern until the first
match occurs.
### <a id="efm-%>" class="section-title" href="#efm-%>">Note:</a>
The %> item can be used to avoid trying patterns that appear earlier in
'errorformat'.  This is useful for patterns that match just about anything.
For example, if the error looks like this:

Error in line 123 of foo.c: ~
unknown variable "i" ~

This can be found with:
```
:set efm=xxx,%E%>Error in line %l of %f:,%Z%m
Where "xxx" has a pattern that would also match the second line.

Important: There is no memory of what part of the errorformat matched before;
every line in the error file gets a complete new run through the error format
lines.  For example, if one has:
```
setlocal efm=aa,bb,cc,dd,ee
Where aa, bb, etc. are error format strings.  Each line of the error file will
be matched to the pattern aa, then bb, then cc, etc.  Just because cc matched
the previous error line does _not_ mean that dd will be tried first on the
current line, even if cc and dd are multi-line errorformat strings.



### <a id="errorformat-separate-filename" class="section-title" href="#errorformat-separate-filename">Separate file name</a>

These prefixes are useful if the file name is given once and multiple messages
follow that refer to this file name.
%O		single-line file message: overread the matched part
%P		single-line file message: push file %f onto the stack
%Q		single-line file message: pop the last file from stack

Example: Given a compiler that produces the following error logfile (without
leading line numbers):

1	[a1.tt]
2	(1,17)  error: ';' missing
3	(21,2)  warning: variable 'z' not defined
4	(67,3)  error: end of file found before string ended
5
6	[a2.tt]
7
8	[a3.tt]
9	NEW compiler v1.1
10	(2,2)   warning: variable 'x' not defined
11	(67,3)  warning: 's' already defined

This logfile lists several messages for each file enclosed in [...] which are
properly parsed by an error format like this:
```
### <a id=":set efm=%+P[%f],(%l\\,%c)%[\ ]%t%[^:]:\ %m,%-Q" class="section-title" href="#:set efm=%+P[%f],(%l\\,%c)%[\ ]%t%[^:]:\ %m,%-Q">Note:</a>

A call of [:clist](#:clist) writes them accordingly with their correct filenames:

2 a1.tt:1 col 17 error: ';' missing
3 a1.tt:21 col 2 warning: variable 'z' not defined
4 a1.tt:67 col 3 error: end of file found before string ended
8 a3.tt:2 col 2 warning: variable 'x' not defined
9 a3.tt:67 col 3 warning: 's' already defined

Unlike the other prefixes that all match against whole lines, %P, %Q and %O
can be used to match several patterns in the same line.  Thus it is possible
to parse even nested files like in the following line:
{"file1" {"file2" error1} error2 {"file3" error3 {"file4" error4 error5}}}
The %O then parses over strings that do not contain any push/pop file name
information.  See [errorformat-LaTeX](#errorformat-LaTeX) for an extended example.


### <a id="efm-ignore" class="section-title" href="#efm-ignore">Ignoring and using whole messages</a>

The codes '+' or '-' can be combined with the uppercase codes above; in that
case they have to precede the letter, e.g. '%+A' or '%-G':
%-		do not include the matching multi-line in any output
%+		include the whole matching line in the %m error string

One prefix is only useful in combination with '+' or '-', namely %G.  It parses
over lines containing general information like compiler version strings or
other headers that can be skipped.
%-G		ignore this message
%+G		general message


Pattern matching

The scanf()-like "%*[]" notation is supported for backward-compatibility
with previous versions of Vim.  However, it is also possible to specify
(nearly) any Vim supported regular expression in format strings.
Since meta characters of the regular expression language can be part of
ordinary matching strings or file names (and therefore internally have to
be escaped), meta symbols have to be written with leading '%':
%\		The single '\' character.  Note that this has to be
escaped ("%\\") in ":set errorformat=" definitions.
%.		The single '.' character.
### <a id="The single ''(!) character." class="section-title" href="#The single ''(!) character.">	%#</a>
%^		The single '^' character.  Note that this is not
useful, the pattern already matches start of line.
%$		The single '$' character.  Note that this is not
useful, the pattern already matches end of line.
%[		The single '[' character for a [] character range.
%~		The single '~' character.
When using character classes in expressions (see [/\i](#/\i) for an overview),
terms containing the "\+" quantifier can be written in the scanf() "%*"
### <a id="Example: "%\\d%\\+" ("\d\+", "any number") is equivalent to "%\\d"." class="section-title" href="#Example: "%\\d%\\+" ("\d\+", "any number") is equivalent to "%\\d".">notation.</a>
Important note: The \(...\) grouping of sub-matches can not be used in format
specifications because it is reserved for internal conversions.


### <a id="efm-entries" class="section-title" href="#efm-entries">Multiple entries in 'errorformat'</a>

To be able to detect output from several compilers, several format patterns
may be put in 'errorformat', separated by commas (note: blanks after the comma
are ignored).  The first pattern that has a complete match is used.  If no
match is found, matching parts from the last one will be used, although the
file name is removed and the error message is set to the whole message.  If
there is a pattern that may match output from several compilers (but not in a
right way), put it after one that is more restrictive.

To include a comma in a pattern precede it with a backslash (you have to type
two in a ":set" command).  To include a backslash itself give two backslashes
(you have to type four in a ":set" command).  You also need to put a backslash
before a space for ":set".


### <a id="quickfix-valid" class="section-title" href="#quickfix-valid">Valid matches</a>

If a line does not completely match one of the entries in 'errorformat', the
whole line is put in the error message and the entry is marked "not valid"
These lines are skipped with the ":cn" and ":cp" commands (unless there is
no valid line at all).  You can use ":cl!" to display all the error messages.

If the error format does not contain a file name Vim cannot switch to the
correct file.  You will have to do this by hand.


For example, the format of the output from the Amiga Aztec compiler is:

filename>linenumber:columnnumber:errortype:errornumber:errormessage

filename	name of the file in which the error was detected
linenumber	line number where the error was detected
columnnumber	column number where the error was detected
errortype	type of the error, normally a single 'E' or 'W'
errornumber	number of the error (for lookup in the manual)
errormessage	description of the error

This can be matched with this 'errorformat' entry:
%f>%l:%c:%t:%n:%m

Some examples for C compilers that produce single-line error outputs:
%f:%l:\ %t%*[^0123456789]%n:\ %m	for Manx/Aztec C error messages
(scanf() doesn't understand [0-9])
%f\ %l\ %t%*[^0-9]%n:\ %m		for SAS C
\"%f\"\\,%*[^0-9]%l:\ %m		for generic C compilers
%f:%l:\ %m				for GCC
%f:%l:\ %m,%Dgmake[%*\\d]:\ Entering\ directory\ `%f',
%Dgmake[%*\\d]:\ Leaving\ directory\ `%f'
for GCC with gmake (concat the lines!)
%f(%l)\ :\ %*[^:]:\ %m			old SCO C compiler (pre-OS5)
%f(%l)\ :\ %t%*[^0-9]%n:\ %m		idem, with error type and number
%f:%l:\ %m,In\ file\ included\ from\ %f:%l:,\^I\^Ifrom\ %f:%l%m
for GCC, with some extras

Extended examples for the handling of multi-line messages are given below,
see [errorformat-Jikes| and |errorformat-LaTeX](#errorformat-Jikes| and |errorformat-LaTeX).

Note the backslash in front of a space and double quote.  It is required for
the :set command.  There are two backslashes in front of a comma, one for the
:set command and one to avoid recognizing the comma as a separator of error
formats.


Filtering messages

If you have a compiler that produces error messages that do not fit in the
format string, you could write a program that translates the error messages
into this format.  You can use this program with the ":make" command by
changing the 'makeprg' option.  For example:
```
:set mp=make\ \\\|&\ error_filter
The backslashes before the pipe character are required to avoid it to be
recognized as a command separator.  The backslash before each space is
required for the set command.


## <a id="quickfix-directory-stack" class="section-title" href="#quickfix-directory-stack">8. the Directory Stack</a> 

Quickfix maintains a stack for saving all used directories parsed from the
make output.  For GNU-make this is rather simple, as it always prints the
absolute path of all directories it enters and leaves.  Regardless if this is
done via a 'cd' command in the makefile or with the parameter "-C dir" (change
to directory before reading the makefile).  It may be useful to use the switch
"-w" to force GNU-make to print out the working directory before and after
processing.

Maintaining the correct directory is more complicated if you don't use
GNU-make.  AIX-make for example doesn't print any information about its
working directory.  Then you need to enhance the makefile.  In the makefile of
LessTif there is a command which echoes "Making {target} in {dir}".  The
special problem here is that it doesn't print information on leaving the
directory and that it doesn't print the absolute path.

To solve the problem with relative paths and missing "leave directory"
messages Vim uses the following algorithm:

1) Check if the given directory is a subdirectory of the current directory.
If this is true, store it as the current directory.
2) If it is not a subdir of the current directory, try if this is a
subdirectory of one of the upper directories.
3) If the directory still isn't found, it is assumed to be a subdirectory
of Vim's current directory.

Additionally it is checked for every file, if it really exists in the
identified directory.  If not, it is searched in all other directories of the
directory stack (NOT the directory subtree!).  If it is still not found, it is
assumed that it is in Vim's current directory.

There are limitations in this algorithm.  These examples assume that make just
prints information about entering a directory in the form "Making all in dir".

1) Assume you have following directories and files:
./dir1
./dir1/file1.c
./file1.c

If make processes the directory "./dir1" before the current directory and
there is an error in the file "./file1.c", you will end up with the file
"./dir1/file.c" loaded by Vim.

This can only be solved with a "leave directory" message.

2) Assume you have following directories and files:
./dir1
./dir1/dir2
./dir2

You get the following:

Make output			  Directory interpreted by Vim
------------------------	  ----------------------------
Making all in dir1		  ./dir1
Making all in dir2		  ./dir1/dir2
Making all in dir2		  ./dir1/dir2

This can be solved by printing absolute directories in the "enter directory"
message or by printing "leave directory" messages.

To avoid this problem, ensure to print absolute directory names and "leave
directory" messages.

Examples for Makefiles:

Unix:
libs:
for dn in $(LIBDIRS); do				\
(cd $$dn; echo "Entering dir '$$(pwd)'"; make); \
echo "Leaving dir";				\
done

Add
%DEntering\ dir\ '%f',%XLeaving\ dir
to your 'errorformat' to handle the above output.

Note that Vim doesn't check if the directory name in a "leave directory"
messages is the current directory.  This is why you could just use the message
"Leaving dir".


## <a id="errorformats" class="section-title" href="#errorformats">9. Specific Error File Formats</a> 

### <a id="errorformat-Jikes" class="section-title" href="#errorformat-Jikes">Note:</a>
Jikes(TM), a source-to-bytecode Java compiler published by IBM Research,
produces simple multi-line error messages.

An 'errorformat' string matching the produced messages is shown below.
The following lines can be placed in the user's [init.vim](#init.vim) to overwrite Vim's
recognized default formats, or see [:set+=](#:set+=) how to install this format
additionally to the default.
```

### <a id=":set efm=%A%f:%l:%c:%\\d:%\\d:," class="section-title" href="#:set efm=%A%f:%l:%c:%\\d:%\\d:,">Note:</a>
\%C%*\\s%trror:%m,
\%+C%*[^:]%trror:%m,
\%C%*\\s%tarning:%m,
\%C%m

```

Jikes(TM) produces a single-line error message when invoked with the option
"+E", and can be matched with the following:
```

### <a id=":setl efm=%f:%l:%v:%\\d:%\\d:%\\s%m" class="section-title" href="#:setl efm=%f:%l:%v:%\\d:%\\d:%\\s%m">Note:</a>

```

### <a id="errorformat-javac" class="section-title" href="#errorformat-javac">Note:</a>
This 'errorformat' has been reported to work well for javac, which outputs a
line with "^" to indicate the column of the error:
```
:setl efm=%A%f:%l:\ %m,%-Z%p^,%-C%.%#
or:
```
:setl efm=%A%f:%l:\ %m,%+Z%p^,%+C%.%#,%-G%.%#

```

Here is an alternative from Michael F. Lamb for Unix that filters the errors
first:
```
### <a id=":setl errorformat=%Z%f:%l:\ %m,%A%p^,%-G%[^sl]%.%#" class="section-title" href="#:setl errorformat=%Z%f:%l:\ %m,%A%p^,%-G%[^sl]%.%#">Note:</a>
:setl makeprg=javac\ %:S\ 2>&1\ \\\|\ vim-javac-filter

You need to put the following in "vim-javac-filter" somewhere in your path
(e.g., in ~/bin) and make it executable:
```
#!/bin/sed -f
### <a id="/\^$/s/\t/\ /g;/:[0-9]\+:/{h;d};/^[ \t]\^/G;" class="section-title" href="#/\^$/s/\t/\ /g;/:[0-9]\+:/{h;d};/^[ \t]\^/G;">Note:</a>

In English, that sed script:
- Changes single tabs to single spaces and
- Moves the line with the filename, line number, error message to just after
the pointer line. That way, the unused error text between doesn't break
vim's notion of a "multi-line message" and also doesn't force us to include
it as a "continuation of a multi-line message."

### <a id="errorformat-ant" class="section-title" href="#errorformat-ant">Note:</a>
For ant (https://jakarta.apache.org/) the above errorformat has to be modified
to honour the leading [javac] in front of each javac output line:
```
:set efm=%A\ %#[javac]\ %f:%l:\ %m,%-Z\ %#[javac]\ %p^,%-C%.%#

The 'errorformat' can also be configured to handle ant together with either
javac or jikes.  If you're using jikes, you should tell ant to use jikes' +E
command line switch which forces jikes to generate one-line error messages.
This is what the second line (of a build.xml file) below does:
```

```
property name = "build.compiler"       value = "jikes"/>

```
property name = "build.compiler.emacs" value = "true"/>

The 'errorformat' which handles ant with both javac and jikes is:
```
### <a id=":set efm=\ %#[javac]\ %#%f:%l:%c:%\\d:%\\d:\ %t%[%^:]%#:%m," class="section-title" href="#:set efm=\ %#[javac]\ %#%f:%l:%c:%\\d:%\\d:\ %t%[%^:]%#:%m,">Note:</a>
\%A\ %#[javac]\ %f:%l:\ %m,%-Z\ %#[javac]\ %p^,%-C%.%#

```

### <a id="errorformat-jade" class="section-title" href="#errorformat-jade">Note:</a>
parsing jade (see http://www.jclark.com/) errors is simple:
```
:set efm=jade:%f:%l:%c:%t:%m

```

### <a id="errorformat-LaTeX" class="section-title" href="#errorformat-LaTeX">Note:</a>
The following is an example how an 'errorformat' string can be specified
for the (La)TeX typesetting system which displays error messages over
multiple lines.  The output of ":clist" and ":cc" etc. commands displays
multi-lines in a single line, leading white space is removed.
It should be easy to adopt the above LaTeX errorformat to any compiler output
consisting of multi-line errors.

The commands can be placed in a [vimrc](#vimrc) file or some other Vim script file,
e.g. a script containing LaTeX related stuff which is loaded only when editing
LaTeX sources.
Make sure to copy all lines of the example (in the given order), afterwards
remove the comment lines.  For the '\' notation at the start of some lines see
[line-continuation](#line-continuation).

First prepare 'makeprg' such that LaTeX will report multiple
errors; do not stop when the first error has occurred:
```
:set makeprg=latex\ \\\\nonstopmode\ \\\\input\\{$*}

```

Start of multi-line error messages:
```
:set efm=%E!\ LaTeX\ %trror:\ %m,
\%E!\ %m,

```
		Start of multi-line warning messages; the first two also
include the line number.  Meaning of some regular expressions:
- "%.%#"  (".*")   matches a (possibly empty) string
### <a id="- "%\\d" ("\d\+") matches a number >" class="section-title" href="#- "%\\d" ("\d\+") matches a number >">Note:</a>
\%+WLaTeX\ %.%#Warning:\ %.%#line\ %l%.%#,
\%+W%.%#\ at\ lines\ %l--%*\\d,
\%WLaTeX\ %.%#Warning:\ %m,

```
		Possible continuations of error/warning messages; the first
one also includes the line number:
```
\%Cl.%l\ %m,
\%+C\ \ %m.,
\%+C%.%#-%.%#,
\%+C%.%#[]%.%#,
\%+C[]%.%#,
\%+C%.%#%[{}\\]%.%#,
\%+C<%.%#>%.%#,
\%C\ \ %m,

```
		Lines that match the following patterns do not contain any
important information; do not include them in messages:
```
\%-GSee\ the\ LaTeX%m,
\%-GType\ \ H\ <return>%m,
\%-G\ ...%.%#,
\%-G%.%#\ (C)\ %.%#,
\%-G(see\ the\ transcript%.%#),

```
		Generally exclude any empty or whitespace-only line from
being displayed:
```
\%-G\\s%#,

```
		The LaTeX output log does not specify the names of erroneous
source files per line; rather they are given globally,
enclosed in parentheses.
The following patterns try to match these names and store
them in an internal stack.  The patterns possibly scan over
the same input line (one after another), the trailing "%r"
conversion indicates the "rest" of the line that will be
parsed in the next go until the end of line is reached.

Overread a file name enclosed in '('...')'; do not push it
on a stack since the file apparently does not contain any
error:
```
\%+O(%f)%r,

```
		Push a file name onto the stack.  The name is given after '(':
```
\%+P(%f%r,
\%+P\ %\\=(%f%r,
\%+P%*[^()](%f%r,
\%+P[%\\d%[^()]%#(%f%r,

```
		Pop the last stored file name when a ')' is scanned:
```
\%+Q)%r,
\%+Q%*[^()])%r,
\%+Q[%\\d%*[^()])%r

Note that in some cases file names in the LaTeX output log cannot be parsed
properly.  The parser might have been messed up by unbalanced parentheses
then.  The above example tries to catch the most relevant cases only.
You can customize the given setting to suit your own purposes, for example,
all the annoying "Overfull ..." warnings could be excluded from being
recognized as an error.
Alternatively to filtering the LaTeX compiler output, it is also possible
to directly read the *.log file that is produced by the [La]TeX compiler.
This contains even more useful information about possible error causes.
However, to properly parse such a complex file, an external filter should
be used.  See the description further above how to make such a filter known
by Vim.


## <a id="quickfix-window-function" class="section-title" href="#quickfix-window-function">10. Customizing the Quickfix Window</a> 

The default format for the lines displayed in the quickfix window and location
list window is:


```
filename>[<lnum> col <col>](#<lnum> col <col>)<text>

The values displayed in each line correspond to the "bufnr", "lnum", "col" and
"text" fields returned by the [getqflist()](#getqflist()) function.

For some quickfix/location lists, the displayed text needs to be customized.
For example, if only the filename is present for a quickfix entry, then the
two "|" field separator characters after the filename are not needed.  Another
use case is to customize the path displayed for a filename. By default, the
complete path (which may be too long) is displayed for files which are not
under the current directory tree. The file path may need to be simplified to a
common parent directory.

The displayed text can be customized by setting the 'quickfixtextfunc' option
to a Vim function.  This function will be called with a dict argument and
should return a List of strings to be displayed in the quickfix or location
list window. The dict argument will have the following fields:

quickfix	set to 1 when called for a quickfix list and 0 when called for
a location list.
winid	for a location list, set to the id of the window with the
location list. For a quickfix list, set to 0. Can be used in
getloclist() to get the location list entry.
id		quickfix or location list identifier
start_idx	index of the first entry for which text should be returned
end_idx	index of the last entry for which text should be returned

The function should return a single line of text to display in the quickfix
window for each entry from start_idx to end_idx. The function can obtain
information about the entries using the [getqflist()](#getqflist()) function and specifying
the quickfix list identifier "id". For a location list, getloclist() function
can be used with the "winid" argument. If an empty list is returned, then the
default format is used to display all the entries. If an item in the returned
list is an empty string, then the default format is used to display the
corresponding entry.

If a quickfix or location list specific customization is needed, then the
'quickfixtextfunc' attribute of the list can be set using the [setqflist()](#setqflist()) or
[setloclist()](#setloclist()) function. This overrides the global 'quickfixtextfunc' option.

The example below displays the list of old files ([v:oldfiles](#v:oldfiles)) in a quickfix
window. As there is no line, column number and error text information
associated with each entry, the 'quickfixtextfunc' function returns only the
filename.
Example:
```
" create a quickfix list from v:oldfiles
call setqflist([], ' ', {'lines' : v:oldfiles, 'efm' : '%f',
\ 'quickfixtextfunc' : 'QfOldFiles'})
func QfOldFiles(info)
" get information about a range of quickfix entries
let items = getqflist({'id' : a:info.id, 'items' : 1}).items
let l = []
for idx in range(a:info.start_idx - 1, a:info.end_idx - 1)
" use the simplified file name
call add(l, fnamemodify(bufname(items[idx].bufnr), ':p:.'))
endfor
return l
endfunc

```


vim:tw=78:ts=8:noet:ft=help:norl:


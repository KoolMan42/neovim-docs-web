---
title: Tree Sitter
description: Some page
layout: "@layouts/MainLayout.astro"
---


## <a id="Nvim" class="section-title" href="#Nvim"> Vim Diff Txt</a> 

NVIM REFERENCE MANUAL


### <a id="vim-differences" class="section-title" href="#vim-differences">Differences between Nvim and Vim</a>

Nvim differs from Vim in many ways, although editor and Vimscript (not
Vim9script) features are mostly identical.  This document is a complete and
centralized reference of the differences.

Type [gO](#gO) to see the table of contents.


## <a id="nvim-config" class="section-title" href="#nvim-config">1. Configuration</a> 

- Use `$XDG_CONFIG_HOME/nvim/init.vim` instead of `.vimrc` for your [config](#config).
- Use `$XDG_CONFIG_HOME/nvim` instead of `.vim` to store configuration files.
- Use `$XDG_STATE_HOME/nvim/shada/main.shada` instead of `.viminfo` for persistent
session information.  [shada](#shada)


## <a id="nvim-defaults" class="section-title" href="#nvim-defaults">2. Defaults</a> 

- Filetype detection is enabled by default. This can be disabled by adding
":filetype off" to [init.vim](#init.vim).
- Syntax highlighting is enabled by default. This can be disabled by adding
":syntax off" to [init.vim](#init.vim).

- 'autoindent' is enabled
- 'autoread' is enabled
- 'background' defaults to "dark" (unless set automatically by the terminal/UI)
- 'backspace' defaults to "indent,eol,start"
- 'backupdir' defaults to .,~/.local/state/nvim/backup// ([xdg](#xdg)), auto-created
- 'belloff' defaults to "all"
- 'compatible' is always disabled
- 'complete' excludes "i"
- 'directory' defaults to ~/.local/state/nvim/swap// ([xdg](#xdg)), auto-created
- 'display' defaults to "lastline"
- 'encoding' is UTF-8 (cf. 'fileencoding' for file-content encoding)
- 'fillchars' defaults (in effect) to "vert:│,fold:·,sep:│"
- 'formatoptions' defaults to "tcqj"
- 'fsync' is disabled
- 'hidden' is enabled
- 'history' defaults to 10000 (the maximum)
- 'hlsearch' is enabled
- 'incsearch' is enabled
- 'joinspaces' is disabled
- 'langnoremap' is enabled
- 'langremap' is disabled
- 'laststatus' defaults to 2 (statusline is always shown)
- 'listchars' defaults to "tab:> ,trail:-,nbsp:+"
- 'mouse' defaults to "nvi"
- 'mousemodel' defaults to "popup_setpos"
- 'nrformats' defaults to "bin,hex"
- 'ruler' is enabled
- 'sessionoptions' includes "unix,slash", excludes "options"
- 'shortmess' includes "F", excludes "S"
- 'showcmd' is enabled
- 'sidescroll' defaults to 1
- 'smarttab' is enabled
- 'startofline' is disabled
- 'switchbuf' defaults to "uselast"
- 'tabpagemax' defaults to 50
- 'tags' defaults to "./tags;,tags"
- 'ttimeoutlen' defaults to 50
- 'ttyfast' is always set
- 'undodir' defaults to ~/.local/state/nvim/undo// ([xdg](#xdg)), auto-created
- 'viewoptions' includes "unix,slash", excludes "options"
- 'viminfo' includes "!"
- 'wildmenu' is enabled
- 'wildoptions' defaults to "pum,tagfile"

- [man.lua| plugin is enabled, so |:Man](#man.lua| plugin is enabled, so |:Man) is available by default.
- [matchit](#matchit) plugin is enabled. To disable it in your config:
```
:let loaded_matchit = 1

- [g:vimsyn_embed](#g:vimsyn_embed) defaults to "l" to enable Lua highlighting


Default Mouse ~
### <a id="default-mouse disable-mouse" class="section-title" href="#default-mouse disable-mouse">Note:</a>
By default the mouse is enabled, and <RightMouse> opens a [popup-menu](#popup-menu) with
standard actions ("Cut", "Copy", "Paste", …). Mouse is NOT enabled in
[command-mode| or the |more-prompt](#command-mode| or the |more-prompt), so you can temporarily disable it just by
typing ":".

If you don't like this you can disable the mouse in your [config](#config) using any of
the following:
- Disable mouse completely by unsetting the 'mouse' option:
```
set mouse=
- Pressing <RightMouse> extends selection instead of showing popup-menu:
```
set mousemodel=extend
- Pressing <A-LeftMouse> releases mouse until the cursor moves:
```
nnoremap <A-LeftMouse> <Cmd>
\ set mouse=<Bar>
\ echo 'mouse OFF until next cursor-move'<Bar>
### <a id="\ autocmd CursorMoved  ++once set mouse&<Bar>" class="section-title" href="#\ autocmd CursorMoved  ++once set mouse&<Bar>">Note:</a>
\ echo 'mouse ON'<CR>

```


Default Mappings ~
### <a id="default-mappings" class="section-title" href="#default-mappings">Note:</a>
Nvim creates the following default mappings at [startup](#startup). You can disable any
of these in your config by simply removing the mapping, e.g. ":unmap Y".
```
nnoremap Y y$
nnoremap <C-L> <Cmd>nohlsearch<Bar>diffupdate<Bar>normal! <C-L><CR>
inoremap <C-U> <C-G>u<C-U>
inoremap <C-W> <C-G>u<C-W>
xnoremap * y/\V<C-R>"<CR>
xnoremap # y?\V<C-R>"<CR>
nnoremap & :&&<CR>

```

Default Autocommands ~
### <a id="default-autocmds" class="section-title" href="#default-autocmds">Note:</a>
Default autocommands exist in the following groups. Use ":autocmd! {group}" to
remove them and ":autocmd {group}" to see how they're defined.

nvim_terminal:
- BufReadCmd: Treats "term://" buffers as [terminal| buffers. |terminal-start](#terminal| buffers. |terminal-start)

nvim_cmdwin:
- CmdwinEnter: Limits syntax sync to maxlines=1 in the [cmdwin](#cmdwin).


## <a id="nvim-features" class="section-title" href="#nvim-features">3. New Features</a> 

MAJOR COMPONENTS ~

API				[API](#API)
Job control			[job-control](#job-control)
LSP framework			[lsp](#lsp)
Lua scripting			[lua](#lua)
Parsing engine			[treesitter](#treesitter)
Providers
Clipboard			[provider-clipboard](#provider-clipboard)
Node.js plugins		[provider-nodejs](#provider-nodejs)
Python plugins		[provider-python](#provider-python)
Ruby plugins			[provider-ruby](#provider-ruby)
Remote plugins			[remote-plugin](#remote-plugin)
Shared data			[shada](#shada)
Terminal emulator		[terminal](#terminal)
Vimscript parser		[nvim_parse_expression()](#nvim_parse_expression())
XDG base directories		[xdg](#xdg)

USER EXPERIENCE  ~

Working intuitively and consistently is a major goal of Nvim.

### <a id="feature-compile" class="section-title" href="#feature-compile">Note:</a>
- Nvim always includes ALL features, in contrast to Vim (which ships with
various combinations of 100+ optional features). Think of it as a leaner
version of Vim's "HUGE" build. This reduces surface area for bugs, and
removes a common source of confusion and friction for users.

- Nvim avoids features that cannot be provided on all platforms; instead that
is delegated to external plugins/extensions. E.g. the `-X` platform-specific
option is "sometimes" available in Vim (with potential surprises:
https://stackoverflow.com/q/14635295).

- Vim's internal test functions (test_autochdir(), test_settime(), etc.) are
not exposed (nor implemented); instead Nvim has a robust API.

- Behaviors, options, documentation are removed if they cost users more time
than they save.

Usability details have been improved where the benefit outweighs any
backwards-compatibility cost. Some examples:

- Directories for 'directory' and 'undodir' are auto-created.
- Terminal features such as 'guicursor' are enabled where possible.

Some features are built in that otherwise required external plugins:

- Highlighting the yanked region, see [lua-highlight](#lua-highlight).

ARCHITECTURE ~

External plugins run in separate processes. [remote-plugin](#remote-plugin) This improves
stability and allows those plugins to work without blocking the editor. Even
"legacy" Python and Ruby plugins which use the old Vim interfaces ([if_pyth](#if_pyth),
[if_ruby](#if_ruby)) run out-of-process.

Platform and I/O facilities are built upon libuv. Nvim benefits from libuv
features and bug fixes, and other projects benefit from improvements to libuv
by Nvim developers.

FEATURES ~

Command-line highlighting:
The expression prompt ([@=|, |c_CTRL-R_=|, |i_CTRL-R_=](#@=|, |c_CTRL-R_=|, |i_CTRL-R_=)) is highlighted
using a built-in Vimscript expression parser. [expr-highlight](#expr-highlight)
### <a id="E5408 E5409" class="section-title" href="#E5408 E5409">Note:</a>
[input()|, |inputdialog()| support custom highlighting. |input()-highlight](#input()|, |inputdialog()| support custom highlighting. |input()-highlight)
### <a id="g:Nvim_color_cmdline" class="section-title" href="#g:Nvim_color_cmdline">Note:</a>
(Experimental) Command-line ([:](#:)) is colored by callback defined in
`g:Nvim_color_cmdline` (this callback is for testing only, and will be
removed in the future).

Commands:
[:checkhealth](#:checkhealth)
[:drop](#:drop) is always available
[:Man](#:Man) is available by default, with many improvements such as completion
[:match](#:match) can be invoked before highlight group is defined
[:source](#:source) works with Lua
User commands can support [:command-preview](#:command-preview) to show results as you type

Events:
[RecordingEnter](#RecordingEnter)
[RecordingLeave](#RecordingLeave)
[SearchWrapped](#SearchWrapped)
[Signal](#Signal)
[TabNewEntered](#TabNewEntered)
[TermClose](#TermClose)
[TermOpen](#TermOpen)
[UIEnter](#UIEnter)
[UILeave](#UILeave)

Functions:
[dictwatcheradd()| notifies a callback whenever a |Dict](#dictwatcheradd()| notifies a callback whenever a |Dict) is modified
[dictwatcherdel()](#dictwatcherdel())
[menu_get()](#menu_get())
[msgpackdump()|, |msgpackparse()](#msgpackdump()|, |msgpackparse()) provide msgpack de/serialization
[stdpath()](#stdpath())
[system()|, |systemlist()](#system()|, |systemlist()) can run {cmd} directly (without 'shell')
[matchadd()](#matchadd()) can be called before highlight group is defined

Highlight groups:
[highlight-blend](#highlight-blend) controls blend level for a highlight group
[expr-highlight](#expr-highlight) highlight groups (prefixed with "Nvim")
[hl-NormalFloat](#hl-NormalFloat) highlights floating window
[hl-NormalNC](#hl-NormalNC) highlights non-current windows
[hl-MsgArea](#hl-MsgArea) highlights messages/cmdline area
[hl-MsgSeparator](#hl-MsgSeparator) highlights separator for scrolled messages
[hl-Substitute](#hl-Substitute)
[hl-TermCursor](#hl-TermCursor)
[hl-TermCursorNC](#hl-TermCursorNC)
[hl-WinSeparator](#hl-WinSeparator) highlights window separators
[hl-Whitespace](#hl-Whitespace) highlights 'listchars' whitespace

Input/Mappings:
ALT ([META|) chords always work (even in the |TUI|). Map |<M-](#META|) chords always work (even in the |TUI|). Map |<M-) with any key:

```
M-1>, <M-BS>, <M-Del>, <M-Ins>, <M-/>, <M-\>, <M-Space>, <M-Enter>, etc.
Case-sensitive: <M-a> and <M-A> are two different keycodes.

ALT may behave like <Esc> if not mapped. [i_ALT| |v_ALT| |c_ALT](#i_ALT| |v_ALT| |c_ALT)

Normal commands:
[gO](#gO) shows a filetype-defined "outline" of the current buffer.

Options:
'cpoptions'   flags: [cpo-_](#cpo-_)
'guicursor'   works in the terminal
'fillchars'   flags: "msgsep", "horiz", "horizup",
"horizdown", "vertleft", "vertright", "verthoriz"
'foldcolumn'  supports up to 9 dynamic/fixed columns
'inccommand'  shows interactive results for [:substitute](#:substitute)-like commands
and [:command-preview](#:command-preview) commands
'laststatus'  global statusline support
'mousescroll' amount to scroll by when scrolling with a mouse
'pumblend'    pseudo-transparent popupmenu
'scrollback'
'signcolumn'  supports up to 9 dynamic/fixed columns
'statusline'  supports unlimited alignment sections
'tabline'     %@Func@foo%X can call any function on mouse-click
'winblend'    pseudo-transparency in floating windows [api-floatwin](#api-floatwin)
'winhighlight' window-local highlights

Signs:
Signs are removed if the associated line is deleted.

Variables:
[v:progpath](#v:progpath) is always absolute ("full")
[v:windowid](#v:windowid) is always available (for use by external UIs)


## <a id="nvim-features-changed" class="section-title" href="#nvim-features-changed">4. Changed Features</a> 

Nvim always builds with all features, in contrast to Vim which may have
certain features removed/added at compile-time. [feature-compile](#feature-compile)

Some Vim features were changed in Nvim, and vice versa.

If a Python interpreter is available on your `$PATH`, [:python| and |:python3](#:python| and |:python3)
are always available and may be used simultaneously. See [provider-python](#provider-python).

[:redir| nested in |execute()](#:redir| nested in |execute()) works.

[mkdir()](#mkdir()) behaviour changed:
1. Assuming /tmp/foo does not exist and /tmp can be written to
mkdir('/tmp/foo/bar', 'p', 0700) will create both /tmp/foo and /tmp/foo/bar 
with 0700 permissions. Vim mkdir will create /tmp/foo with 0755.
2. If you try to create an existing directory with `'p'` (e.g. mkdir('/',
'p')) mkdir() will silently exit. In Vim this was an error.
3. mkdir() error messages now include strerror() text when mkdir fails.

[string()| and |:echo](#string()| and |:echo) behaviour changed:
1. No maximum recursion depth limit is applied to nested container
structures.
2. [string()](#string()) fails immediately on nested containers, not when recursion limit
was exceeded.
2. When [:echo](#:echo) encounters duplicate containers like
```

let l = []
echo [l, l]

```

it does not use "[...]" (was: "[[], [...]]", now: "[[], []]"). "..." is
only used for recursive containers.
3. [:echo](#:echo) printing nested containers adds "@level" after "..." designating
the level at which recursive container was printed: [:echo-self-refer](#:echo-self-refer).
Same thing applies to [string()](#string()) (though it uses construct like
"{E724@level}"), but this is not reliable because [string()](#string()) continues to
error out.
4. Stringifyed infinite and NaN values now use [str2float()](#str2float()) and can be evaled
back.
5. (internal) Trying to print or stringify VAR_UNKNOWN in Vim results in 
nothing, E908, in Nvim it is internal error.

[json_decode()](#json_decode()) behaviour changed:
1. It may output [msgpack-special-dict](#msgpack-special-dict).
2. [msgpack-special-dict](#msgpack-special-dict) is emitted also in case of duplicate keys, while in 
Vim it errors out.
3. It accepts only valid JSON.  Trailing commas are not accepted.

[json_encode()| behaviour slightly changed: now |msgpack-special-dict](#json_encode()| behaviour slightly changed: now |msgpack-special-dict) values 
are accepted, but [v:none](#v:none) is not.

Viminfo text files were replaced with binary (messagepack) ShaDa files.
Additional differences:

- [shada-c](#shada-c) has no effect.
- [shada-s](#shada-s) now limits size of every item and not just registers.
- 'viminfo' option got renamed to 'shada'. Old option is kept as an alias for
compatibility reasons.
- [:wviminfo| was renamed to |:wshada|, |:rviminfo| to |:rshada](#:wviminfo| was renamed to |:wshada|, |:rviminfo| to |:rshada).  Old
commands are still kept.
- ShaDa file format was designed with forward and backward compatibility in
mind. [shada-compatibility](#shada-compatibility)
- Some errors make ShaDa code keep temporary file in-place for user to decide
what to do with it.  Vim deletes temporary file in these cases.
[shada-error-handling](#shada-error-handling)
- ShaDa file keeps search direction ([v:searchforward](#v:searchforward)), viminfo does not.

[printf()](#printf()) returns something meaningful when used with `%p` argument: in Vim 
it used to return useless address of the string (strings are copied to the 
newly allocated memory all over the place) and fail on types which cannot be 
coerced to strings. See [id()](#id()) for more details, currently it uses 
`printf("%p", {expr})` internally.

[c_CTRL-R| pasting a non-special register into |cmdline](#c_CTRL-R| pasting a non-special register into |cmdline) omits the last <CR>.

[CursorMoved](#CursorMoved) always triggers when moving between windows.

Lua interface ([lua.txt](#lua.txt)):

- `:lua print("a\0b")` will print `a^@b`, like with `:echomsg "a\nb"` . In Vim
that prints `a` and `b` on separate lines, exactly like
`:lua print("a\nb")` .
- `:lua error('TEST')` emits the error “E5105: Error while calling lua chunk:
[string "<VimL compiled string>"]:1: TEST”, whereas Vim emits only “TEST”.
- Lua has direct access to Nvim [API](#API) via `vim.api`.
- Lua package.path and package.cpath are automatically updated according to
'runtimepath': [lua-require](#lua-require).

Commands:
[:doautocmd](#:doautocmd) does not warn about "No matching autocommands".
[:wincmd](#:wincmd) accepts a count.
`:write!` does not show a prompt if the file was updated externally.

Command line completion:
The meanings of arrow keys do not change depending on 'wildoptions'.

Functions:
[input()| and |inputdialog()](#input()| and |inputdialog()) support for each other’s features (return on
cancel and completion respectively) via dictionary argument (replaces all
other arguments if used), and "cancelreturn" can have any type if passed in
a dictionary.
[input()| and |inputdialog()](#input()| and |inputdialog()) support user-defined cmdline highlighting.

Highlight groups:
[hl-ColorColumn|, |hl-CursorColumn](#hl-ColorColumn|, |hl-CursorColumn) are lower priority than most other
groups
[hl-CurSearch](#hl-CurSearch) highlights match under cursor instead of last match found
using [n| or |N](#n| or |N)
[hl-CursorLine](#hl-CursorLine) is low-priority unless foreground color is set
[hl-VertSplit| superseded by |hl-WinSeparator](#hl-VertSplit| superseded by |hl-WinSeparator)
Highlight groups names are allowed to contain the characters `.` and `@`.
It is an error to define a highlight group with a name that doesn't match
### <a id="the regexp `[a-zA-Z0-9_.@]` (see [group-name|)." class="section-title" href="#the regexp `[a-zA-Z0-9_.@]` (see |group-name](#group-name|)." class="section-title" href="#the regexp `[a-zA-Z0-9_.@]` (see |group-name)).">Note:</a>

Macro/[recording](#recording) behavior
Replay of a macro recorded during :lmap produces the same actions as when it
was recorded. In Vim if a macro is recorded while using :lmap'ped keys then
the behaviour during record and replay differs.

'keymap' is implemented via :lmap instead of :lnoremap so that you can use
macros and 'keymap' at the same time. This also means you can use [:imap](#:imap) on
the results of keys from 'keymap'.

Mappings:
Creating a mapping for a simplifiable key (e.g. <C-I>) doesn't replace an
existing mapping for its simplified form (e.g. <Tab>).

Motion:
The [jumplist](#jumplist) avoids useless/phantom jumps.

Normal commands:
[Q](#Q) replays the last recorded macro instead of switching to Ex mode.
Instead [gQ](#gQ) can be used to enter Ex mode.

Options:
'ttimeout', 'ttimeoutlen' behavior was simplified
'jumpoptions' "stack" behavior
'jumpoptions' "view" tries to restore the [mark-view](#mark-view) when moving through
the [jumplist|, |changelist|, |alternate-file| or using |mark-motions](#jumplist|, |changelist|, |alternate-file| or using |mark-motions).
'shortmess' the "F" flag does not affect output from autocommands

Shell:
Shell output ([:!|, |:make](#:!|, |:make), …) is always routed through the UI, so it
cannot "mess up" the screen. (You can still use "chansend(v:stderr,…)" if
you want to mess up the screen :)

Nvim throttles (skips) messages from shell commands ([:!|, |:grep|, |:make](#:!|, |:grep|, |:make))
if there is too much output. No data is lost, this only affects display and
improves performance. [:terminal](#:terminal) output is never throttled.

[:!| does not support "interactive" commands. Use |:terminal](#:!| does not support "interactive" commands. Use |:terminal) instead.
(GUI Vim has a similar limitation, see ":help gui-pty" in Vim.)

:!start is not special-cased on Windows.

[system()| does not support writing/reading "backgrounded" commands. |E5677](#system()| does not support writing/reading "backgrounded" commands. |E5677)

Startup:
[-e| and |-es](#-e| and |-es) invoke the same "improved Ex mode" as -E and -Es.
[-E| and |-Es](#-E| and |-Es) read stdin as text (into buffer 1).
[-es| and |-Es](#-es| and |-Es) have improved behavior:
- Quits automatically, don't need "-c qa!".
- Skips swap-file dialog.
[-s](#-s) reads Normal commands from stdin if the script name is "-".
Reading text (instead of commands) from stdin [--](#--):
- works by default: "-" file is optional
- works in more cases: [-Es](#-Es), file args

Syntax highlighting:
syncolor.vim has been removed. Nvim now sets up default highlighting groups
automatically for both light and dark backgrounds, regardless of whether or
not syntax highlighting is enabled. This means that [:syntax-on](#:syntax-on) and
[:syntax-enable](#:syntax-enable) are now identical. Users who previously used an
after/syntax/syncolor.vim file should transition that file into a
colorscheme. [:colorscheme](#:colorscheme)

TUI:
### <a id=":set-termcap" class="section-title" href="#:set-termcap">Note:</a>
Start Nvim with 'verbose' level 3 to show terminal capabilities:
```
nvim -V3

```

### <a id="'term' E529 E530 E531" class="section-title" href="#'term' E529 E530 E531">Note:</a>
'term' reflects the terminal type derived from [$TERM](#$TERM) and other environment
checks.  For debugging only; not reliable during startup.
```
:echo &term

```
  "builtin_x" means one of the [builtin-terms](#builtin-terms) was chosen, because the expected
terminfo file was not found on the system.

Nvim will use 256-colour capability on Linux virtual terminals.  Vim uses
only 8 colours plus bright foreground on Linux VTs.

Vim combines what is in its [builtin-terms](#builtin-terms) with what it reads from terminfo,
and has a 'ttybuiltin' setting to control how that combination works.  Nvim
uses one or the other, it does not attempt to merge the two.

UI/Display:
[Visual| selection highlights the character at cursor. |visual-use](#Visual| selection highlights the character at cursor. |visual-use)

messages: When showing messages longer than 'cmdheight', only
scroll the message lines, not the entire screen. The
separator line is decorated by [hl-MsgSeparator](#hl-MsgSeparator) and
### <a id="the "msgsep" flag of 'fillchars'. msgsep" class="section-title" href="#the "msgsep" flag of 'fillchars'. msgsep">Note:</a>

Vimscript compatibility:
`count` does not alias to [v:count](#v:count)
`errmsg` does not alias to [v:errmsg](#v:errmsg)
`shell_error` does not alias to [v:shell_error](#v:shell_error)
`this_session` does not alias to [v:this_session](#v:this_session)

Working directory (Vim implemented some of these later than Nvim):
- [DirChanged| and |DirChangedPre](#DirChanged| and |DirChangedPre) can be triggered when switching to another
window or tab.
- [getcwd()| and |haslocaldir()](#getcwd()| and |haslocaldir()) may throw errors if the tab page or window
cannot be found.  *E5000* *E5001* *E5002*
- [haslocaldir()](#haslocaldir()) checks for tab-local directory if and only if -1 is passed as
window number, and its only possible returns values are 0 and 1.
- `getcwd(-1)` is equivalent to `getcwd(-1, 0)` instead of returning the global
working directory. Use `getcwd(-1, -1)` to get the global working directory.


## <a id="nvim-features-missing" class="section-title" href="#nvim-features-missing">5. Missing Legacy Features</a> 

Some legacy Vim features are not yet implemented:

- *if_lua* : Nvim [Lua](#Lua) API is not compatible with Vim's "if_lua"
- *if_mzscheme*
- [if_pyth](#if_pyth): *python-bindeval* *python-Function* are not supported
- *if_tcl*

*:gui*
*:gvim*


## <a id="nvim-features-removed" class="section-title" href="#nvim-features-removed">6. Removed Features</a> 

These Vim features were intentionally removed from Nvim.

Aliases:
ex        (alias for "nvim -e")
exim      (alias for "nvim -E")
gex       (GUI)
gview     (GUI)
gvim      (GUI)
gvimdiff  (GUI)
rgview    (GUI)
rgvim     (GUI)
rview
rvim
view      (alias for "nvim -R")
vimdiff   (alias for "nvim -d" [diff-mode](#diff-mode))

Commands:
:fixdel
:helpfind
:mode (no longer accepts an argument)
:open
:Print
:promptfind
:promptrepl
:scriptversion (always version 1)
:shell
:sleep! (does not hide the cursor; same as :sleep)
:smile
:tearoff
:cstag
:cscope
:lcscope
:scscope

Compile-time features:
Emacs tags support
X11 integration (see [x11-selection](#x11-selection))

Eval:
Vim9script
### <a id="cscope_connection()" class="section-title" href="#cscope_connection()">Note:</a>
### <a id="js_encode()" class="section-title" href="#js_encode()">Note:</a>
### <a id="js_decode()" class="section-title" href="#js_decode()">Note:</a>
### <a id="v:none (used by Vim to represent JavaScript "undefined"); use [v:null| instead." class="section-title" href="#v:none (used by Vim to represent JavaScript "undefined"); use |v:null](#v:null| instead." class="section-title" href="#v:none (used by Vim to represent JavaScript "undefined"); use |v:null) instead.">Note:</a>
### <a id="v:sizeofint" class="section-title" href="#v:sizeofint">Note:</a>
### <a id="v:sizeoflong" class="section-title" href="#v:sizeoflong">Note:</a>
### <a id="v:sizeofpointer" class="section-title" href="#v:sizeofpointer">Note:</a>

Events:
### <a id="SigUSR1 Use [Signal| to detect `SIGUSR1` signal instead." class="section-title" href="#SigUSR1 Use |Signal](#Signal| to detect `SIGUSR1` signal instead." class="section-title" href="#SigUSR1 Use |Signal) to detect `SIGUSR1` signal instead.">Note:</a>

Highlight groups:
### <a id="hl-StatusLineTerm hl-StatusLineTermNC are unnecessary because Nvim" class="section-title" href="#hl-StatusLineTerm hl-StatusLineTermNC are unnecessary because Nvim">Note:</a>
supports 'winhighlight' window-local highlights.
For example, to mimic Vim's StatusLineTerm:
```
hi StatusLineTerm ctermfg=black ctermbg=green
hi StatusLineTermNC ctermfg=green
### <a id="autocmd TermOpen,WinEnter  if &buftype=='terminal'" class="section-title" href="#autocmd TermOpen,WinEnter  if &buftype=='terminal'">Note:</a>
\|setlocal winhighlight=StatusLine:StatusLineTerm,StatusLineNC:StatusLineTermNC
\[else|setlocal winhighlight=](#else|setlocal winhighlight=)endif

```


Options:
antialias
### <a id="'balloondelay' 'bdlay'" class="section-title" href="#'balloondelay' 'bdlay'">Note:</a>
### <a id="'ballooneval' 'beval' 'noballooneval' 'nobeval'" class="section-title" href="#'ballooneval' 'beval' 'noballooneval' 'nobeval'">Note:</a>
### <a id="'balloonexpr' 'bexpr'" class="section-title" href="#'balloonexpr' 'bexpr'">Note:</a>
bioskey (MS-DOS)
conskey (MS-DOS)
### <a id="'cp' 'nocompatible' 'nocp' 'compatible' (Nvim is always "nocompatible".)" class="section-title" href="#'cp' 'nocompatible' 'nocp' 'compatible' (Nvim is always "nocompatible".)">Note:</a>
### <a id="'cpoptions' (gjkHw<- and all POSIX flags were removed)" class="section-title" href="#'cpoptions' (gjkHw<- and all POSIX flags were removed)">Note:</a>
### <a id="'cryptmethod' 'cm' 'key' (Vim encryption implementation)" class="section-title" href="#'cryptmethod' 'cm' 'key' (Vim encryption implementation)">Note:</a>
cscopepathcomp
cscopeprg
cscopequickfix
cscoperelative
cscopetag
cscopetagorder
cscopeverbose
### <a id="'ed' 'edcompatible' 'noed' 'noedcompatible'" class="section-title" href="#'ed' 'edcompatible' 'noed' 'noedcompatible'">Note:</a>
'encoding' ("utf-8" is always used)
esckeys
'guioptions' "t" flag was removed
### <a id="'guifontset' 'gfs' (Use 'guifont' instead.)" class="section-title" href="#'guifontset' 'gfs' (Use 'guifont' instead.)">Note:</a>
### <a id="'guipty' (Nvim uses pipes and PTYs consistently on all platforms.)" class="section-title" href="#'guipty' (Nvim uses pipes and PTYs consistently on all platforms.)">Note:</a>
'highlight' (Names of builtin [highlight-groups](#highlight-groups) cannot be changed.)
### <a id="'imactivatefunc' 'imaf'" class="section-title" href="#'imactivatefunc' 'imaf'">Note:</a>
### <a id="'imactivatekey' 'imak'" class="section-title" href="#'imactivatekey' 'imak'">Note:</a>
### <a id="'imstatusfunc' 'imsf'" class="section-title" href="#'imstatusfunc' 'imsf'">Note:</a>
### <a id="'insertmode' 'im' Use the following script to emulate 'insertmode':" class="section-title" href="#'insertmode' 'im' Use the following script to emulate 'insertmode':">Note:</a>
```
### <a id="autocmd BufWinEnter  startinsert" class="section-title" href="#autocmd BufWinEnter  startinsert">Note:</a>
inoremap <Esc> <C-X><C-Z><C-]>
inoremap <C-C> <C-X><C-Z>
inoremap <C-L> <C-X><C-Z><C-]><Esc>
inoremap <C-Z> <C-X><C-Z><Cmd>suspend<CR>
noremap <C-C> <Esc>
snoremap <C-C> <Esc>
noremap <C-\><C-G> <C-\><C-N><Cmd>startinsert<CR>
cnoremap <C-\><C-G> <C-\><C-N><Cmd>startinsert<CR>
inoremap <C-\><C-G> <C-X><C-Z>
### <a id="autocmd CmdWinEnter  noremap <buffer> <C-C> <C-C>" class="section-title" href="#autocmd CmdWinEnter  noremap <buffer> <C-C> <C-C>">Note:</a>
### <a id="autocmd CmdWinEnter  inoremap <buffer> <C-C> <C-C>" class="section-title" href="#autocmd CmdWinEnter  inoremap <buffer> <C-C> <C-C>">Note:</a>

lua << EOF
vim.on_key(function(c)
if c == '\27' then
local mode = vim.api.nvim_get_mode().mode
if mode:find('^[nvV\22sS\19]') and vim.fn.getcmdtype() == '' then
vim.schedule(function()
vim.cmd('startinsert')
end)
end
end
end)
EOF

```

### <a id="'macatsui'" class="section-title" href="#'macatsui'">Note:</a>
### <a id="'maxcombine' 'mco'" class="section-title" href="#'maxcombine' 'mco'">Note:</a>
Nvim always displays up to 6 combining characters.  You can still edit
text with more than 6 combining characters, you just can't see them.
Use [g8| or |ga|.  See |mbyte-combining](#g8| or |ga|.  See |mbyte-combining).
### <a id="'maxmem' Nvim delegates memory-management to the OS." class="section-title" href="#'maxmem' Nvim delegates memory-management to the OS.">Note:</a>
### <a id="'maxmemtot' Nvim delegates memory-management to the OS." class="section-title" href="#'maxmemtot' Nvim delegates memory-management to the OS.">Note:</a>
### <a id="'prompt' 'noprompt'" class="section-title" href="#'prompt' 'noprompt'">Note:</a>
### <a id="'remap' 'noremap'" class="section-title" href="#'remap' 'noremap'">Note:</a>
### <a id="'restorescreen' 'rs' 'norestorescreen' 'nors'" class="section-title" href="#'restorescreen' 'rs' 'norestorescreen' 'nors'">Note:</a>
### <a id="'shelltype'" class="section-title" href="#'shelltype'">Note:</a>
### <a id="'shortname' 'sn' 'noshortname' 'nosn'" class="section-title" href="#'shortname' 'sn' 'noshortname' 'nosn'">Note:</a>
### <a id="'swapsync' 'sws'" class="section-title" href="#'swapsync' 'sws'">Note:</a>
### <a id="'termencoding' 'tenc' (Vim 7.4.852 also removed this for Windows)" class="section-title" href="#'termencoding' 'tenc' (Vim 7.4.852 also removed this for Windows)">Note:</a>
### <a id="'terse' 'noterse' (Add "s" to 'shortmess' instead)" class="section-title" href="#'terse' 'noterse' (Add "s" to 'shortmess' instead)">Note:</a>
textauto
textmode
### <a id="'toolbar' 'tb'" class="section-title" href="#'toolbar' 'tb'">Note:</a>
### <a id="'toolbariconsize' 'tbis'" class="section-title" href="#'toolbariconsize' 'tbis'">Note:</a>
### <a id="'ttybuiltin' 'tbi' 'nottybuiltin' 'notbi'" class="section-title" href="#'ttybuiltin' 'tbi' 'nottybuiltin' 'notbi'">Note:</a>
### <a id="'ttyfast' 'tf' 'nottyfast' 'notf'" class="section-title" href="#'ttyfast' 'tf' 'nottyfast' 'notf'">Note:</a>
### <a id="'ttymouse' 'ttym'" class="section-title" href="#'ttymouse' 'ttym'">Note:</a>
### <a id="'ttyscroll' 'tsl'" class="section-title" href="#'ttyscroll' 'tsl'">Note:</a>
### <a id="'ttytype' 'tty'" class="section-title" href="#'ttytype' 'tty'">Note:</a>
weirdinvert

Performance:
Folds are not updated during insert-mode.

Startup:
--literal (file args are always literal; to expand wildcards on Windows, use
### <a id="[:n| e.g. `nvim +"n "`)" class="section-title" href="#|:n](#:n| e.g. `nvim +"n "`)" class="section-title" href="#|:n) e.g. `nvim +"n "`)">Note:</a>
Easy mode: eview, evim, nvim -y
Restricted mode: rview, rvim, nvim -Z
Vi mode: nvim -v

Test functions:
test_alloc_fail()
test_autochdir()
test_disable_char_avail()
test_feedinput()
test_garbagecollect_soon
test_getvalue()
test_ignore_error()
test_null_blob()
test_null_channel()
test_null_dict()
test_null_function()
test_null_job()
test_null_list()
test_null_partial()
test_null_string()
test_option_not_set()
test_override()
test_refcount()
test_scrollbar()
test_setmouse()
test_settime()
test_srand_seed()

TUI:
### <a id="t_xx termcap-options t_AB t_Sb t_vb t_SI" class="section-title" href="#t_xx termcap-options t_AB t_Sb t_vb t_SI">Note:</a>
Nvim does not have special `t_XX` options nor <t_XX> keycodes to configure
terminal capabilities. Instead Nvim treats the terminal as any other UI,
e.g. 'guicursor' sets the terminal cursor style if possible.

### <a id="termcap" class="section-title" href="#termcap">Note:</a>
Nvim never uses the termcap database, only [terminfo| and |builtin-terms](#terminfo| and |builtin-terms).

### <a id="xterm-8bit xterm-8-bit" class="section-title" href="#xterm-8bit xterm-8-bit">Note:</a>
Xterm can be run in a mode where it uses true 8-bit CSI.  Supporting this
requires autodetection of whether the terminal is in UTF-8 mode or non-UTF-8
mode, as the 8-bit CSI character has to be written differently in each case.
Vim issues a "request version" sequence to the terminal at startup and looks
at how the terminal is sending CSI.  Nvim does not issue such a sequence and
always uses 7-bit control sequences.

Cscope:
### <a id="cscope" class="section-title" href="#cscope">Note:</a>
Cscope has been removed in favour of LSP based solutions.


## <a id="" class="section-title" href="#">Vim Tw 78 Ts 8 Sw 2 Et Ft Help Norl</a> 




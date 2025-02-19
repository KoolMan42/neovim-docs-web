---
title: Tree Sitter
description: Some page
layout: "@layouts/MainLayout.astro"
---


## <a id="Nvim" class="section-title" href="#Nvim"> Deprecated Txt</a> 

NVIM REFERENCE MANUAL


### <a id="deprecated" class="section-title" href="#deprecated">Nvim</a>

The items listed below are deprecated: they will be removed in the future.
They should not be used in new scripts, and old scripts should be updated.


## <a id="" class="section-title" href="#">Deprecated Features</a> 

API
- *nvim_buf_clear_highlight()*	Use [nvim_buf_clear_namespace()](#nvim_buf_clear_namespace()) instead.
- *nvim_buf_set_virtual_text()*	Use [nvim_buf_set_extmark()](#nvim_buf_set_extmark()) instead.
- *nvim_command_output()*	Use [nvim_exec()](#nvim_exec()) instead.
- *nvim_execute_lua()*		Use [nvim_exec_lua()](#nvim_exec_lua()) instead.

COMMANDS
- *:rv* *:rviminfo*		Deprecated alias to [:rshada](#:rshada) command.
- *:wv* *:wviminfo*		Deprecated alias to [:wshada](#:wshada) command.

ENVIRONMENT VARIABLES
- *$NVIM_LISTEN_ADDRESS*
- Deprecated way to:
- set the server name (use [--listen| or |serverstart()](#--listen| or |serverstart()) instead)
- get the server name (use [v:servername](#v:servername) instead)
- detect a parent Nvim (use [$NVIM](#$NVIM) instead)
- Ignored if --listen is given.
- Unset by [terminal| and |jobstart()](#terminal| and |jobstart()) unless explicitly given by the "env"
option. Example:
```
call jobstart(['foo'], { 'env': { 'NVIM_LISTEN_ADDRESS': v:servername  } })

```


EVENTS
- *BufCreate*		Use [BufAdd](#BufAdd) instead.
- *EncodingChanged*	Never fired; 'encoding' is always "utf-8".
- *FileEncoding*	Never fired; equivalent to [EncodingChanged](#EncodingChanged).
- *GUIEnter*		Never fired; use [UIEnter](#UIEnter) instead.
- *GUIFailed*		Never fired.

KEYCODES
- *<MouseDown>*		Use <ScrollWheelUp> instead.
- *<MouseUp>*		Use <ScrollWheelDown> instead.

FUNCTIONS
- *buffer_exists()*	Obsolete name for [bufexists()](#bufexists()).
- *buffer_name()*	Obsolete name for [bufname()](#bufname()).
- *buffer_number()*	Obsolete name for [bufnr()](#bufnr()).
- *file_readable()*	Obsolete name for [filereadable()](#filereadable()).
- *health#report_error*	Use Lua [vim.health.report_error()](#vim.health.report_error()) instead.
- *health#report_info*	Use Lua [vim.health.report_info()](#vim.health.report_info()) instead.
- *health#report_ok*	Use Lua [vim.health.report_ok()](#vim.health.report_ok()) instead.
- *health#report_start*	Use Lua [vim.health.report_start()](#vim.health.report_start()) instead.
- *health#report_warn*	Use Lua [vim.health.report_warn()](#vim.health.report_warn()) instead.
- *highlight_exists()*	Obsolete name for [hlexists()](#hlexists()).
- *highlightID()*	Obsolete name for [hlID()](#hlID()).
- *inputdialog()*	Use [input()](#input()) instead.
- *jobclose()*		Obsolete name for [chanclose()](#chanclose())
- *jobsend()*		Obsolete name for [chansend()](#chansend())
- *last_buffer_nr()*	Obsolete name for bufnr("$").
- *rpcstop()*		Use [jobstop()](#jobstop()) instead to stop any job, or
`chanclose(id, "rpc")` to close RPC communication
without stopping the job. Use chanclose(id) to close
any socket.

HIGHLIGHTS
- *hl-VertSplit*	Use [hl-WinSeparator](#hl-WinSeparator) instead.

LSP DIAGNOSTICS
For each of the functions below, use the corresponding function in
[vim.diagnostic](#vim.diagnostic) instead (unless otherwise noted). For example, use
[vim.diagnostic.get()| instead of |vim.lsp.diagnostic.get()](#vim.diagnostic.get()| instead of |vim.lsp.diagnostic.get()).

- *vim.lsp.diagnostic.clear()*		Use [vim.diagnostic.hide()](#vim.diagnostic.hide()) instead.
- *vim.lsp.diagnostic.disable()*
- *vim.lsp.diagnostic.display()*	Use [vim.diagnostic.show()](#vim.diagnostic.show()) instead.
- *vim.lsp.diagnostic.enable()*
- *vim.lsp.diagnostic.get()*
- *vim.lsp.diagnostic.get_all()*	Use [vim.diagnostic.get()](#vim.diagnostic.get()) instead.
- *vim.lsp.diagnostic.get_count()*	Use [vim.diagnostic.get()](#vim.diagnostic.get()) instead.
- *vim.lsp.diagnostic.get_line_diagnostics()* Use [vim.diagnostic.get()](#vim.diagnostic.get()) instead.
- *vim.lsp.diagnostic.get_next()*
- *vim.lsp.diagnostic.get_next_pos()*
- *vim.lsp.diagnostic.get_prev()*
- *vim.lsp.diagnostic.get_prev_pos()*
- *vim.lsp.diagnostic.get_virtual_text_chunks_for_line()* No replacement. Use
options provided by [vim.diagnostic.config()](#vim.diagnostic.config()) to customize virtual text.
- *vim.lsp.diagnostic.goto_next()*
- *vim.lsp.diagnostic.goto_prev()*
- *vim.lsp.diagnostic.redraw()*		Use [vim.diagnostic.show()](#vim.diagnostic.show()) instead.
- *vim.lsp.diagnostic.reset()*
- *vim.lsp.diagnostic.save()*		Use [vim.diagnostic.set()](#vim.diagnostic.set()) instead.
- *vim.lsp.diagnostic.set_loclist()*	Use [vim.diagnostic.setloclist()](#vim.diagnostic.setloclist()) instead.
- *vim.lsp.diagnostic.set_qflist()*	Use [vim.diagnostic.setqflist()](#vim.diagnostic.setqflist()) instead.
- *vim.lsp.diagnostic.show_line_diagnostics()* Use [vim.diagnostic.open_float()](#vim.diagnostic.open_float()) instead.
- *vim.lsp.diagnostic.show_position_diagnostics()* Use [vim.diagnostic.open_float()](#vim.diagnostic.open_float()) instead.

The following are deprecated without replacement. These functions are moved
internally and are no longer exposed as part of the API. Instead, use
[vim.diagnostic.config()| and |vim.diagnostic.show()](#vim.diagnostic.config()| and |vim.diagnostic.show()).

- *vim.lsp.diagnostic.set_signs()*
- *vim.lsp.diagnostic.set_underline()*
- *vim.lsp.diagnostic.set_virtual_text()*

LSP FUNCTIONS
- *vim.lsp.buf.range_code_action()*	Use [vim.lsp.buf.code_action()](#vim.lsp.buf.code_action()) with
the `range` parameter.
- *vim.lsp.util.diagnostics_to_items()*	Use [vim.diagnostic.toqflist()](#vim.diagnostic.toqflist()) instead.
- *vim.lsp.util.set_qflist()*		Use [setqflist()](#setqflist()) instead.
- *vim.lsp.util.set_loclist()*		Use [setloclist()](#setloclist()) instead.
- *vim.lsp.buf_get_clients()*		Use [vim.lsp.get_active_clients()](#vim.lsp.get_active_clients()) with
{buffer = bufnr} instead.
- *vim.lsp.buf.formatting()*		Use [vim.lsp.buf.format()](#vim.lsp.buf.format()) with
{async = true} instead.
- *vim.lsp.buf.range_formatting()*	Use [vim.lsp.formatexpr()](#vim.lsp.formatexpr())
or [vim.lsp.buf.format()](#vim.lsp.buf.format()) instead.

LUA
- *vim.register_keystroke_callback()* 	Use [vim.on_key()](#vim.on_key()) instead.

NORMAL COMMANDS
- *]f* *[f*		Same as "gf".

OPTIONS
- *cpo-<* *:menu-<special>* *:menu-special* *:map-<special>* *:map-special*
`<>` notation is always enabled.
- *'exrc'* *'ex'*	Security risk: downloaded files could include
a malicious .nvimrc or .exrc file. See 'secure'.
Recommended alternative: define an autocommand in your
[vimrc](#vimrc) to set options for a matching directory.
- 'gdefault'		Enables the [:substitute](#:substitute) flag 'g' by default.
- *'fe'*		'fenc'+'enc' before Vim 6.0; no longer used.
- *'highlight'* *'hl'*	Names of builtin [highlight-groups](#highlight-groups) cannot be changed.
- *'langnoremap'*	Deprecated alias to 'nolangremap'.
- 'sessionoptions'	Flags "unix", "slash" are ignored and always enabled.
- *'vi'*
- 'viewoptions'		Flags "unix", "slash" are ignored and always enabled.
- *'viminfo'*		Deprecated alias to 'shada' option.
- *'viminfofile'*	Deprecated alias to 'shadafile' option.

UI EXTENSIONS
- *ui-wildmenu*		Use [ui-cmdline| with |ui-popupmenu](#ui-cmdline| with |ui-popupmenu) instead. Enabled
by the `ext_wildmenu` [ui-option](#ui-option). Emits these events:
- `["wildmenu_show", items]`
- `["wildmenu_select", selected]`
- `["wildmenu_hide"]`

VARIABLES
- *b:terminal_job_pid*	PID of the top-level process in a [:terminal](#:terminal).
Use `jobpid(&channel)` instead.


vim:noet:tw=78:ts=8:ft=help:norl:


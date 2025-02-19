---
title: Tree Sitter
description: Some page
layout: "@layouts/MainLayout.astro"
---


## <a id="LSP Extension" class="section-title" href="#LSP Extension"> Lsp Extension Txt</a> 

NVIM REFERENCE MANUAL


The `vim.lsp` Lua module is a framework for building LSP plugins.

1. Start with [vim.lsp.start_client()| and |vim.lsp.buf_attach_client()](#vim.lsp.start_client()| and |vim.lsp.buf_attach_client()).
2. Peek at the API:
```
:lua print(vim.inspect(vim.lsp))

```
  3. See [lsp-extension-example](#lsp-extension-example) for a full example.


## <a id="lsp-extension-example" class="section-title" href="#lsp-extension-example">Lsp Example</a> 

This example is for plugin authors or users who want a lot of control. If you
are just getting started see [lsp-quickstart](#lsp-quickstart).

For more advanced configurations where just filtering by filetype isn't
sufficient, you can use the `vim.lsp.start_client()` and
`vim.lsp.buf_attach_client()` commands to easily customize the configuration
however you please. For example, if you want to do your own filtering, or
start a new LSP client based on the root directory for working with multiple
projects in a single session. To illustrate, the following is a fully working
Lua example.

The example will:
1. Check for each new buffer whether or not we want to start an LSP client.
2. Try to find a root directory by ascending from the buffer's path.
3. Create a new LSP for that root directory if one doesn't exist.
4. Attach the buffer to the client for that root directory.
```
-- Some path manipulation utilities
local function is_dir(filename)
local stat = vim.loop.fs_stat(filename)
return stat and stat.type == 'directory' or false
end

local path_sep = vim.loop.os_uname().sysname == "Windows" and "\\" or "/"
-- Assumes filepath is a file.
local function dirname(filepath)
local is_changed = false
local result = filepath:gsub(path_sep.."([^"..path_sep.."]+)$", function()
is_changed = true
return ""
end)
return result, is_changed
end

local function path_join(...)
return table.concat(vim.tbl_flatten {...}, path_sep)
end

-- Ascend the buffer's path until we find the rootdir.
-- is_root_path is a function which returns bool
local function buffer_find_root_dir(bufnr, is_root_path)
local bufname = vim.api.nvim_buf_get_name(bufnr)
if vim.fn.filereadable(bufname) == 0 then
return nil
end
local dir = bufname
-- Just in case our algorithm is buggy, don't infinite loop.
for _ = 1, 100 do
local did_change
dir, did_change = dirname(dir)
if is_root_path(dir, bufname) then
return dir, bufname
end
-- If we can't ascend further, then stop looking.
if not did_change then
return nil
end
end
end

-- A table to store our root_dir to client_id lookup. We want one LSP per
-- root directory, and this is how we assert that.
local javascript_lsps = {}
-- Which filetypes we want to consider.
local javascript_filetypes = {
["javascript.jsx"] = true;
["javascript"]     = true;
["typescript"]     = true;
["typescript.jsx"] = true;
}

-- Create a template configuration for a server to start, minus the root_dir
-- which we will specify later.
local javascript_lsp_config = {
name = "javascript";
cmd = { path_join(os.getenv("JAVASCRIPT_LANGUAGE_SERVER_DIRECTORY"), "lib", "language-server-stdio.js") };
}

-- This needs to be global so that we can call it from the autocmd.
function check_start_javascript_lsp()
local bufnr = vim.api.nvim_get_current_buf()
-- Filter which files we are considering.
if not javascript_filetypes[vim.api.nvim_buf_get_option(bufnr, 'filetype')] then
return
end
-- Try to find our root directory. We will define this as a directory which contains
-- node_modules. Another choice would be to check for `package.json`, or for `.git`.
local root_dir = buffer_find_root_dir(bufnr, function(dir)
return is_dir(path_join(dir, 'node_modules'))
-- return vim.fn.filereadable(path_join(dir, 'package.json')) == 1
-- return is_dir(path_join(dir, '.git'))
end)
-- We couldn't find a root directory, so ignore this file.
if not root_dir then return end

-- Check if we have a client already or start and store it.
local client_id = javascript_lsps[root_dir]
if not client_id then
local new_config = vim.tbl_extend("error", javascript_lsp_config, {
root_dir = root_dir;
})
client_id = vim.lsp.start_client(new_config)
javascript_lsps[root_dir] = client_id
end
-- Finally, attach to the buffer to track changes. This will do nothing if we
-- are already attached.
vim.lsp.buf_attach_client(bufnr, client_id)
end

### <a id="vim.api.nvim_command [[autocmd BufReadPost  lua check_start_javascript_lsp()]]" class="section-title" href="#vim.api.nvim_command [[autocmd BufReadPost  lua check_start_javascript_lsp()]]">Note:</a>

```


vim:tw=78:ts=8:ft=help:norl:


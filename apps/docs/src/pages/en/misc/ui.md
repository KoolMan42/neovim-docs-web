---
title: Tree Sitter
description: Some page
layout: "@layouts/MainLayout.astro"
---


## <a id="" class="section-title" href="#">*Ui.Txt*	Nvim</a> 

NVIM REFERENCE MANUAL


### <a id="UI ui" class="section-title" href="#UI ui">Nvim UI protocol</a>

Type [gO](#gO) to see the table of contents.


## <a id="ui-events" class="section-title" href="#ui-events">UI Events</a> 

UIs can be implemented as external client processes communicating with Nvim
over the RPC API. The default UI model is a terminal-like grid with a single,
monospace font. The UI can opt-in to have windows drawn on separate grids, and
have some elements ("widgets") presented by the UI itself rather than by Nvim
("externalized").

### <a id="ui-option" class="section-title" href="#ui-option">Note:</a>
Call [nvim_ui_attach()](#nvim_ui_attach()) to tell Nvim that your program wants to draw the Nvim
screen grid with a size of width × height cells. This is typically done by an
embedder at startup (see [ui-startup](#ui-startup)), but UIs can also connect to a running
Nvim instance and invoke nvim_ui_attach(). The `options` parameter is a map
with these (optional) keys:

### <a id="ui-rgb" class="section-title" href="#ui-rgb">Note:</a>
- `rgb`			Decides the color format.
- true:	(default) 24-bit RGB colors
- false:	Terminal colors (8-bit, max 256)

### <a id="ui-override" class="section-title" href="#ui-override">Note:</a>
- `override`		Decides how UI capabilities are resolved.
- true:	Enable requested UI capabilities, even if not
supported by all connected UIs (including [TUI](#TUI)).
- false: (default) Disable UI capabilities not
supported by all connected UIs (including TUI).

### <a id="ui-ext-options" class="section-title" href="#ui-ext-options">Note:</a>
- `ext_cmdline`		Externalize the cmdline. [ui-cmdline](#ui-cmdline)
- `ext_hlstate`		Detailed highlight state. [ui-hlstate](#ui-hlstate)
Sets `ext_linegrid` implicitly.
- `ext_linegrid`	Line-based grid events. [ui-linegrid](#ui-linegrid)
Deactivates [ui-grid-old](#ui-grid-old) implicitly.
- `ext_messages`	Externalize messages. [ui-messages](#ui-messages)
Sets `ext_linegrid` and `ext_cmdline` implicitly.
- `ext_multigrid`	Per-window grid events. [ui-multigrid](#ui-multigrid)
Sets `ext_linegrid` implicitly.
- `ext_popupmenu`	Externalize [popupmenu-completion](#popupmenu-completion) and
'wildmenu'. [ui-popupmenu](#ui-popupmenu)
- `ext_tabline`		Externalize the tabline. [ui-tabline](#ui-tabline)
- `ext_termcolors`	Use external default colors.
- `term_name`		Sets the name of the terminal 'term'.
- `term_colors`		Sets the number of supported colors 't_Co'.
- `term_background`	Sets the default value of 'background'.
- `stdin_fd`		Read buffer from `fd` as if it was a stdin pipe
This option can only used by [--embed](#--embed) ui,
see [ui-startup-stdin](#ui-startup-stdin).

Specifying an unknown option is an error; UIs can check the [api-metadata](#api-metadata)
`ui_options` key for supported options.

By default Nvim requires all connected UIs to support the same capabilities,
thus the active capabilities are the intersection of those requested. UIs may
specify [ui-override](#ui-override) to invert this behavior (useful for debugging). The
"option_set" event announces which capabilities are active.

Nvim sends RPC notifications to all attached UIs, with method name "redraw"
and a single argument: an array (batch) of screen "update events". Each update
event is itself an array whose first element is the event name and remaining
elements are event-parameter tuples. Thus multiple events of the same kind can
be sent contiguously without repeating the event name.

Example of a typical "redraw" batch in a single RPC notification:
```

['notification', 'redraw',
[
['grid_resize', [2, 77, 36]],
['grid_line',
[2, 0, 0, [[' ' , 0, 77]]],
[2, 1, 0, [['~', 7], [' ', 7, 76]]],
[2, 9, 0, [['~', 7], [' ', 7, 76]]], 
...
[2, 35, 0, [['~', 7], [' ', 7, 76]]],
[1, 36, 0, [['[', 9], ['N'], ['o'], [' '], ['N'], ['a'], ['m'], ['e'], [']']]],
[1, 36, 9, [[' ', 9, 50]]],
[1, 36, 59, [['0', 9], [','], ['0'], ['-' ], ['1'], [' ', 9, 10], ['A'], ['l', 9, 2]]]
],
['msg_showmode', [[]]],
['win_pos', [2, 1000, 0, 0, 77, 36]],
['grid_cursor_goto', [2, 0, 0]],
['flush', []]
]
]

Events must be handled in-order. Nvim sends a "flush" event when it has
completed a redraw of the entire screen (so all windows have a consistent view
of buffer state, options, etc.). Multiple "redraw" batches may be sent before
the entire screen has been redrawn, with "flush" following only the last
batch. The user should only see the final state (when "flush" is sent), not
any intermediate state while processing part of the batch array, nor after
a batch not ending with "flush".

By default, Nvim sends [ui-global| and |ui-grid-old](#ui-global| and |ui-grid-old) events (for backwards
compatibility); these suffice to implement a terminal-like interface. However
the new [ui-linegrid](#ui-linegrid) represents text more efficiently (especially highlighted
text), and allows UI capabilities requiring multiple grids. New UIs should
implement [ui-linegrid| instead of |ui-grid-old](#ui-linegrid| instead of |ui-grid-old).

Nvim optionally sends various screen elements "semantically" as structured
events instead of raw grid-lines, as specified by [ui-ext-options](#ui-ext-options). The UI
must present such elements itself, Nvim will not draw them on the grid.

Future versions of Nvim may add new update kinds and may append new parameters
to existing update kinds. Clients must be prepared to ignore such extensions,
for forward-compatibility. [api-contract](#api-contract)


## <a id="ui-startup" class="section-title" href="#ui-startup">UI Startup</a> 

UI embedders (clients that start Nvim with [--embed](#--embed) and later call
[nvim_ui_attach()|) must start Nvim without |--headless](#nvim_ui_attach()|) must start Nvim without |--headless):
```
nvim --embed
Nvim will pause before loading startup files and reading buffers, so the UI
has a chance to invoke requests and do early initialization. Startup will
continue as soon as the UI invokes [nvim_ui_attach()](#nvim_ui_attach()).

A simple UI only needs to do a single [nvim_ui_attach()](#nvim_ui_attach()) request and then
prepare to handle any UI event. A more featureful UI, which might need
additional configuration of the Nvim process, should use the following startup
procedure:

1. Invoke [nvim_get_api_info()](#nvim_get_api_info()), if needed to setup the client library and/or
to get the list of supported UI extensions.

2. Do any configuration that should be happen before user config is loaded.
Buffers and windows are not available at this point, but this could be used
to set [g:](#g:) variables visible to init.vim

3. If the UI wants to do additional setup after user config is loaded,
register a VimEnter autocmd:
```
### <a id="nvim_command("autocmd VimEnter  call rpcrequest(1, 'vimenter')")" class="section-title" href="#nvim_command("autocmd VimEnter  call rpcrequest(1, 'vimenter')")">Note:</a>

4. Now invoke [nvim_ui_attach()](#nvim_ui_attach()). The UI must handle user input by now:
sourcing init.vim and loading buffers might lead to blocking prompts.

5. If step 3 was used, Nvim will send a blocking "vimenter" request to the UI.
Inside this request handler, the UI can safely do any initialization before
entering normal mode, for example reading variables set by init.vim.

### <a id="ui-startup-stdin" class="section-title" href="#ui-startup-stdin">Note:</a>
An UI can support the native read from stdin feature as invoked with
`command [ nvim -` for the builtin TUI. |--](# nvim -` for the builtin TUI. |--)
The embedding process can detect that its stdin is open to a file which
not is a terminal, just like nvim does. It then needs to forward this fd
to Nvim. As fd=0 is already is used to send rpc data from the embedder to
Nvim, it needs to use some other file descriptor, like fd=3 or higher.

Then, `stdin_fd` option should be passed to `nvim_ui_attach` and nvim will
implicitly read it as a buffer. This option can only be used when Nvim is
launched with `--embed` option, as described above.


## <a id="ui-global" class="section-title" href="#ui-global">Global Events</a> 

The following UI events are always emitted, and describe global state of
the editor.

["set_title", title] ~
["set_icon", icon] ~
Set the window title, and icon (minimized) window title, respectively.
In windowing systems not distinguishing between the two, "set_icon"
can be ignored.

["mode_info_set", cursor_style_enabled, mode_info] ~
`cursor_style_enabled` is a boolean indicating if the UI should set
the cursor style. `mode_info` is a list of mode property maps. The
current mode is given by the `mode_idx` field of the `mode_change`
event.

Each mode property map may contain these keys:

KEY		DESCRIPTION ~
`cursor_shape`:	"block", "horizontal", "vertical"
`cell_percentage`: Cell % occupied by the cursor.
`blinkwait`, `blinkon`, `blinkoff`: See [cursor-blinking](#cursor-blinking).
`attr_id`:	Cursor attribute id (defined by `hl_attr_define`).
When attr_id is 0, the background and foreground
colors should be swapped.
`attr_id_lm`:	Cursor attribute id for when 'langmap' is active.
`short_name`:	Mode code name, see 'guicursor'.
`name`:		Mode descriptive name.
`mouse_shape`:	(To be implemented.)

Some keys are missing in some modes.

The following keys are deprecated:

`hl_id`:	Use `attr_id` instead.
`hl_lm`:	Use `attr_id_lm` instead.

["option_set", name, value] ~
UI-related option changed, where `name` is one of:

- 'arabicshape'
- 'ambiwidth'
- 'emoji'
- 'guifont'
- 'guifontwide'
- 'linespace'
- 'mousefocus'
- 'mousemoveevent'
- 'pumblend'
- 'showtabline'
- 'termguicolors'
- "ext_*" (all [ui-ext-options](#ui-ext-options))

Triggered when the UI first connects to Nvim, and whenever an option
is changed by the user or a plugin.

Options are not represented here if their effects are communicated in
other UI events. For example, instead of forwarding the 'mouse' option
value, the "mouse_on" and "mouse_off" UI events directly indicate if
mouse support is active. Some options like 'ambiwidth' have already
taken effect on the grid, where appropriate empty cells are added,
however a UI might still use such options when rendering raw text
sent from Nvim, like for [ui-cmdline](#ui-cmdline).

["mode_change", mode, mode_idx] ~
Editor mode changed.  The `mode` parameter is a string representing
the current mode. `mode_idx` is an index into the array emitted in
the `mode_info_set` event. UIs should change the cursor style
according to the properties specified in the corresponding item. The
set of modes reported will change in new versions of Nvim, for
instance more submodes and temporary states might be represented as
separate modes.

["mouse_on"] ~
["mouse_off"] ~
'mouse' was enabled/disabled in the current editor mode. Useful for
a terminal UI, or embedding into an application where Nvim mouse would
conflict with other usages of the mouse. Other UI:s may ignore this event.

["busy_start"] ~
["busy_stop"] ~
Indicates to the UI that it must stop rendering the cursor. This event
is misnamed and does not actually have anything to do with busyness.

["suspend"] ~
[:suspend| command or |CTRL-Z](#:suspend| command or |CTRL-Z) mapping is used. A terminal client (or
another client where it makes sense) could suspend itself.  Other
clients can safely ignore it.

["update_menu"] ~
The menu mappings changed.

["bell"] ~
["visual_bell"] ~
Notify the user with an audible or visual bell, respectively.

["flush"] ~
Nvim is done redrawing the screen. For an implementation that renders
to an internal buffer, this is the time to display the redrawn parts
to the user.


## <a id="ui-linegrid" class="section-title" href="#ui-linegrid">Grid Events (Line-Based)</a> 

Activated by the `ext_linegrid` [ui-option](#ui-option). Recommended for all new UIs.
Deactivates [ui-grid-old](#ui-grid-old) implicitly.

The biggest change compared to [ui-grid-old](#ui-grid-old) is to use a single `grid_line`
event to update the contents of a screen line (whereas the old protocol used
a combination of cursor, highlight and text events)

Most of these events take a `grid` index as first parameter.  Grid 1 is the
global grid used by default for the entire editor screen state. The
`ext_linegrid` capability by itself will never cause any additional grids to
be created; to enable per-window grids, activate [ui-multigrid](#ui-multigrid).

Highlight attribute groups are predefined. UIs should maintain a table to map
numerical highlight ids to the actual attributes.

["grid_resize", grid, width, height] ~
Resize a `grid`. If `grid` wasn't seen by the client before, a new grid is
being created with this size.

["default_colors_set", rgb_fg, rgb_bg, rgb_sp, cterm_fg, cterm_bg] ~
The first three arguments set the default foreground, background and
special colors respectively. `cterm_fg` and `cterm_bg` specifies the
default color codes to use in a 256-color terminal.

The RGB values will always be valid colors, by default. If no
colors have been set, they will default to black and white, depending
on 'background'. By setting the `ext_termcolors` option, instead
-1 will be used for unset colors. This is mostly useful for a TUI
implementation, where using the terminal builtin ("ANSI") defaults
are expected.

Note: Unlike the corresponding [ui-grid-old](#ui-grid-old) events, the screen is not
always cleared after sending this event. The UI must repaint the
screen with changed background color itself.

### <a id="ui-event-hl_attr_define" class="section-title" href="#ui-event-hl_attr_define">Note:</a>
["hl_attr_define", id, rgb_attr, cterm_attr, info] ~
Add a highlight with `id`  to the highlight table, with the
attributes specified by the `rgb_attr` and `cterm_attr` dicts, with the
following (all optional) keys.

`foreground`:		foreground color.
`background`:		background color.
`special`:		color to use for various underlines, when
present.
`reverse`:		reverse video. Foreground and background colors
are switched.
`italic`:		italic text.
`bold`:			bold text.
`strikethrough`:	struckthrough text.
`underline`:		underlined text. The line has `special` color.
`undercurl`:		undercurled text. The curl has `special` color.
`underdouble`:		double underlined text. The lines have `special` color.
`underdotted`:		underdotted text. The dots have `special` color.
`underdashed`:		underdashed text. The dashes have `special` color.
`blend`:		Blend level (0-100). Could be used by UIs to
support blending floating windows to the
background or to signal a transparent cursor.

For absent color keys the default color should be used. Don't store
the default value in the table, rather a sentinel value, so that
a changed default color will take effect.
All boolean keys default to false, and will only be sent when they
are true.

Highlights are always transmitted both for both the RGB format and as
terminal 256-color codes, as the `rgb_attr` and `cterm_attr` parameters
respectively. The [ui-rgb](#ui-rgb) option has no effect effect anymore.
Most external UIs will only need to store and use the `rgb_attr`
attributes.

`id` 0 will always be used for the default highlight with colors defined
by `default_colors_set` and no styles applied.

Note: Nvim may reuse `id` values if its internal highlight table is full.
In that case Nvim will always issue redraws of screen cells that are
affected by redefined ids, so UIs do not need to keep track of this
themselves.

`info` is an empty array by default, and will be used by the
[ui-hlstate](#ui-hlstate) extension explained below.

["hl_group_set", name, hl_id] ~
The bulitin highlight group `name` was set to use the attributes `hl_id`
defined by a previous `hl_attr_define` call. This event is not needed
to render the grids which use attribute ids directly, but is useful
for an UI who want to render its own elements with consistent
highlighting. For instance an UI using [ui-popupmenu](#ui-popupmenu) events, might
use the [hl-Pmenu](#hl-Pmenu) family of builtin highlights.

### <a id="ui-event-grid_line" class="section-title" href="#ui-event-grid_line">Note:</a>
["grid_line", grid, row, col_start, cells] ~
Redraw a continuous part of a `row` on a `grid`, starting at the column
`col_start`. `cells` is an array of arrays each with 1 to 3 items:
`[text(, hl_id, repeat)]` . `text` is the UTF-8 text that should be put in
a cell, with the highlight `hl_id` defined by a previous `hl_attr_define`
call.  If `hl_id` is not present the most recently seen `hl_id` in
the same call should be used (it is always sent for the first
cell in the event). If `repeat` is present, the cell should be
repeated `repeat` times (including the first time), otherwise just
once.

The right cell of a double-width char will be represented as the empty
string. Double-width chars never use `repeat`.

If the array of cell changes doesn't reach to the end of the line, the
rest should remain unchanged. A whitespace char, repeated
enough to cover the remaining line, will be sent when the rest of the
line should be cleared.

["grid_clear", grid] ~
Clear a `grid`.

["grid_destroy", grid] ~
`grid` will not be used anymore and the UI can free any data associated
with it.

["grid_cursor_goto", grid, row, column] ~
Makes `grid` the current grid and `row, column` the cursor position on this
grid.  This event will be sent at most once in a `redraw` batch and
indicates the visible cursor position.

["grid_scroll", grid, top, bot, left, right, rows, cols] ~
Scroll a region of `grid`. This is semantically unrelated to editor
[scrolling](#scrolling), rather this is an optimized way to say "copy these screen
cells".

The following diagrams show what happens per scroll direction.
"===" represents the SR (scroll region) boundaries.
"---" represents the moved rectangles.
Note that dst and src share a common region.

If `rows` is bigger than 0, move a rectangle in the SR up, this can
happen while scrolling down.
```
+-------------------------+
[ (clipped above SR)      ](# (clipped above SR)      )            ^
[=========================| dst_top    ](#=========================| dst_top    )
[ dst (still in SR)       |            ](# dst (still in SR)       |            )
+-------------------------+ src_top    |
[ src (moved up) and dst  |            ](# src (moved up) and dst  |            )
[-------------------------| dst_bot    ](#-------------------------| dst_bot    )
[ src (invalid)           |            ](# src (invalid)           |            )
+=========================+ src_bot

```

If `rows` is less than zero, move a rectangle in the SR down, this can
happen while scrolling up.
```
+=========================+ src_top
[ src (invalid)           |            ](# src (invalid)           |            )
[------------------------ | dst_top    ](#------------------------ | dst_top    )
[ src (moved down) and dst|            ](# src (moved down) and dst|            )
+-------------------------+ src_bot    |
[ dst (still in SR)       |            ](# dst (still in SR)       |            )
[=========================| dst_bot    ](#=========================| dst_bot    )
[ (clipped below SR)      ](# (clipped below SR)      )            v
+-------------------------+

```

`cols` is always zero in this version of Nvim, and reserved for future
use. 

Note when updating code from [ui-grid-old](#ui-grid-old) events: ranges are
end-exclusive, which is consistent with API conventions, but different
from `set_scroll_region` which was end-inclusive.

The scrolled-in area will be filled using [ui-event-grid_line](#ui-event-grid_line) directly
after the scroll event. The UI thus doesn't need to clear this area as
part of handling the scroll event.


## <a id="ui-grid-old" class="section-title" href="#ui-grid-old">Grid Events (Cell-Based)</a> 

This is the legacy representation of the screen grid, emitted if [ui-linegrid](#ui-linegrid)
is not active. New UIs should implement [ui-linegrid](#ui-linegrid) instead.

["resize", width, height] ~
The grid is resized to `width` and `height` cells.

["clear"] ~
Clear the grid.

["eol_clear"] ~
Clear from the cursor position to the end of the current line.

["cursor_goto", row, col] ~
Move the cursor to position (row, col). Currently, the same cursor is
used to define the position for text insertion and the visible cursor.
However, only the last cursor position, after processing the entire
array in the "redraw" event, is intended to be a visible cursor
position.

["update_fg", color] ~
["update_bg", color] ~
["update_sp", color] ~
Set the default foreground, background and special colors
respectively.

### <a id="ui-event-highlight_set" class="section-title" href="#ui-event-highlight_set">Note:</a>
["highlight_set", attrs] ~
Set the attributes that the next text put on the grid will have.
`attrs` is a dict with the keys below. Any absent key is reset
to its default value. Color defaults are set by the `update_fg` etc
updates. All boolean keys default to false.

`foreground`:	foreground color.
`background`:	background color.
`special`:	color to use for various underlines, when present.
`reverse`:	reverse video. Foreground and background colors are
switched.
`italic`:	italic text.
`bold`:		bold text.
`strikethrough`:  struckthrough text.
`underline`:	underlined text. The line has `special` color.
`undercurl`:	undercurled text. The curl has `special` color.
`underdouble`:	double underlined text. The lines have `special` color.
`underdotted`:	underdotted text. The dots have `special` color.
`underdashed`:	underdashed text. The dashes have `special` color.

["put", text] ~
The (utf-8 encoded) string `text` is put at the cursor position
(and the cursor is advanced), with the highlights as set by the
last `highlight_set` update.

["set_scroll_region", top, bot, left, right] ~
Define the scroll region used by `scroll` below.

Note: ranges are end-inclusive, which is inconsistent with API
conventions.

["scroll", count] ~
Scroll the text in the scroll region. The diagrams below illustrate
what will happen, depending on the scroll direction. "=" is used to
represent the SR(scroll region) boundaries and "-" the moved rectangles.
Note that dst and src share a common region.

If count is bigger than 0, move a rectangle in the SR up, this can
happen while scrolling down.
```
+-------------------------+
[ (clipped above SR)      ](# (clipped above SR)      )            ^
[=========================| dst_top    ](#=========================| dst_top    )
[ dst (still in SR)       |            ](# dst (still in SR)       |            )
+-------------------------+ src_top    |
[ src (moved up) and dst  |            ](# src (moved up) and dst  |            )
[-------------------------| dst_bot    ](#-------------------------| dst_bot    )
[ src (cleared)           |            ](# src (cleared)           |            )
+=========================+ src_bot

```

If count is less than zero, move a rectangle in the SR down, this can
happen while scrolling up.
```
+=========================+ src_top
[ src (cleared)           |            ](# src (cleared)           |            )
[------------------------ | dst_top    ](#------------------------ | dst_top    )
[ src (moved down) and dst|            ](# src (moved down) and dst|            )
+-------------------------+ src_bot    |
[ dst (still in SR)       |            ](# dst (still in SR)       |            )
[=========================| dst_bot    ](#=========================| dst_bot    )
[ (clipped below SR)      ](# (clipped below SR)      )            v
+-------------------------+

```



## <a id="ui-hlstate" class="section-title" href="#ui-hlstate">Detailed Highlight State Extension</a> 

Activated by the `ext_hlstate` [ui-option](#ui-option).
Activates [ui-linegrid](#ui-linegrid) implicitly.

By default Nvim will only describe grid cells using the final calculated
highlight attributes, as described by the dict keys in [ui-event-highlight_set](#ui-event-highlight_set).
The `ext_hlstate` extension allows to the UI to also receive a semantic
description of the highlights active in a cell. In this mode highlights will be
predefined in a table, see [ui-event-hl_attr_define| and |ui-event-grid_line](#ui-event-hl_attr_define| and |ui-event-grid_line).
The `info` parameter in `hl_attr_define` will contain a semantic description
of the highlights. As highlight groups can be combined, this will be an array
of items, with the item with highest priority last. Each item is a dictionary
with the following possible keys:

`kind`:	always present. One of the following values:
"ui":       Builtin UI highlight. [highlight-groups](#highlight-groups)
"syntax":   Highlight applied to a buffer by a syntax declaration or
other runtime/plugin functionality such as
[nvim_buf_add_highlight()](#nvim_buf_add_highlight())
"terminal": highlight from a process running in a [terminal-emulator](#terminal-emulator).
Contains no further semantic information.
`ui_name`:	Highlight name from [highlight-groups](#highlight-groups). Only for "ui" kind.
`hi_name`:	Name of the final [:highlight](#:highlight) group where the used
attributes are defined.
`id`:	Unique numeric id representing this item.

Note: "ui" items will have both `ui_name` and `hi_name` present. These can
differ, because the builtin group was linked to another group [:hi-link](#:hi-link) , or
because 'winhighlight' was used. UI items will be transmitted, even if the
highlight group is cleared, so `ui_name` can always be used to reliably identify
screen elements, even if no attributes have been applied.


## <a id="ui-multigrid" class="section-title" href="#ui-multigrid">Multigrid Events</a> 

Activated by the `ext_multigrid` [ui-option](#ui-option).
Activates [ui-linegrid](#ui-linegrid) implicitly.

See [ui-linegrid](#ui-linegrid) for grid events.
See [nvim_ui_try_resize_grid()](#nvim_ui_try_resize_grid()) to request changing the grid size.
See [nvim_input_mouse()](#nvim_input_mouse()) for sending mouse events to Nvim.

The multigrid extension gives UIs more control over how windows are displayed:
- UIs receive updates on a separate grid for each window.
- UIs can set the grid size independently of how much space the window
occupies on the global layout. So the UI could use a different font size
per-window. Or reserve space around the border of the window for its own
elements, such as scrollbars from the UI toolkit.
- A dedicated grid is used for messages, which may scroll over the window
area. (Alternatively [ui-messages](#ui-messages) can be used).

By default, the grid size is handled by Nvim and set to the outer grid size
(i.e. the size of the window frame in Nvim) whenever the split is created.
Once a UI sets a grid size, Nvim does not handle the size for that grid and
the UI must change the grid size whenever the outer size is changed. To
delegate grid-size handling back to Nvim, request the size (0, 0).

A window can be hidden and redisplayed without its grid being deallocated.
This can happen multiple times for the same window, for instance when switching
tabs.

["win_pos", grid, win, start_row, start_col, width, height] ~
Set the position and size of the grid in Nvim (i.e. the outer grid
size). If the window was previously hidden, it should now be shown
again.

["win_float_pos", grid, win, anchor, anchor_grid, anchor_row, anchor_col, focusable] ~
Display or reconfigure floating window `win`. The window should be
displayed above another grid `anchor_grid` at the specified position
`anchor_row` and `anchor_col`. For the meaning of `anchor` and more
details of positioning, see [nvim_open_win()](#nvim_open_win()).

["win_external_pos", grid, win] ~
Display or reconfigure external window `win`. The window should be
displayed as a separate top-level window in the desktop environment,
or something similar.

["win_hide", grid] ~
Stop displaying the window. The window can be shown again later.

["win_close", grid] ~
Close the window.

["msg_set_pos", grid, row, scrolled, sep_char] ~
Display messages on `grid`.  The grid will be displayed at `row` on
the default grid (grid=1), covering the full column width. `scrolled`
indicates whether the message area has been scrolled to cover other
grids. It can be useful to draw a separator then [msgsep](#msgsep). The Builtin
TUI draws a full line filled with `sep_char` ('fillchars' msgsep
field) and [hl-MsgSeparator](#hl-MsgSeparator) highlight.

When [ui-messages](#ui-messages) is active, no message grid is used, and this event
will not be sent.

["win_viewport", grid, win, topline, botline, curline, curcol] ~
Indicates the range of buffer text displayed in the window, as well
as the cursor position in the buffer. All positions are zero-based.
`botline` is set to one more than the line count of the buffer, if
there are filler lines past the end.

["win_extmark", grid, win, ns_id, mark_id, row, col] ~
Updates the position of an extmark which is currently visible in a
window. Only emitted if the mark has the `ui_watched` attribute.


## <a id="ui-popupmenu" class="section-title" href="#ui-popupmenu">Popupmenu Events</a> 

Activated by the `ext_popupmenu` [ui-option](#ui-option).

This UI extension delegates presentation of the [popupmenu-completion](#popupmenu-completion) and
command-line 'wildmenu'.

["popupmenu_show", items, selected, row, col, grid] ~
Show [popupmenu-completion](#popupmenu-completion). `items` is an array of completion items
to show; each item is an array of the form [word, kind, menu, info] as
defined at [complete-items](#complete-items), except that `word` is replaced by `abbr`
if present.  `selected` is the initially-selected item, a zero-based
index into the array of items (-1 if no item is selected). `row` and
`col` give the anchor position, where the first character of the
completed word will be. When [ui-multigrid](#ui-multigrid) is used, `grid` is the
grid for the anchor position. When `ext_cmdline` is active, `grid` is
set to -1 to indicate the popupmenu should be anchored to the external
cmdline. Then `col` will be a byte position in the cmdline text.

["popupmenu_select", selected] ~
Select an item in the current popupmenu. `selected` is a zero-based
index into the array of items from the last popupmenu_show event, or
-1 if no item is selected.

["popupmenu_hide"] ~
Hide the popupmenu.


## <a id="ui-tabline" class="section-title" href="#ui-tabline">Tabline Events</a> 

Activated by the `ext_tabline` [ui-option](#ui-option).

["tabline_update", curtab, tabs, curbuf, buffers] ~
Tabline was updated. UIs should present this data in a custom tabline
widget. Note: options `curbuf` + `buffers` were added in API7.
curtab:   Current Tabpage
tabs:     List of Dicts [{ "tab": Tabpage, "name": String }, ...]
curbuf:   Current buffer handle.
buffers:  List of Dicts [{ "buffer": buffer handle, "name": String}, ...]


## <a id="ui-cmdline" class="section-title" href="#ui-cmdline">Cmdline Events</a> 

Activated by the `ext_cmdline` [ui-option](#ui-option).

This UI extension delegates presentation of the [cmdline](#cmdline) (except 'wildmenu').
For command-line 'wildmenu' UI events, activate [ui-popupmenu](#ui-popupmenu).

["cmdline_show", content, pos, firstc, prompt, indent, level] ~
content: List of [attrs, string]
[[{}, "t"], [attrs, "est"], ...]

Triggered when the cmdline is displayed or changed.
The `content` is the full content that should be displayed in the
cmdline, and the `pos` is the position of the cursor that in the
cmdline. The content is divided into chunks with different highlight
attributes represented as a dict (see [ui-event-highlight_set](#ui-event-highlight_set)).

`firstc` and `prompt` are text, that if non-empty should be
displayed in front of the command line. `firstc` always indicates
built-in command lines such as `:` (ex command) and `/` `?` (search),
while `prompt` is an [input()](#input()) prompt. `indent` tells how many spaces
the content should be indented.

The Nvim command line can be invoked recursively, for instance by
typing `<c-r>=` at the command line prompt. The `level` field is used
to distinguish different command lines active at the same time. The
first invoked command line has level 1, the next recursively-invoked
prompt has level 2. A command line invoked from the [cmdline-window](#cmdline-window)
has a higher level than than the edited command line.

["cmdline_pos", pos, level] ~
Change the cursor position in the cmdline.

["cmdline_special_char", c, shift, level] ~
Display a special char in the cmdline at the cursor position. This is
typically used to indicate a pending state, e.g. after [c_CTRL-V](#c_CTRL-V). If
`shift` is true the text after the cursor should be shifted, otherwise
it should overwrite the char at the cursor.

Should be hidden at next cmdline_show.

["cmdline_hide"] ~
Hide the cmdline.

["cmdline_block_show", lines] ~
Show a block of context to the current command line. For example if
the user defines a [:function](#:function) interactively:
```
:function Foo()
:  echo "foo"
:

```

`lines` is a list of lines of highlighted chunks, in the same form as
the "cmdline_show" `contents` parameter.

["cmdline_block_append", line] ~
Append a line at the end of the currently shown block.

["cmdline_block_hide"] ~
Hide the block.


## <a id="ui-messages" class="section-title" href="#ui-messages">Message/Dialog Events</a> 

Activated by the `ext_messages` [ui-option](#ui-option).
Activates [ui-linegrid| and |ui-cmdline](#ui-linegrid| and |ui-cmdline) implicitly.

This UI extension delegates presentation of messages and dialogs. Messages
that would otherwise render in the message/cmdline screen space, are emitted
as UI events.

Nvim will not allocate screen space for the cmdline or messages, and
'cmdheight' will be forced zero. Cmdline state is emitted as [ui-cmdline](#ui-cmdline)
events, which the UI must handle.

["msg_show", kind, content, replace_last] ~
Display a message to the user.

kind
Name indicating the message kind:
"" (empty)	Unknown (consider a feature-request: [bugs](#bugs))
"confirm"	[confirm()| or |:confirm](#confirm()| or |:confirm) dialog
"confirm_sub"	[:substitute| confirm dialog |:s_c](#:substitute| confirm dialog |:s_c)
"emsg"		Error ([errors|, internal error, |:throw](#errors|, internal error, |:throw), …)
"echo"		[:echo](#:echo) message
"echomsg"	[:echomsg](#:echomsg) message
"echoerr"	[:echoerr](#:echoerr) message
"lua_error"	Error in [:lua](#:lua) code
"rpc_error"	Error response from [rpcrequest()](#rpcrequest())
"return_prompt"	[press-enter](#press-enter) prompt after a multiple messages
"quickfix"	Quickfix navigation message
"search_count"	Search count message ("S" flag of 'shortmess')
"wmsg"		Warning ("search hit BOTTOM", [W10](#W10), …)
New kinds may be added in the future; clients should treat unknown
kinds as the empty kind.

content
Array of `[attr_id, text_chunk]` tuples, building up the message
text of chunks of different highlights. No extra spacing should be
added between chunks, the `text_chunk` by itself contains any
necessary whitespace. Messages can contain line breaks "\n".

replace_last
Decides how multiple messages should be displayed:
false: Display the message together with all previous messages
that are still visible.
true:  Replace the message in the most-recent `msg_show` call,
but any other visible message should still remain.

["msg_clear"] ~
Clear all messages currently displayed by "msg_show". (Messages sent
by other "msg_" events below will not be affected).

["msg_showmode", content] ~
Shows 'showmode' and [recording](#recording) messages. `content` has the same
format as in "msg_show". This event is sent with empty `content` to
hide the last message.

["msg_showcmd", content] ~
Shows 'showcmd' messages. `content` has the same format as in "msg_show".
This event is sent with empty `content` to hide the last message.

["msg_ruler", content] ~
Used to display 'ruler' when there is no space for the ruler in a
statusline. `content` has the same format as in "msg_show". This event is
sent with empty `content` to hide the last message.

["msg_history_show", entries] ~
Sent when [:messages](#:messages) command is invoked. History is sent as a list of
entries, where each entry is a `[kind, content]` tuple.


## <a id="" class="section-title" href="#">Vim Tw 78 Ts 8 Noet Ft Help Norl</a> 




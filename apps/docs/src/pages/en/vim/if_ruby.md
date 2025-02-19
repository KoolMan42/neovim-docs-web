---
title: Tree Sitter
description: Some page
layout: "@layouts/MainLayout.astro"
---


## <a id="Nvim" class="section-title" href="#Nvim"> if Ruby Txt</a> 

VIM REFERENCE MANUAL    by Shugo Maeda

### <a id="if_ruby ruby Ruby" class="section-title" href="#if_ruby ruby Ruby">The Ruby Interface to Vim</a>

### <a id="E266 E267 E268 E269 E270 E271 E272 E273" class="section-title" href="#E266 E267 E268 E269 E270 E271 E272 E273">Note:</a>

The home page for ruby is https://www.ruby-lang.org/.  You can find links for
downloading Ruby there.

Type [gO](#gO) to see the table of contents.


## <a id="ruby-commands" class="section-title" href="#ruby-commands">1. Commands</a> 

### <a id=":ruby :rub" class="section-title" href="#:ruby :rub">Note:</a>
:rub[y] {cmd}		Execute Ruby command {cmd}.  A command to try it out:
```
:ruby print "Hello"

:rub[y] << [endmarker]
{script}
{endmarker}
Execute Ruby script {script}.
The {endmarker} after {script} must NOT be preceded by
any white space.

If [endmarker] is omitted, it defaults to a dot '.'
like for the [:append| and |:insert](#:append| and |:insert) commands.

This form of the [:ruby](#:ruby) command is mainly useful for
including ruby code in vim scripts.

Example Vim script:
```

function! RedGem()
ruby << EOF
class Garnet
def initialize(s)
@buffer = VIM::Buffer.current
vimputs(s)
end
def vimputs(s)
@buffer.append(@buffer.count,s)
end
end
gem = Garnet.new("pretty")
EOF
endfunction

```

To see what version of Ruby you have:
```
:ruby print RUBY_VERSION

```


### <a id=":rubydo :rubyd E265" class="section-title" href="#:rubydo :rubyd E265">Note:</a>
:[range]rubyd[o] {cmd}	Evaluate Ruby command {cmd} for each line in the
[range], with $_ being set to the text of each line in
turn, without a trailing <EOL>.  Setting $_ will change
the text, but note that it is not possible to add or
delete lines using this command.
The default for [range] is the whole file: "1,$".

### <a id=":rubyfile :rubyf" class="section-title" href="#:rubyfile :rubyf">Note:</a>
:rubyf[ile] {file}	Execute the Ruby script in {file}.  This is the same as
`:ruby load 'file'`, but allows file name completion.

Executing Ruby commands is not possible in the [sandbox](#sandbox).


## <a id="ruby-vim" class="section-title" href="#ruby-vim">2. the VIM Module</a> 

Ruby code gets all of its access to vim via the "VIM" module.

Overview
```
print "Hello"			      # displays a message
VIM.command(cmd)		      # execute an Ex command
num = VIM::Window.count		      # gets the number of windows
w = VIM::Window[n]		      # gets window "n"
cw = VIM::Window.current	      # gets the current window
num = VIM::Buffer.count		      # gets the number of buffers
b = VIM::Buffer[n]		      # gets buffer "n"
cb = VIM::Buffer.current	      # gets the current buffer
w.height = lines		      # sets the window height
w.cursor = [row, col]		      # sets the window cursor position
pos = w.cursor			      # gets an array [row, col]
name = b.name			      # gets the buffer file name
line = b[n]			      # gets a line from the buffer
num = b.count			      # gets the number of lines
b[n] = str			      # sets a line in the buffer
b.delete(n)			      # deletes a line
b.append(n, str)		      # appends a line after n
line = VIM::Buffer.current.line       # gets the current line
num = VIM::Buffer.current.line_number # gets the current line number
VIM::Buffer.current.line = "test"     # sets the current line number

```


Module Functions:

### <a id="ruby-message" class="section-title" href="#ruby-message">Note:</a>
VIM::message({msg})
Displays the message {msg}.

### <a id="ruby-set_option" class="section-title" href="#ruby-set_option">Note:</a>
VIM::set_option({arg})
Sets a vim option.  {arg} can be any argument that the ":set" command
accepts.  Note that this means that no spaces are allowed in the
argument!  See [:set](#:set).

### <a id="ruby-command" class="section-title" href="#ruby-command">Note:</a>
VIM::command({cmd})
Executes Ex command {cmd}.

### <a id="ruby-evaluate" class="section-title" href="#ruby-evaluate">Note:</a>
VIM::evaluate({expr})
Evaluates {expr} using the vim internal expression evaluator (see
[expression](#expression)).  Returns the expression result as a string.
A [List](#List) is turned into a string by joining the items and inserting
line breaks.


## <a id="ruby-buffer" class="section-title" href="#ruby-buffer">3. VIM::Buffer Objects</a> 

VIM::Buffer objects represent vim buffers.

Class Methods:

current		Returns the current buffer object.
count		Returns the number of buffers.
self[{n}]	Returns the buffer object for the number {n}.  The first number
is 0.

Methods:

name		Returns the full name of the buffer.
number		Returns the number of the buffer.
count		Returns the number of lines.
length		Returns the number of lines.
self[{n}]	Returns a line from the buffer. {n} is the line number.
self[{n}] = {str}
Sets a line in the buffer. {n} is the line number.
delete({n})	Deletes a line from the buffer. {n} is the line number.
append({n}, {str})
Appends a line after the line {n}.
line		Returns the current line of the buffer if the buffer is
active.
line = {str}    Sets the current line of the buffer if the buffer is active.
line_number     Returns the number of the current line if the buffer is
active.


## <a id="ruby-window" class="section-title" href="#ruby-window">4. VIM::Window Objects</a> 

VIM::Window objects represent vim windows.

Class Methods:

current		Returns the current window object.
count		Returns the number of windows.
self[{n}]	Returns the window object for the number {n}.  The first number
is 0.

Methods:

buffer		Returns the buffer displayed in the window.
height		Returns the height of the window.
height = {n}	Sets the window height to {n}.
width		Returns the width of the window.
width = {n}	Sets the window width to {n}.
cursor		Returns a [row, col] array for the cursor position.
First line number is 1 and first column number is 0.
cursor = [{row}, {col}]
Sets the cursor position to {row} and {col}.


## <a id="ruby-globals" class="section-title" href="#ruby-globals">5. Global Variables</a> 

There are two global variables.

$curwin		The current window object.
$curbuf		The current buffer object.


## <a id="ruby-rubyeval" class="section-title" href="#ruby-rubyeval">6. Rubyeval() Vim Function</a> 

To facilitate bi-directional interface, you can use [rubyeval()](#rubyeval()) function to
evaluate Ruby expressions and pass their values to Vim script.

The Ruby value "true", "false" and "nil" are converted to v:true, v:false and
v:null, respectively.


## <a id="" class="section-title" href="#">Vim Tw 78 Ts 8 Noet Ft Help Norl</a> 




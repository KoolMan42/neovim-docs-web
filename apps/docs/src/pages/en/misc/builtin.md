---
title: Tree Sitter
description: Some page
layout: "@layouts/MainLayout.astro"
---


## <a id="" class="section-title" href="#">*Builtin.Txt*	Nvim</a> 

VIM REFERENCE MANUAL	  by Bram Moolenaar


### <a id="builtin-functions" class="section-title" href="#builtin-functions">Builtin functions</a>

For functions grouped by what they are used for see [function-list](#function-list).

Type [gO](#gO) to see the table of contents.


## <a id="builtin-function-list" class="section-title" href="#builtin-function-list">1. Overview</a> 

Use CTRL-] on the function name to jump to the full explanation.

USAGE				RESULT	DESCRIPTION	~

abs({expr})			Float or Number  absolute value of {expr}
acos({expr})			Float	arc cosine of {expr}
add({object}, {item})		List/Blob   append {item} to {object}
and({expr}, {expr})		Number	bitwise AND
api_info()			Dict	api metadata
append({lnum}, {text})		Number	append {text} below line {lnum}
appendbufline({expr}, {lnum}, {text})
Number	append {text} below line {lnum}
in buffer {expr}
argc([{winid}])			Number	number of files in the argument list
argidx()			Number	current index in the argument list
arglistid([{winnr} [, {tabnr}]]) Number	argument list id
argv({nr} [, {winid}])		String	{nr} entry of the argument list
argv([-1, {winid}])		List	the argument list
asin({expr})			Float	arc sine of {expr}
assert_beeps({cmd})		Number	assert {cmd} causes a beep
assert_equal({exp}, {act} [, {msg}])
Number	assert {exp} is equal to {act}
assert_equalfile({fname-one}, {fname-two} [, {msg}])
Number	assert file contents are equal
assert_exception({error} [, {msg}])
Number	assert {error} is in v:exception
assert_fails({cmd} [, {error}])	Number	assert {cmd} fails
assert_false({actual} [, {msg}])
Number	assert {actual} is false
assert_inrange({lower}, {upper}, {actual} [, {msg}])
Number	assert {actual} is inside the range
assert_match({pat}, {text} [, {msg}])
Number	assert {pat} matches {text}
assert_nobeep({cmd})		Number	assert {cmd} does not cause a beep
assert_notequal({exp}, {act} [, {msg}])
Number	assert {exp} is not equal {act}
assert_notmatch({pat}, {text} [, {msg}])
Number	assert {pat} not matches {text}
assert_report({msg})		Number	report a test failure
assert_true({actual} [, {msg}])	Number	assert {actual} is true
atan({expr})			Float	arc tangent of {expr}
atan2({expr1}, {expr2})		Float	arc tangent of {expr1} / {expr2}
browse({save}, {title}, {initdir}, {default})
String	put up a file requester
browsedir({title}, {initdir})	String	put up a directory requester
bufadd({name})			Number	add a buffer to the buffer list
bufexists({expr})		Number	[TRUE](#TRUE) if buffer {expr} exists
buflisted({expr})		Number	[TRUE](#TRUE) if buffer {expr} is listed
bufload({expr})			Number	load buffer {expr} if not loaded yet
bufloaded({expr})		Number	[TRUE](#TRUE) if buffer {expr} is loaded
bufname([{expr}])		String	Name of the buffer {expr}
bufnr([{expr} [, {create}]])	Number	Number of the buffer {expr}
bufwinid({expr})		Number	[window-ID](#window-ID) of buffer {expr}
bufwinnr({expr})		Number	window number of buffer {expr}
byte2line({byte})		Number	line number at byte count {byte}
byteidx({expr}, {nr})		Number	byte index of {nr}'th char in {expr}
byteidxcomp({expr}, {nr})	Number	byte index of {nr}'th char in {expr}
call({func}, {arglist} [, {dict}])
any	call {func} with arguments {arglist}
ceil({expr})			Float	round {expr} up
changenr()			Number	current change number
chanclose({id} [, {stream}])	Number	Closes a channel or one of its streams
chansend({id}, {data})		Number	Writes {data} to channel
char2nr({expr} [, {utf8}])	Number	ASCII/UTF-8 value of first char in {expr}
charclass({string})		Number	character class of {string}
charcol({expr})			Number	column number of cursor or mark
charidx({string}, {idx} [, {countcc}])
Number	char index of byte {idx} in {string}
chdir({dir})			String	change current working directory
cindent({lnum})			Number	C indent for line {lnum}
clearmatches([{win}])		none	clear all matches
col({expr})			Number	column byte index of cursor or mark
complete({startcol}, {matches}) none	set Insert mode completion
complete_add({expr})		Number	add completion match
complete_check()		Number	check for key typed during completion
complete_info([{what}])		Dict	get current completion information
confirm({msg} [, {choices} [, {default} [, {type}]]])
Number	number of choice picked by user
copy({expr})			any	make a shallow copy of {expr}
cos({expr})			Float	cosine of {expr}
cosh({expr})			Float	hyperbolic cosine of {expr}
count({comp}, {expr} [, {ic} [, {start}]])
Number	count how many {expr} are in {comp}
ctxget([{index}])		Dict	return the [context](#context) dict at {index}
ctxpop()			none	pop and restore [context](#context) from the
[context-stack](#context-stack)
ctxpush([{types}])		none	push the current [context](#context) to the
[context-stack](#context-stack)
ctxset({context} [, {index}])	none	set [context](#context) at {index}
ctxsize()			Number	return [context-stack](#context-stack) size
cursor({lnum}, {col} [, {off}])
Number	move cursor to {lnum}, {col}, {off}
cursor({list})			Number	move cursor to position in {list}
debugbreak({pid})		Number	interrupt process being debugged
deepcopy({expr} [, {noref}])	any	make a full copy of {expr}
delete({fname} [, {flags}])	Number	delete the file or directory {fname}
deletebufline({buf}, {first} [, {last}])
Number	delete lines from buffer {buf}
dictwatcheradd({dict}, {pattern}, {callback})
Start watching a dictionary
dictwatcherdel({dict}, {pattern}, {callback})
Stop watching a dictionary
did_filetype()			Number	[TRUE](#TRUE) if FileType autocommand event used
diff_filler({lnum})		Number	diff filler lines about {lnum}
diff_hlID({lnum}, {col})	Number	diff highlighting at {lnum}/{col}
digraph_get({chars})		String	get the [digraph](#digraph) of {chars}
digraph_getlist([{listall}])	List	get all [digraph](#digraph)s
digraph_set({chars}, {digraph})	Boolean	register [digraph](#digraph)
digraph_setlist({digraphlist})	Boolean	register multiple [digraph](#digraph)s
empty({expr})			Number	[TRUE](#TRUE) if {expr} is empty
environ()			Dict	return environment variables
escape({string}, {chars})	String	escape {chars} in {string} with '\'
eval({string})			any	evaluate {string} into its value
eventhandler()			Number	[TRUE](#TRUE) if inside an event handler
executable({expr})		Number	1 if executable {expr} exists
execute({command})		String	execute and capture output of {command}
exepath({expr})			String	full path of the command {expr}
exists({expr})			Number	[TRUE](#TRUE) if {expr} exists
exp({expr})			Float	exponential of {expr}
expand({expr} [, {nosuf} [, {list}]])
any	expand special keywords in {expr}
expandcmd({expr})		String	expand {expr} like with `:edit`
extend({expr1}, {expr2} [, {expr3}])
List/Dict insert items of {expr2} into {expr1}
feedkeys({string} [, {mode}])	Number	add key sequence to typeahead buffer
filereadable({file})		Number	[TRUE](#TRUE) if {file} is a readable file
filewritable({file})		Number	[TRUE](#TRUE) if {file} is a writable file
filter({expr1}, {expr2})	List/Dict  remove items from {expr1} where
{expr2} is 0
finddir({name} [, {path} [, {count}]])
String	find directory {name} in {path}
findfile({name} [, {path} [, {count}]])
String	find file {name} in {path}
flatten({list} [, {maxdepth}])	List	flatten {list} up to {maxdepth} levels
float2nr({expr})		Number	convert Float {expr} to a Number
floor({expr})			Float	round {expr} down
fmod({expr1}, {expr2})		Float	remainder of {expr1} / {expr2}
fnameescape({fname})		String	escape special characters in {fname}
fnamemodify({fname}, {mods})	String	modify file name
foldclosed({lnum})		Number	first line of fold at {lnum} if closed
foldclosedend({lnum})		Number	last line of fold at {lnum} if closed
foldlevel({lnum})		Number	fold level at {lnum}
foldtext()			String	line displayed for closed fold
foldtextresult({lnum})		String	text for closed fold at {lnum}
fullcommand({name})		String	get full command from {name}
funcref({name} [, {arglist}] [, {dict}])
Funcref	reference to function {name}
function({name} [, {arglist}] [, {dict}])
Funcref	named reference to function {name}
garbagecollect([{atexit}])	none	free memory, breaking cyclic references
get({list}, {idx} [, {def}])	any	get item {idx} from {list} or {def}
get({dict}, {key} [, {def}])	any	get item {key} from {dict} or {def}
get({func}, {what})		any	get property of funcref/partial {func}
getbufinfo([{buf}])		List	information about buffers
getbufline({buf}, {lnum} [, {end}])
List	lines {lnum} to {end} of buffer {buf}
getbufvar({buf}, {varname} [, {def}])
any	variable {varname} in buffer {buf}
getchangelist([{buf}])		List	list of change list items
getchar([expr])			Number or String
get one character from the user
getcharmod()			Number	modifiers for the last typed character
getcharpos({expr})		List	position of cursor, mark, etc.
getcharsearch()			Dict	last character search
getcharstr([expr])		String	get one character from the user
getcmdcompltype()		String	return the type of the current
command-line completion
getcmdline()			String	return the current command-line
getcmdpos()			Number	return cursor position in command-line
getcmdscreenpos()		Number	return cursor screen position in
command-line
getcmdtype()			String	return current command-line type
getcmdwintype()			String	return current command-line window type
getcompletion({pat}, {type} [, {filtered}])
List	list of cmdline completion matches
getcurpos([{winnr}])		List	position of the cursor
getcursorcharpos([{winnr}])	List	character position of the cursor
getcwd([{winnr} [, {tabnr}]])	String	get the current working directory
getenv({name})			String	return environment variable
getfontname([{name}])		String	name of font being used
getfperm({fname})		String	file permissions of file {fname}
getfsize({fname})		Number	size in bytes of file {fname}
getftime({fname})		Number	last modification time of file
getftype({fname})		String	description of type of file {fname}
getjumplist([{winnr} [, {tabnr}]])
List	list of jump list items
getline({lnum})			String	line {lnum} of current buffer
getline({lnum}, {end})		List	lines {lnum} to {end} of current buffer
getloclist({nr})		List	list of location list items
getloclist({nr}, {what})	Dict	get specific location list properties
getmarklist([{buf}])		List	list of global/local marks
getmatches([{win}])		List	list of current matches
getmousepos()			Dict	last known mouse position
getpid()			Number	process ID of Vim
getpos({expr})			List	position of cursor, mark, etc.
getqflist()			List	list of quickfix items
getqflist({what})		Dict	get specific quickfix list properties
getreg([{regname} [, 1 [, {list}]]])
String or List   contents of a register
getreginfo([{regname}])		Dict	information about a register
getregtype([{regname}])		String	type of a register
gettabinfo([{expr}])		List	list of tab pages
gettabvar({nr}, {varname} [, {def}])
any	variable {varname} in tab {nr} or {def}
gettabwinvar({tabnr}, {winnr}, {name} [, {def}])
any	{name} in {winnr} in tab page {tabnr}
gettagstack([{nr}])		Dict	get the tag stack of window {nr}
getwininfo([{winid}])		List	list of info about each window
getwinpos([{timeout}])		List	X and Y coord in pixels of the Vim window
getwinposx()			Number	X coord in pixels of Vim window
getwinposy()			Number	Y coord in pixels of Vim window
getwinvar({nr}, {varname} [, {def}])
any	variable {varname} in window {nr}
glob({expr} [, {nosuf} [, {list} [, {alllinks}]]])
any	expand file wildcards in {expr}
glob2regpat({expr})		String	convert a glob pat into a search pat
globpath({path}, {expr} [, {nosuf} [, {list} [, {alllinks}]]])
String	do glob({expr}) for all dirs in {path}
has({feature})			Number	[TRUE](#TRUE) if feature {feature} supported
has_key({dict}, {key})		Number	[TRUE](#TRUE) if {dict} has entry {key}
haslocaldir([{winnr} [, {tabnr}]])
Number	[TRUE| if the window executed |:lcd](#TRUE| if the window executed |:lcd) or
the tab executed [:tcd](#:tcd)
hasmapto({what} [, {mode} [, {abbr}]])
Number	[TRUE](#TRUE) if mapping to {what} exists
histadd({history}, {item})	Number	add an item to a history
histdel({history} [, {item}])	Number	remove an item from a history
histget({history} [, {index}])	String	get the item {index} from a history
histnr({history})		Number	highest index of a history
hlID({name})			Number	syntax ID of highlight group {name}
hlexists({name})		Number	[TRUE](#TRUE) if highlight group {name} exists
hostname()			String	name of the machine Vim is running on
iconv({expr}, {from}, {to})	String	convert encoding of {expr}
indent({lnum})			Number	indent of line {lnum}
index({object}, {expr} [, {start} [, {ic}]])
Number	index in {object} where {expr} appears
input({prompt} [, {text} [, {completion}]])
String	get input from the user
inputlist({textlist})		Number	let the user pick from a choice list
inputrestore()			Number	restore typeahead
inputsave()			Number	save and clear typeahead
inputsecret({prompt} [, {text}])
String	like input() but hiding the text
insert({object}, {item} [, {idx}])
List	insert {item} in {object} [before {idx}]
interrupt()			none	interrupt script execution
invert({expr})			Number	bitwise invert
isdirectory({directory})	Number	[TRUE](#TRUE) if {directory} is a directory
isinf({expr})			Number	determine if {expr} is infinity value
(positive or negative)
islocked({expr})		Number	[TRUE](#TRUE) if {expr} is locked
isnan({expr})			Number	[TRUE](#TRUE) if {expr} is NaN
id({expr})			String	identifier of the container
items({dict})			List	key-value pairs in {dict}
jobpid({id})			Number	Returns pid of a job.
jobresize({id}, {width}, {height})
Number	Resize pseudo terminal window of a job
jobstart({cmd} [, {opts}])	Number	Spawns {cmd} as a job
jobstop({id})			Number	Stops a job
jobwait({ids} [, {timeout}])	Number	Wait for a set of jobs
join({list} [, {sep}])		String	join {list} items into one String
json_decode({expr})		any	Convert {expr} from JSON
json_encode({expr})		String	Convert {expr} to JSON
keys({dict})			List	keys in {dict}
keytrans({string})		String	translate internal keycodes to a form
that can be used by [:map](#:map)
len({expr})			Number	the length of {expr}
libcall({lib}, {func}, {arg})	String	call {func} in library {lib} with {arg}
libcallnr({lib}, {func}, {arg})	Number	idem, but return a Number
line({expr} [, {winid}])	Number	line nr of cursor, last line or mark
line2byte({lnum})		Number	byte count of line {lnum}
lispindent({lnum})		Number	Lisp indent for line {lnum}
list2str({list} [, {utf8}])	String	turn numbers in {list} into a String
localtime()			Number	current time
log({expr})			Float	natural logarithm (base e) of {expr}
log10({expr})			Float	logarithm of Float {expr} to base 10
luaeval({expr} [, {expr}])	any	evaluate [Lua](#Lua) expression
map({expr1}, {expr2})		List/Dict  change each item in {expr1} to {expr}
maparg({name} [, {mode} [, {abbr} [, {dict}]]])
String or Dict
rhs of mapping {name} in mode {mode}
mapcheck({name} [, {mode} [, {abbr}]])
String	check for mappings matching {name}
mapset({mode}, {abbr}, {dict})
none	restore mapping from [maparg()](#maparg()) result
match({expr}, {pat} [, {start} [, {count}]])
Number	position where {pat} matches in {expr}
matchadd({group}, {pattern} [, {priority} [, {id} [, {dict}]]])
Number	highlight {pattern} with {group}
matchaddpos({group}, {pos} [, {priority} [, {id} [, {dict}]]])
Number	highlight positions with {group}
matcharg({nr})			List	arguments of [:match](#:match)
matchdelete({id} [, {win}])	Number	delete match identified by {id}
matchend({expr}, {pat} [, {start} [, {count}]])
Number	position where {pat} ends in {expr}
matchfuzzy({list}, {str} [, {dict}])
List	fuzzy match {str} in {list}
matchfuzzypos({list}, {str} [, {dict}])
List	fuzzy match {str} in {list}
matchlist({expr}, {pat} [, {start} [, {count}]])
List	match and submatches of {pat} in {expr}
matchstr({expr}, {pat} [, {start} [, {count}]])
String	{count}'th match of {pat} in {expr}
matchstrpos({expr}, {pat} [, {start} [, {count}]])
List	{count}'th match of {pat} in {expr}
max({expr})			Number	maximum value of items in {expr}
menu_get({path} [, {modes}])	List	description of [menus](#menus) matched by {path}
menu_info({name} [, {mode}])	Dict	get menu item information
min({expr})			Number	minimum value of items in {expr}
mkdir({name} [, {path} [, {prot}]])
Number	create directory {name}
mode([expr])			String	current editing mode
msgpackdump({list} [, {type}])	List/Blob  dump objects to msgpack
msgpackparse({data})		List	parse msgpack to a list of objects
nextnonblank({lnum})		Number	line nr of non-blank line >= {lnum}
nr2char({expr} [, {utf8}])	String	single char with ASCII/UTF-8 value {expr}
nvim_...({args}...)		any	call nvim [api](#api) functions
or({expr}, {expr})		Number	bitwise OR
pathshorten({expr} [, {len}])	String	shorten directory names in a path
perleval({expr})		any	evaluate [perl](#perl) expression
pow({x}, {y})			Float	{x} to the power of {y}
prevnonblank({lnum})		Number	line nr of non-blank line <= {lnum}
printf({fmt}, {expr1}...)	String	format text
prompt_getprompt({buf})		String	get prompt text
prompt_setcallback({buf}, {expr}) none	set prompt callback function
prompt_setinterrupt({buf}, {text}) none	set prompt interrupt function
prompt_setprompt({buf}, {text}) none	set prompt text
pum_getpos()			Dict	position and size of pum if visible
pumvisible()			Number	whether popup menu is visible
py3eval({expr})			any	evaluate [python3](#python3) expression
pyeval({expr})			any	evaluate [Python](#Python) expression
pyxeval({expr})			any	evaluate [python_x](#python_x) expression
rand([{expr}])			Number	get pseudo-random number
range({expr} [, {max} [, {stride}]])
List	items from {expr} to {max}
readdir({dir} [, {expr}])	List	file names in {dir} selected by {expr}
readfile({fname} [, {type} [, {max}]])
List	get list of lines from file {fname}
reduce({object}, {func} [, {initial}])
any	reduce {object} using {func}
reg_executing()			String	get the executing register name
reg_recorded()			String	get the last recorded register name
reg_recording()			String	get the recording register name
reltime([{start} [, {end}]])	List	get time value
reltimefloat({time})		Float	turn the time value into a Float
reltimestr({time})		String	turn time value into a String
remove({list}, {idx} [, {end}])	any/List
remove items {idx}-{end} from {list}
remove({blob}, {idx} [, {end}])	Number/Blob
remove bytes {idx}-{end} from {blob}
remove({dict}, {key})		any	remove entry {key} from {dict}
rename({from}, {to})		Number	rename (move) file from {from} to {to}
repeat({expr}, {count})		String	repeat {expr} {count} times
resolve({filename})		String	get filename a shortcut points to
reverse({list})			List	reverse {list} in-place
round({expr})			Float	round off {expr}
rubyeval({expr})		any	evaluate [Ruby](#Ruby) expression
rpcnotify({channel}, {event} [, {args}...])
Sends an [RPC](#RPC) notification to {channel}
rpcrequest({channel}, {method} [, {args}...])
Sends an [RPC](#RPC) request to {channel}
screenattr({row}, {col})	Number	attribute at screen position
screenchar({row}, {col})	Number	character at screen position
screenchars({row}, {col})	List	List of characters at screen position
screencol()			Number	current cursor column
screenpos({winid}, {lnum}, {col}) Dict	screen row and col of a text character
screenrow()			Number	current cursor row
screenstring({row}, {col})	String	characters at screen position
search({pattern} [, {flags} [, {stopline} [, {timeout} [, {skip}]]]])
Number	search for {pattern}
searchcount([{options}])	Dict	Get or update the last search count
searchdecl({name} [, {global} [, {thisblock}]])
Number	search for variable declaration
searchpair({start}, {middle}, {end} [, {flags} [, {skip} [...]]])
Number	search for other end of start/end pair
searchpairpos({start}, {middle}, {end} [, {flags} [, {skip} [...]]])
List	search for other end of start/end pair
searchpos({pattern} [, {flags} [, {stopline} [, {timeout} [, {skip}]]]])
List	search for {pattern}
serverlist()			String	get a list of available servers
setbufline({expr}, {lnum}, {text})
Number	set line {lnum} to {text} in buffer
{expr}
setbufvar({buf}, {varname}, {val})	set {varname} in buffer {buf} to {val}
setcellwidths({list})		none	set character cell width overrides
setcharpos({expr}, {list})	Number	set the {expr} position to {list}
setcharsearch({dict})		Dict	set character search from {dict}
setcmdline({str} [, {pos}])	Number	set command-line
setcmdpos({pos})		Number	set cursor position in command-line
setcursorcharpos({list})	Number	move cursor to position in {list}
setenv({name}, {val})		none	set environment variable
setfperm({fname}, {mode}	Number	set {fname} file permissions to {mode}
setline({lnum}, {line})		Number	set line {lnum} to {line}
setloclist({nr}, {list} [, {action}])
Number	modify location list using {list}
setloclist({nr}, {list}, {action}, {what})
Number	modify specific location list props
setmatches({list} [, {win}])	Number	restore a list of matches
setpos({expr}, {list})		Number	set the {expr} position to {list}
setqflist({list} [, {action}])	Number	modify quickfix list using {list}
setqflist({list}, {action}, {what})
Number	modify specific quickfix list props
setreg({n}, {v} [, {opt}])	Number	set register to value and type
settabvar({nr}, {varname}, {val})	set {varname} in tab page {nr} to {val}
settabwinvar({tabnr}, {winnr}, {varname}, {val})    set {varname} in window
{winnr} in tab page {tabnr} to {val}
settagstack({nr}, {dict} [, {action}])
Number	modify tag stack using {dict}
setwinvar({nr}, {varname}, {val})	set {varname} in window {nr} to {val}
sha256({string})		String	SHA256 checksum of {string}
shellescape({string} [, {special}])
String	escape {string} for use as shell
command argument
shiftwidth([{col}])		Number	effective value of 'shiftwidth'
sign_define({name} [, {dict}])	Number	define or update a sign
sign_define({list})		List	define or update a list of signs
sign_getdefined([{name}])	List	get a list of defined signs
sign_getplaced([{buf} [, {dict}]])
List	get a list of placed signs
sign_jump({id}, {group}, {buf})
Number	jump to a sign
sign_place({id}, {group}, {name}, {buf} [, {dict}])
Number	place a sign
sign_placelist({list})		List	place a list of signs
sign_undefine([{name}])		Number	undefine a sign
sign_undefine({list})		List	undefine a list of signs
sign_unplace({group} [, {dict}])
Number	unplace a sign
sign_unplacelist({list})	List	unplace a list of signs
simplify({filename})		String	simplify filename as much as possible
sin({expr})			Float	sine of {expr}
sinh({expr})			Float	hyperbolic sine of {expr}
sockconnect({mode}, {address} [, {opts}])
Number	Connects to socket
sort({list} [, {func} [, {dict}]])
List	sort {list}, using {func} to compare
soundfold({word})		String	sound-fold {word}
spellbadword()			String	badly spelled word at cursor
spellsuggest({word} [, {max} [, {capital}]])
List	spelling suggestions
split({expr} [, {pat} [, {keepempty}]])
List	make [List](#List) from {pat} separated {expr}
sqrt({expr})			Float	square root of {expr}
srand([{expr}])			List	get seed for [rand()](#rand())
stdioopen({dict})		Number	open stdio in a headless instance.
stdpath({what})			String/List  returns the standard path(s) for {what}
str2float({expr} [, {quoted}])	Float	convert String to Float
str2list({expr} [, {utf8}])	List	convert each character of {expr} to
ASCII/UTF-8 value
str2nr({expr} [, {base} [, {quoted}]])
Number	convert String to Number
strcharpart({str}, {start} [, {len}])
String	{len} characters of {str} at
character {start}
strchars({expr} [, {skipcc}])	Number	character length of the String {expr}
strdisplaywidth({expr} [, {col}]) Number display length of the String {expr}
strftime({format} [, {time}])	String	format time with a specified format
strgetchar({str}, {index})	Number	get char {index} from {str}
stridx({haystack}, {needle} [, {start}])
Number	index of {needle} in {haystack}
string({expr})			String	String representation of {expr} value
strlen({expr})			Number	length of the String {expr}
strpart({str}, {start} [, {len} [, {chars}]])
String	{len} bytes/chars of {str} at
byte {start}
strptime({format}, {timestring})
Number	Convert {timestring} to unix timestamp
strridx({haystack}, {needle} [, {start}])
Number	last index of {needle} in {haystack}
strtrans({expr})		String	translate string to make it printable
strwidth({expr})		Number	display cell length of the String {expr}
submatch({nr} [, {list}])	String or List
specific match in ":s" or substitute()
substitute({expr}, {pat}, {sub}, {flags})
String	all {pat} in {expr} replaced with {sub}
swapinfo({fname})		Dict	information about swap file {fname}
swapname({buf})			String	swap file of buffer {buf}
synID({lnum}, {col}, {trans})	Number	syntax ID at {lnum} and {col}
synIDattr({synID}, {what} [, {mode}])
String	attribute {what} of syntax ID {synID}
synIDtrans({synID})		Number	translated syntax ID of {synID}
synconcealed({lnum}, {col})	List	info about concealing
synstack({lnum}, {col})	List	stack of syntax IDs at {lnum} and {col}
system({cmd} [, {input}])	String	output of shell command/filter {cmd}
systemlist({cmd} [, {input}])	List	output of shell command/filter {cmd}
tabpagebuflist([{arg}])		List	list of buffer numbers in tab page
tabpagenr([{arg}])		Number	number of current or last tab page
tabpagewinnr({tabarg} [, {arg}])
Number	number of current window in tab page
tagfiles()			List	tags files used
taglist({expr} [, {filename}])	List	list of tags matching {expr}
tan({expr})			Float	tangent of {expr}
tanh({expr})			Float	hyperbolic tangent of {expr}
tempname()			String	name for a temporary file
test_garbagecollect_now()	none	free memory right now for testing
timer_info([{id}])		List	information about timers
timer_pause({id}, {pause})	none	pause or unpause a timer
timer_start({time}, {callback} [, {options}])
Number	create a timer
timer_stop({timer})		none	stop a timer
timer_stopall()			none	stop all timers
tolower({expr})			String	the String {expr} switched to lowercase
toupper({expr})			String	the String {expr} switched to uppercase
tr({src}, {fromstr}, {tostr})	String	translate chars of {src} in {fromstr}
to chars in {tostr}
trim({text} [, {mask} [, {dir}]])
String	trim characters in {mask} from {text}
trunc({expr})			Float	truncate Float {expr}
type({name})			Number	type of variable {name}
undofile({name})		String	undo file name for {name}
undotree()			List	undo file tree
uniq({list} [, {func} [, {dict}]])
List	remove adjacent duplicates from a list
values({dict})			List	values in {dict}
virtcol({expr})			Number	screen column of cursor or mark
virtcol2col({winid}, {lnum}, {col})
Number  byte index of a character on screen
visualmode([expr])		String	last visual mode used
wait({timeout}, {condition} [, {interval}])
Number	Wait until {condition} is satisfied
wildmenumode()			Number	whether 'wildmenu' mode is active
win_execute({id}, {command} [, {silent}])
String	execute {command} in window {id}
win_findbuf({bufnr})		List	find windows containing {bufnr}
win_getid([{win} [, {tab}]])	Number	get [window-ID](#window-ID) for {win} in {tab}
win_gettype([{nr}])		String	type of window {nr}
win_gotoid({expr})		Number	go to [window-ID](#window-ID) {expr}
win_id2tabwin({expr})		List	get tab and window nr from [window-ID](#window-ID)
win_id2win({expr})		Number	get window nr from [window-ID](#window-ID)
win_move_separator({nr})	Number	move window vertical separator
win_move_statusline({nr})	Number	move window status line
win_screenpos({nr})		List	get screen position of window {nr}
win_splitmove({nr}, {target} [, {options}])
Number	move window {nr} to split of {target}
winbufnr({nr})			Number	buffer number of window {nr}
wincol()			Number	window column of the cursor
windowsversion()		String	MS-Windows OS version
winheight({nr})			Number	height of window {nr}
winlayout([{tabnr}])		List	layout of windows in tab {tabnr}
winline()			Number	window line of the cursor
winnr([{expr}])			Number	number of current window
winrestcmd()			String	returns command to restore window sizes
winrestview({dict})		none	restore view of current window
winsaveview()			Dict	save view of current window
winwidth({nr})			Number	width of window {nr}
wordcount()			Dict	get byte/char/word statistics
writefile({object}, {fname} [, {flags}])
Number	write [Blob| or |List](#Blob| or |List) of lines to file
xor({expr}, {expr})		Number	bitwise XOR


## <a id="builtin-function-details" class="section-title" href="#builtin-function-details">2. Details</a> 

Not all functions are here, some have been moved to a help file covering the
specific functionality.

### <a id="abs()" class="section-title" href="#abs()">abs({expr})</a>
Return the absolute value of {expr}.  When {expr} evaluates to
a [Float| abs() returns a |Float](#Float| abs() returns a |Float).  When {expr} can be
converted to a [Number| abs() returns a |Number](#Number| abs() returns a |Number).  Otherwise
abs() gives an error message and returns -1.
Examples:
```
echo abs(1.456)

```
			1.456
```
echo abs(-5.456)

```
			5.456
```
echo abs(-4)

```
			4

Can also be used as a [method](#method):
```
Compute()->abs()

### <a id="acos()" class="section-title" href="#acos()">acos({expr})</a>
Return the arc cosine of {expr} measured in radians, as a
[Float](#Float) in the range of [0, pi].
{expr} must evaluate to a [Float| or a |Number](#Float| or a |Number) in the range
[-1, 1].
Returns NaN if {expr} is outside the range [-1, 1].  Returns
0.0 if {expr} is not a [Float| or a |Number](#Float| or a |Number).
Examples:
```
:echo acos(0)

```
			1.570796
```
:echo acos(-0.5)

```
			2.094395

Can also be used as a [method](#method):
```
Compute()->acos()

### <a id="add()" class="section-title" href="#add()">add({object}, {expr})</a>
Append the item {expr} to [List| or |Blob](#List| or |Blob) {object}.  Returns
the resulting [List| or |Blob](#List| or |Blob).  Examples:
```
:let alist = add([1, 2, 3], item)
:call add(mylist, "woodstock")

```
		Note that when {expr} is a [List](#List) it is appended as a single
item.  Use [extend()| to concatenate |Lists](#extend()| to concatenate |Lists).
When {object} is a [Blob](#Blob) then {expr} must be a number.
Use [insert()](#insert()) to add an item at another position.
Returns 1 if {object} is not a [List| or a |Blob](#List| or a |Blob).

Can also be used as a [method](#method):
```
mylist->add(val1)->add(val2)

### <a id="and()" class="section-title" href="#and()">and({expr}, {expr})</a>
Bitwise AND on the two arguments.  The arguments are converted
to a number.  A List, Dict or Float argument causes an error.
Example:
```
:let flag = and(bits, 0x80)

```
		Can also be used as a [method](#method):
```
:let flag = bits->and(0x80)

### <a id="api_info()" class="section-title" href="#api_info()">api_info()</a>
Returns Dictionary of [api-metadata](#api-metadata).

View it in a nice human-readable format:
```
:lua print(vim.inspect(vim.fn.api_info()))

### <a id="append()" class="section-title" href="#append()">append({lnum}, {text})</a>
When {text} is a [List|: Append each item of the |List](#List|: Append each item of the |List) as a
text line below line {lnum} in the current buffer.
Otherwise append {text} as one text line below line {lnum} in
the current buffer.
{lnum} can be zero to insert a line before the first one.
{lnum} is used like with [getline()](#getline()).
Returns 1 for failure ({lnum} out of range or out of memory),
0 for success.  Example:
```
:let failed = append(line('$'), "# THE END")
:let failed = append(0, ["Chapter 1", "the beginning"])


```
		Can also be used as a [method](#method) after a List:
```
mylist->append(lnum)

### <a id="appendbufline()" class="section-title" href="#appendbufline()">appendbufline({buf}, {lnum}, {text})</a>
Like [append()](#append()) but append the text in buffer {expr}.

This function works only for loaded buffers. First call
[bufload()](#bufload()) if needed.

For the use of {buf}, see [bufname()](#bufname()).

{lnum} is used like with [append()|.  Note that using |line()](#append()|.  Note that using |line())
would use the current buffer, not the one appending to.
Use "$" to append at the end of the buffer.

On success 0 is returned, on failure 1 is returned.

If {buf} is not a valid buffer or {lnum} is not valid, an
error message is given. Example:
```
:let failed = appendbufline(13, 0, "# THE START")

```

Can also be used as a [method](#method) after a List:
```
mylist->appendbufline(buf, lnum)

### <a id="argc()" class="section-title" href="#argc()">argc([{winid}])</a>
The result is the number of files in the argument list.  See
[arglist](#arglist).
If {winid} is not supplied, the argument list of the current
window is used.
If {winid} is -1, the global argument list is used.
Otherwise {winid} specifies the window of which the argument
list is used: either the window number or the window ID.
Returns -1 if the {winid} argument is invalid.

### <a id="argidx()" class="section-title" href="#argidx()">Note:</a>
argidx()	The result is the current index in the argument list.  0 is
the first file.  argc() - 1 is the last one.  See [arglist](#arglist).

### <a id="arglistid()" class="section-title" href="#arglistid()">Note:</a>
arglistid([{winnr} [, {tabnr}]])
Return the argument list ID.  This is a number which
identifies the argument list being used.  Zero is used for the
global argument list.  See [arglist](#arglist).
Returns -1 if the arguments are invalid.

Without arguments use the current window.
With {winnr} only use this window in the current tab page.
With {winnr} and {tabnr} use the window in the specified tab
page.
{winnr} can be the window number or the [window-ID](#window-ID).

### <a id="argv()" class="section-title" href="#argv()">Note:</a>
argv([{nr} [, {winid}]])
The result is the {nr}th file in the argument list.  See
[arglist](#arglist).  "argv(0)" is the first one.  Example:
```
:let i = 0
:while i < argc()
:  let f = escape(fnameescape(argv(i)), '.')
:  exe 'amenu Arg.' .. f .. ' :e ' .. f .. '<CR>'
:  let i = i + 1
:endwhile

```
		Without the {nr} argument, or when {nr} is -1, a [List](#List) with
the whole [arglist](#arglist) is returned.

The {winid} argument specifies the window ID, see [argc()](#argc()).
For the Vim command line arguments see [v:argv](#v:argv).

Returns an empty string if {nr}th argument is not present in
the argument list.  Returns an empty List if the {winid}
argument is invalid.

### <a id="asin()" class="section-title" href="#asin()">asin({expr})</a>
Return the arc sine of {expr} measured in radians, as a [Float](#Float)
in the range of [-pi/2, pi/2].
{expr} must evaluate to a [Float| or a |Number](#Float| or a |Number) in the range
[-1, 1].
Returns NaN if {expr} is outside the range [-1, 1].  Returns
0.0 if {expr} is not a [Float| or a |Number](#Float| or a |Number).
Examples:
```
:echo asin(0.8)

```
			0.927295
```
:echo asin(-0.5)

```
			-0.523599

Can also be used as a [method](#method):
```
Compute()->asin()


assert_ functions are documented here: [assert-functions-details](#assert-functions-details)


### <a id="atan()" class="section-title" href="#atan()">atan({expr})</a>
Return the principal value of the arc tangent of {expr}, in
the range [-pi/2, +pi/2] radians, as a [Float](#Float).
{expr} must evaluate to a [Float| or a |Number](#Float| or a |Number).
Returns 0.0 if {expr} is not a [Float| or a |Number](#Float| or a |Number).
Examples:
```
:echo atan(100)

```
			1.560797
```
:echo atan(-4.01)

```
			-1.326405

Can also be used as a [method](#method):
```
Compute()->atan()

### <a id="atan2()" class="section-title" href="#atan2()">atan2({expr1}, {expr2})</a>
Return the arc tangent of {expr1} / {expr2}, measured in
radians, as a [Float](#Float) in the range [-pi, pi].
{expr1} and {expr2} must evaluate to a [Float| or a |Number](#Float| or a |Number).
Returns 0.0 if {expr1} or {expr2} is not a [Float](#Float) or a
[Number](#Number).
Examples:
```
:echo atan2(-1, 1)

```
			-0.785398
```
:echo atan2(1, -1)

```
			2.356194

Can also be used as a [method](#method):
```
Compute()->atan2(1)

### <a id="browse()" class="section-title" href="#browse()">Note:</a>
browse({save}, {title}, {initdir}, {default})
Put up a file requester.  This only works when "has("browse")"
returns [TRUE](#TRUE) (only in some GUI versions).
The input fields are:
{save}	when [TRUE](#TRUE), select file to write
{title}	title for the requester
{initdir}	directory to start browsing in
{default}	default file name
An empty string is returned when the "Cancel" button is hit,
something went wrong, or browsing is not possible.

### <a id="browsedir()" class="section-title" href="#browsedir()">Note:</a>
browsedir({title}, {initdir})
Put up a directory requester.  This only works when
"has("browse")" returns [TRUE](#TRUE) (only in some GUI versions).
On systems where a directory browser is not supported a file
browser is used.  In that case: select a file in the directory
to be used.
The input fields are:
{title}	title for the requester
{initdir}	directory to start browsing in
When the "Cancel" button is hit, something went wrong, or
browsing is not possible, an empty string is returned.

### <a id="bufadd()" class="section-title" href="#bufadd()">bufadd({name})</a>
Add a buffer to the buffer list with name {name} (must be a
String).
If a buffer for file {name} already exists, return that buffer
number.  Otherwise return the buffer number of the newly
created buffer.  When {name} is an empty string then a new
buffer is always created.
The buffer will not have 'buflisted' set and not be loaded
yet.  To add some text to the buffer use this:
```
let bufnr = bufadd('someName')
call bufload(bufnr)
call setbufline(bufnr, 1, ['some', 'text'])

```
		Returns 0 on error.
Can also be used as a [method](#method):
```
let bufnr = 'somename'->bufadd()

### <a id="bufexists()" class="section-title" href="#bufexists()">bufexists({buf})</a>
The result is a Number, which is [TRUE](#TRUE) if a buffer called
{buf} exists.
If the {buf} argument is a number, buffer numbers are used.
Number zero is the alternate buffer for the current window.

If the {buf} argument is a string it must match a buffer name
exactly.  The name can be:
- Relative to the current directory.
- A full path.
- The name of a buffer with 'buftype' set to "nofile".
- A URL name.
Unlisted buffers will be found.
Note that help files are listed by their short name in the
output of [:buffers](#:buffers), but bufexists() requires using their
long name to be able to find them.
bufexists() may report a buffer exists, but to use the name
with a [:buffer| command you may need to use |expand()](#:buffer| command you may need to use |expand()).  Esp
for MS-Windows 8.3 names in the form "c:\DOCUME~1"
Use "bufexists(0)" to test for the existence of an alternate
file name.

Can also be used as a [method](#method):
```
let exists = 'somename'->bufexists()

### <a id="buflisted()" class="section-title" href="#buflisted()">buflisted({buf})</a>
The result is a Number, which is [TRUE](#TRUE) if a buffer called
{buf} exists and is listed (has the 'buflisted' option set).
The {buf} argument is used like with [bufexists()](#bufexists()).

Can also be used as a [method](#method):
```
let listed = 'somename'->buflisted()

### <a id="bufload()" class="section-title" href="#bufload()">bufload({buf})</a>
Ensure the buffer {buf} is loaded.  When the buffer name
refers to an existing file then the file is read.  Otherwise
the buffer will be empty.  If the buffer was already loaded
then there is no change.  If the buffer is not related to a
file the no file is read (e.g., when 'buftype' is "nofile").
If there is an existing swap file for the file of the buffer,
there will be no dialog, the buffer will be loaded anyway.
The {buf} argument is used like with [bufexists()](#bufexists()).

Can also be used as a [method](#method):
```
eval 'somename'->bufload()

### <a id="bufloaded()" class="section-title" href="#bufloaded()">bufloaded({buf})</a>
The result is a Number, which is [TRUE](#TRUE) if a buffer called
{buf} exists and is loaded (shown in a window or hidden).
The {buf} argument is used like with [bufexists()](#bufexists()).

Can also be used as a [method](#method):
```
let loaded = 'somename'->bufloaded()

### <a id="bufname()" class="section-title" href="#bufname()">bufname([{buf}])</a>
The result is the name of a buffer.  Mostly as it is displayed
by the `:ls` command, but not using special names such as
"[No Name]".
If {buf} is omitted the current buffer is used.
If {buf} is a Number, that buffer number's name is given.
Number zero is the alternate buffer for the current window.
If {buf} is a String, it is used as a [file-pattern](#file-pattern) to match
with the buffer names.  This is always done like 'magic' is
set and 'cpoptions' is empty.  When there is more than one
match an empty string is returned.
"" or "%" can be used for the current buffer, "#" for the
alternate buffer.
A full match is preferred, otherwise a match at the start, end
or middle of the buffer name is accepted.  If you only want a
full match then put "^" at the start and "$" at the end of the
pattern.
Listed buffers are found first.  If there is a single match
with a listed buffer, that one is returned.  Next unlisted
buffers are searched for.
If the {buf} is a String, but you want to use it as a buffer
number, force it to be a Number by adding zero to it:
```
:echo bufname("3" + 0)

```
		Can also be used as a [method](#method):
```
echo bufnr->bufname()


```
		If the buffer doesn't exist, or doesn't have a name, an empty
string is returned.
```
bufname("#")		alternate buffer name
bufname(3)		name of buffer 3
bufname("%")		name of current buffer
bufname("file2")	name of buffer where "file2" matches.

```

### <a id="bufnr()" class="section-title" href="#bufnr()">Note:</a>
bufnr([{buf} [, {create}]])
The result is the number of a buffer, as it is displayed by
the `:ls` command.  For the use of {buf}, see [bufname()](#bufname())
above.
If the buffer doesn't exist, -1 is returned.  Or, if the
{create} argument is present and TRUE, a new, unlisted,
buffer is created and its number is returned.
bufnr("$") is the last buffer:
```
:let last_buffer = bufnr("$")

```
		The result is a Number, which is the highest buffer number
of existing buffers.  Note that not all buffers with a smaller
number necessarily exist, because ":bwipeout" may have removed
them.  Use bufexists() to test for the existence of a buffer.

Can also be used as a [method](#method):
```
echo bufref->bufnr()

### <a id="bufwinid()" class="section-title" href="#bufwinid()">bufwinid({buf})</a>
The result is a Number, which is the [window-ID](#window-ID) of the first
window associated with buffer {buf}.  For the use of {buf},
see [bufname()](#bufname()) above.  If buffer {buf} doesn't exist or
there is no such window, -1 is returned.  Example:
```

echo "A window containing buffer 1 is " .. (bufwinid(1))

```

Only deals with the current tab page.

Can also be used as a [method](#method):
```
FindBuffer()->bufwinid()

### <a id="bufwinnr()" class="section-title" href="#bufwinnr()">bufwinnr({buf})</a>
Like [bufwinid()](#bufwinid()) but return the window number instead of the
[window-ID](#window-ID).
If buffer {buf} doesn't exist or there is no such window, -1
is returned.  Example:
```

echo "A window containing buffer 1 is " .. (bufwinnr(1))


```
		The number can be used with [CTRL-W_w](#CTRL-W_w) and ":wincmd w"
[:wincmd](#:wincmd).

Can also be used as a [method](#method):
```
FindBuffer()->bufwinnr()

### <a id="byte2line()" class="section-title" href="#byte2line()">byte2line({byte})</a>
Return the line number that contains the character at byte
count {byte} in the current buffer.  This includes the
end-of-line character, depending on the 'fileformat' option
for the current buffer.  The first character has byte count
one.
Also see [line2byte()|, |go| and |:goto](#line2byte()|, |go| and |:goto).

Returns -1 if the {byte} value is invalid.

Can also be used as a [method](#method):
```
GetOffset()->byte2line()

### <a id="byteidx()" class="section-title" href="#byteidx()">byteidx({expr}, {nr})</a>
Return byte index of the {nr}'th character in the String
{expr}.  Use zero for the first character, it then returns
zero.
If there are no multibyte characters the returned value is
equal to {nr}.
Composing characters are not counted separately, their byte
length is added to the preceding base character.  See
[byteidxcomp()](#byteidxcomp()) below for counting composing characters
separately.
Example :
```
echo matchstr(str, ".", byteidx(str, 3))

```
		will display the fourth character.  Another way to do the
same:
```
let s = strpart(str, byteidx(str, 3))
echo strpart(s, 0, byteidx(s, 1))

```
		Also see [strgetchar()| and |strcharpart()](#strgetchar()| and |strcharpart()).

If there are less than {nr} characters -1 is returned.
If there are exactly {nr} characters the length of the string
in bytes is returned.

Can also be used as a [method](#method):
```
GetName()->byteidx(idx)

### <a id="byteidxcomp()" class="section-title" href="#byteidxcomp()">byteidxcomp({expr}, {nr})</a>
Like byteidx(), except that a composing character is counted
as a separate character.  Example:
```
let s = 'e' .. nr2char(0x301)
echo byteidx(s, 1)
echo byteidxcomp(s, 1)
echo byteidxcomp(s, 2)

```
		The first and third echo result in 3 ('e' plus composing
character is 3 bytes), the second echo results in 1 ('e' is
one byte).

Can also be used as a [method](#method):
```
GetName()->byteidxcomp(idx)

### <a id="call() E699" class="section-title" href="#call() E699">call({func}, {arglist} [, {dict}])</a>
Call function {func} with the items in [List](#List) {arglist} as
arguments.
{func} can either be a [Funcref](#Funcref) or the name of a function.
a:firstline and a:lastline are set to the cursor line.
Returns the return value of the called function.
{dict} is for functions with the "dict" attribute.  It will be
used to set the local variable "self". [Dictionary-function](#Dictionary-function)

Can also be used as a [method](#method):
```
GetFunc()->call([arg, arg], dict)

### <a id="ceil()" class="section-title" href="#ceil()">ceil({expr})</a>
Return the smallest integral value greater than or equal to
{expr} as a [Float](#Float) (round up).
{expr} must evaluate to a [Float| or a |Number](#Float| or a |Number).
Examples:
```
echo ceil(1.456)

```
			2.0
```
echo ceil(-5.456)

```
			-5.0
```
echo ceil(4.0)

```
			4.0

Returns 0.0 if {expr} is not a [Float| or a |Number](#Float| or a |Number).

Can also be used as a [method](#method):
```
Compute()->ceil()

### <a id="changenr()" class="section-title" href="#changenr()">changenr()</a>
Return the number of the most recent change.  This is the same
number as what is displayed with [:undolist](#:undolist) and can be used
with the [:undo](#:undo) command.
When a change was made it is the number of that change.  After
redo it is the number of the redone change.  After undo it is
one less than the number of the undone change.
Returns 0 if the undo list is empty.

### <a id="chanclose()" class="section-title" href="#chanclose()">chanclose({id} [, {stream}])</a>
Close a channel or a specific stream associated with it.
For a job, {stream} can be one of "stdin", "stdout",
"stderr" or "rpc" (closes stdin/stdout for a job started
with `"rpc":v:true`) If {stream} is omitted, all streams
are closed. If the channel is a pty, this will then close the
pty master, sending SIGHUP to the job process.
For a socket, there is only one stream, and {stream} should be
omitted.

### <a id="chansend()" class="section-title" href="#chansend()">chansend({id}, {data})</a>
Send data to channel {id}. For a job, it writes it to the
stdin of the process. For the stdio channel [channel-stdio](#channel-stdio),
it writes to Nvim's stdout.  Returns the number of bytes
written if the write succeeded, 0 otherwise.
See [channel-bytes](#channel-bytes) for more information.

{data} may be a string, string convertible, [Blob](#Blob), or a list.
If {data} is a list, the items will be joined by newlines; any
newlines in an item will be sent as NUL. To send a final
newline, include a final empty string. Example:
```
:call chansend(id, ["abc", "123\n456", ""])

```
 		will send "abc<NL>123<NUL>456<NL>".

chansend() writes raw data, not RPC messages.  If the channel
was created with `"rpc":v:true` then the channel expects RPC
messages, use [rpcnotify()| and |rpcrequest()](#rpcnotify()| and |rpcrequest()) instead.


### <a id="char2nr()" class="section-title" href="#char2nr()">char2nr({string} [, {utf8}])</a>
Return Number value of the first char in {string}.
Examples:
```
char2nr(" ")		returns 32
char2nr("ABC")		returns 65
char2nr("á")		returns 225
char2nr("á"[0])		returns 195
char2nr("\<M-x>")	returns 128

```
		Non-ASCII characters are always treated as UTF-8 characters.
{utf8} is ignored, it exists only for backwards-compatibility.
A combining character is a separate character.
[nr2char()](#nr2char()) does the opposite.

Returns 0 if {string} is not a [String](#String).

Can also be used as a [method](#method):
```
GetChar()->char2nr()

### <a id="charclass()" class="section-title" href="#charclass()">charclass({string})</a>
Return the character class of the first character in {string}.
The character class is one of:
0	blank
1	punctuation
2	word character
3	emoji
other	specific Unicode class
The class is used in patterns and word motions.
Returns 0 if {string} is not a [String](#String).


### <a id="charcol()" class="section-title" href="#charcol()">Note:</a>
charcol({expr})	Same as [col()](#col()) but returns the character index of the column
position given with {expr} instead of the byte position.

Example:
With the cursor on '세' in line 5 with text "여보세요":
```
charcol('.')		returns 3
col('.')		returns 7


```
		Can also be used as a [method](#method):
```
GetPos()->col()

```

### <a id="charidx()" class="section-title" href="#charidx()">Note:</a>
charidx({string}, {idx} [, {countcc}])
Return the character index of the byte at {idx} in {string}.
The index of the first character is zero.
If there are no multibyte characters the returned value is
equal to {idx}.
When {countcc} is omitted or [FALSE](#FALSE), then composing characters
are not counted separately, their byte length is
added to the preceding base character.
When {countcc} is [TRUE](#TRUE), then composing characters are
counted as separate characters.
Returns -1 if the arguments are invalid or if {idx} is greater
than the index of the last byte in {string}.  An error is
given if the first argument is not a string, the second
argument is not a number or when the third argument is present
and is not zero or one.
See [byteidx()| and |byteidxcomp()](#byteidx()| and |byteidxcomp()) for getting the byte index
from the character index.
Examples:
```
echo charidx('áb́ć', 3)		returns 1
echo charidx('áb́ć', 6, 1)	returns 4
echo charidx('áb́ć', 16)		returns -1

```

Can also be used as a [method](#method):
```
GetName()->charidx(idx)

### <a id="chdir()" class="section-title" href="#chdir()">chdir({dir})</a>
Change the current working directory to {dir}.  The scope of
the directory change depends on the directory of the current
window:
- If the current window has a window-local directory
([:lcd](#:lcd)), then changes the window local directory.
- Otherwise, if the current tabpage has a local
directory ([:tcd](#:tcd)) then changes the tabpage local
directory.
- Otherwise, changes the global directory.
{dir} must be a String.
If successful, returns the previous working directory.  Pass
this to another chdir() to restore the directory.
On failure, returns an empty string.

Example:
```
let save_dir = chdir(newdir)
if save_dir != ""
" ... do some work
call chdir(save_dir)
endif


```
		Can also be used as a [method](#method):
```
GetDir()->chdir()

```

### <a id="cindent()" class="section-title" href="#cindent()">cindent({lnum})</a>
Get the amount of indent for line {lnum} according the C
indenting rules, as with 'cindent'.
The indent is counted in spaces, the value of 'tabstop' is
relevant.  {lnum} is used just like in [getline()](#getline()).
When {lnum} is invalid -1 is returned.
See [C-indenting](#C-indenting).

Can also be used as a [method](#method):
```
GetLnum()->cindent()

### <a id="clearmatches()" class="section-title" href="#clearmatches()">clearmatches([{win}])</a>
Clears all matches previously defined for the current window
by [matchadd()| and the |:match](#matchadd()| and the |:match) commands.
If {win} is specified, use the window with this number or
window ID instead of the current window.

Can also be used as a [method](#method):
```
GetWin()->clearmatches()

```

### <a id="col()" class="section-title" href="#col()">Note:</a>
col({expr})	The result is a Number, which is the byte index of the column
position given with {expr}.  The accepted positions are:
.	    the cursor position
$	    the end of the cursor line (the result is the
number of bytes in the cursor line plus one)
'x	    position of mark x (if the mark is not set, 0 is
returned)
v       In Visual mode: the start of the Visual area (the
cursor is the end).  When not in Visual mode
returns the cursor position.  Differs from ['<](#'<) in
that it's updated right away.
Additionally {expr} can be [lnum, col]: a [List](#List) with the line
and column number. Most useful when the column is "$", to get
the last column of a specific line.  When "lnum" or "col" is
out of range then col() returns zero.
To get the line number use [line()](#line()).  To get both use
[getpos()](#getpos()).
For the screen column position use [virtcol()](#virtcol()).  For the
character position use [charcol()](#charcol()).
Note that only marks in the current file can be used.
Examples:
```
col(".")		column of cursor
col("$")		length of cursor line plus one
col("'t")		column of mark t
col("'" .. markname)	column of mark markname

```
		The first column is 1.  Returns 0 if {expr} is invalid.
For an uppercase mark the column may actually be in another
buffer.
For the cursor position, when 'virtualedit' is active, the
column is one higher if the cursor is after the end of the
line.  This can be used to obtain the column in Insert mode:
```
:imap <F2> <C-O>:let save_ve = &ve<CR>
\<C-O>:set ve=all<CR>
\<C-O>:echo col(".") .. "\n" <Bar>
\let &ve = save_ve<CR>


```
		Can also be used as a [method](#method):
```
GetPos()->col()

```


### <a id="complete() E785" class="section-title" href="#complete() E785">complete({startcol}, {matches})</a>
Set the matches for Insert mode completion.
Can only be used in Insert mode.  You need to use a mapping
with CTRL-R = (see [i_CTRL-R](#i_CTRL-R)).  It does not work after CTRL-O
or with an expression mapping.
{startcol} is the byte offset in the line where the completed
text start.  The text up to the cursor is the original text
that will be replaced by the matches.  Use col('.') for an
empty string.  "col('.') - 1" will replace one character by a
match.
{matches} must be a [List|.  Each |List](#List|.  Each |List) item is one match.
See [complete-items](#complete-items) for the kind of items that are possible.
"longest" in 'completeopt' is ignored.
Note that the after calling this function you need to avoid
inserting anything that would cause completion to stop.
The match can be selected with CTRL-N and CTRL-P as usual with
Insert mode completion.  The popup menu will appear if
specified, see [ins-completion-menu](#ins-completion-menu).
Example:
```
inoremap <F5> <C-R>=ListMonths()<CR>

func! ListMonths()
call complete(col('.'), ['January', 'February', 'March',
\ 'April', 'May', 'June', 'July', 'August', 'September',
\ 'October', 'November', 'December'])
return ''
endfunc

```
		This isn't very useful, but it shows how it works.  Note that
an empty string is returned to avoid a zero being inserted.

Can also be used as a [method](#method), the base is passed as the
second argument:
```
GetMatches()->complete(col('.'))

### <a id="complete_add()" class="section-title" href="#complete_add()">complete_add({expr})</a>
Add {expr} to the list of matches.  Only to be used by the
function specified with the 'completefunc' option.
Returns 0 for failure (empty string or out of memory),
1 when the match was added, 2 when the match was already in
the list.
See [complete-functions](#complete-functions) for an explanation of {expr}.  It is
the same as one item in the list that 'omnifunc' would return.

Can also be used as a [method](#method):
```
GetMoreMatches()->complete_add()

### <a id="complete_check()" class="section-title" href="#complete_check()">complete_check()</a>
Check for a key typed while looking for completion matches.
This is to be used when looking for matches takes some time.
Returns [TRUE](#TRUE) when searching for matches is to be aborted,
zero otherwise.
Only to be used by the function specified with the
'completefunc' option.


### <a id="complete_info()" class="section-title" href="#complete_info()">complete_info([{what}])</a>
Returns a [Dictionary](#Dictionary) with information about Insert mode
completion.  See [ins-completion](#ins-completion).
The items are:
mode		Current completion mode name string.
See [complete_info_mode](#complete_info_mode) for the values.
pum_visible	[TRUE](#TRUE) if popup menu is visible.
See [pumvisible()](#pumvisible()).
items	List of completion matches.  Each item is a
dictionary containing the entries "word",
"abbr", "menu", "kind", "info" and "user_data".
See [complete-items](#complete-items).
selected	Selected item index.  First index is zero.
Index is -1 if no item is selected (showing
typed text only, or the last completion after
no item is selected when using the <Up> or

```
Down> keys)
inserted	Inserted string. [NOT IMPLEMENTED YET]

### <a id="complete_info_mode" class="section-title" href="#complete_info_mode">Note:</a>
mode values are:
""		     Not in completion mode
"keyword"	     Keyword completion [i_CTRL-X_CTRL-N](#i_CTRL-X_CTRL-N)
"ctrl_x"	     Just pressed CTRL-X [i_CTRL-X](#i_CTRL-X)
"scroll"	     Scrolling with [i_CTRL-X_CTRL-E](#i_CTRL-X_CTRL-E) or
[i_CTRL-X_CTRL-Y](#i_CTRL-X_CTRL-Y)
"whole_line"	     Whole lines [i_CTRL-X_CTRL-L](#i_CTRL-X_CTRL-L)
"files"	     File names [i_CTRL-X_CTRL-F](#i_CTRL-X_CTRL-F)
"tags"	     Tags [i_CTRL-X_CTRL-]](#i_CTRL-X_CTRL-])
"path_defines"    Definition completion [i_CTRL-X_CTRL-D](#i_CTRL-X_CTRL-D)
"path_patterns"   Include completion [i_CTRL-X_CTRL-I](#i_CTRL-X_CTRL-I)
"dictionary"	     Dictionary [i_CTRL-X_CTRL-K](#i_CTRL-X_CTRL-K)
"thesaurus"	     Thesaurus [i_CTRL-X_CTRL-T](#i_CTRL-X_CTRL-T)
"cmdline"	     Vim Command line [i_CTRL-X_CTRL-V](#i_CTRL-X_CTRL-V)
"function"	     User defined completion [i_CTRL-X_CTRL-U](#i_CTRL-X_CTRL-U)
"omni"	     Omni completion [i_CTRL-X_CTRL-O](#i_CTRL-X_CTRL-O)
"spell"	     Spelling suggestions [i_CTRL-X_s](#i_CTRL-X_s)
"eval"	     [complete()](#complete()) completion
"unknown"	     Other internal modes

If the optional {what} list argument is supplied, then only
the items listed in {what} are returned.  Unsupported items in
{what} are silently ignored.

To get the position and size of the popup menu, see
[pum_getpos()|. It's also available in |v:event](#pum_getpos()|. It's also available in |v:event) during the
[CompleteChanged](#CompleteChanged) event.

Returns an empty [Dictionary](#Dictionary) on error.

Examples:
```
" Get all items
call complete_info()
" Get only 'mode'
call complete_info(['mode'])
" Get only 'mode' and 'pum_visible'
call complete_info(['mode', 'pum_visible'])


```
		Can also be used as a [method](#method):
```
GetItems()->complete_info()

```

### <a id="confirm()" class="section-title" href="#confirm()">Note:</a>
confirm({msg} [, {choices} [, {default} [, {type}]]])
confirm() offers the user a dialog, from which a choice can be
made.  It returns the number of the choice.  For the first
choice this is 1.

{msg} is displayed in a dialog with {choices} as the
alternatives.  When {choices} is missing or empty, "&OK" is
used (and translated).
{msg} is a String, use '\n' to include a newline.  Only on
some systems the string is wrapped when it doesn't fit.

{choices} is a String, with the individual choices separated
by '\n', e.g.
```
confirm("Save changes?", "&Yes\n&No\n&Cancel")

```
		The letter after the '&' is the shortcut key for that choice.
Thus you can type 'c' to select "Cancel".  The shortcut does
not need to be the first letter:
```
confirm("file has been modified", "&Save\nSave &All")

```
		For the console, the first letter of each choice is used as
the default shortcut key.  Case is ignored.

The optional {type} String argument gives the type of dialog.
It can be one of these values: "Error", "Question", "Info",
"Warning" or "Generic".  Only the first character is relevant.
When {type} is omitted, "Generic" is used.

The optional {type} argument gives the type of dialog.  This
is only used for the icon of the Win32 GUI.  It can be one of
these values: "Error", "Question", "Info", "Warning" or
"Generic".  Only the first character is relevant.
When {type} is omitted, "Generic" is used.

If the user aborts the dialog by pressing <Esc>, CTRL-C,
or another valid interrupt key, confirm() returns 0.

An example:
```
let choice = confirm("What do you want?",
\ "&Apples\n&Oranges\n&Bananas", 2)
if choice == 0
echo "make up your mind!"
elseif choice == 3
echo "tasteful"
else
echo "I prefer bananas myself."
endif

```
		In a GUI dialog, buttons are used.  The layout of the buttons
depends on the 'v' flag in 'guioptions'.  If it is included,
the buttons are always put vertically.  Otherwise,  confirm()
tries to put the buttons in one horizontal line.  If they
don't fit, a vertical layout is used anyway.  For some systems
the horizontal layout is always used.

Can also be used as a [method](#method)in:
```
BuildMessage()->confirm("&Yes\n&No")

```

### <a id="copy()" class="section-title" href="#copy()">Note:</a>
copy({expr})	Make a copy of {expr}.  For Numbers and Strings this isn't
different from using {expr} directly.
When {expr} is a [List](#List) a shallow copy is created.  This means
that the original [List](#List) can be changed without changing the
copy, and vice versa.  But the items are identical, thus
changing an item changes the contents of both [Lists](#Lists).
A [Dictionary| is copied in a similar way as a |List](#Dictionary| is copied in a similar way as a |List).
Also see [deepcopy()](#deepcopy()).
Can also be used as a [method](#method):
```
mylist->copy()

### <a id="cos()" class="section-title" href="#cos()">cos({expr})</a>
Return the cosine of {expr}, measured in radians, as a [Float](#Float).
{expr} must evaluate to a [Float| or a |Number](#Float| or a |Number).
Returns 0.0 if {expr} is not a [Float| or a |Number](#Float| or a |Number).
Examples:
```
:echo cos(100)

```
			0.862319
```
:echo cos(-4.01)

```
			-0.646043

Can also be used as a [method](#method):
```
Compute()->cos()

### <a id="cosh()" class="section-title" href="#cosh()">cosh({expr})</a>
Return the hyperbolic cosine of {expr} as a [Float](#Float) in the range
[1, inf].
{expr} must evaluate to a [Float| or a |Number](#Float| or a |Number).
Returns 0.0 if {expr} is not a [Float| or a |Number](#Float| or a |Number).
Examples:
```
:echo cosh(0.5)

```
			1.127626
```
:echo cosh(-0.5)

```
			-1.127626

Can also be used as a [method](#method):
```
Compute()->cosh()

### <a id="count()" class="section-title" href="#count()">count({comp}, {expr} [, {ic} [, {start}]])</a>
Return the number of times an item with value {expr} appears
in [String|, |List| or |Dictionary](#String|, |List| or |Dictionary) {comp}.

If {start} is given then start with the item with this index.
{start} can only be used with a [List](#List).

When {ic} is given and it's [TRUE](#TRUE) then case is ignored.

When {comp} is a string then the number of not overlapping
occurrences of {expr} is returned. Zero is returned when
{expr} is an empty string.

Can also be used as a [method](#method):
```
mylist->count(val)

```

### <a id="ctxget()" class="section-title" href="#ctxget()">ctxget([{index}])</a>
Returns a [Dictionary| representing the |context](#Dictionary| representing the |context) at {index}
from the top of the [context-stack| (see |context-dict](#context-stack| (see |context-dict)).
If {index} is not given, it is assumed to be 0 (i.e.: top).

### <a id="ctxpop()" class="section-title" href="#ctxpop()">ctxpop()</a>
Pops and restores the [context](#context) at the top of the
[context-stack](#context-stack).

### <a id="ctxpush()" class="section-title" href="#ctxpush()">ctxpush([{types}])</a>
Pushes the current editor state ([context](#context)) on the
[context-stack](#context-stack).
If {types} is given and is a [List| of |String](#List| of |String)s, it specifies
which [context-types](#context-types) to include in the pushed context.
Otherwise, all context types are included.

### <a id="ctxset()" class="section-title" href="#ctxset()">ctxset({context} [, {index}])</a>
Sets the [context](#context) at {index} from the top of the
[context-stack](#context-stack) to that represented by {context}.
{context} is a Dictionary with context data ([context-dict](#context-dict)).
If {index} is not given, it is assumed to be 0 (i.e.: top).

### <a id="ctxsize()" class="section-title" href="#ctxsize()">ctxsize()</a>
Returns the size of the [context-stack](#context-stack).

### <a id="cursor()" class="section-title" href="#cursor()">cursor({lnum}, {col} [, {off}])</a>
cursor({list})
Positions the cursor at the column (byte count) {col} in the
line {lnum}.  The first column is one.

When there is one argument {list} this is used as a [List](#List)
with two, three or four item:
[{lnum}, {col}]
[{lnum}, {col}, {off}]
[{lnum}, {col}, {off}, {curswant}]
This is like the return value of [getpos()| or |getcurpos()](#getpos()| or |getcurpos()),
but without the first item.

To position the cursor using the character count, use
[setcursorcharpos()](#setcursorcharpos()).

Does not change the jumplist.
{lnum} is used like with [getline()](#getline()), except that if {lnum} is
zero, the cursor will stay in the current line.
If {lnum} is greater than the number of lines in the buffer,
the cursor will be positioned at the last line in the buffer.
If {col} is greater than the number of bytes in the line,
the cursor will be positioned at the last character in the
line.
If {col} is zero, the cursor will stay in the current column.
If {curswant} is given it is used to set the preferred column
for vertical movement.  Otherwise {col} is used.

When 'virtualedit' is used {off} specifies the offset in
screen columns from the start of the character.  E.g., a
position within a <Tab> or after the last character.
Returns 0 when the position could be set, -1 otherwise.

Can also be used as a [method](#method):
```
GetCursorPos()->cursor()

### <a id="debugbreak()" class="section-title" href="#debugbreak()">debugbreak({pid})</a>
Specifically used to interrupt a program being debugged.  It
will cause process {pid} to get a SIGTRAP.  Behavior for other
processes is undefined. See [terminal-debug](#terminal-debug).
{Sends a SIGINT to a process {pid} other than MS-Windows}

Returns [TRUE](#TRUE) if successfully interrupted the program.
Otherwise returns [FALSE](#FALSE).

Can also be used as a [method](#method):
```
GetPid()->debugbreak()

### <a id="deepcopy() E698" class="section-title" href="#deepcopy() E698">deepcopy({expr} [, {noref}])</a>
Make a copy of {expr}.  For Numbers and Strings this isn't
different from using {expr} directly.
When {expr} is a [List](#List) a full copy is created.  This means
that the original [List](#List) can be changed without changing the
copy, and vice versa.  When an item is a [List](#List), a copy for it
is made, recursively.  Thus changing an item in the copy does
not change the contents of the original [List](#List).

When {noref} is omitted or zero a contained [List](#List) or
[Dictionary](#Dictionary) is only copied once.  All references point to
this single copy.  With {noref} set to 1 every occurrence of a
[List| or |Dictionary](#List| or |Dictionary) results in a new copy.  This also means
that a cyclic reference causes deepcopy() to fail.
### <a id="E724" class="section-title" href="#E724">Note:</a>
Nesting is possible up to 100 levels.  When there is an item
that refers back to a higher level making a deep copy with
{noref} set to 1 will fail.
Also see [copy()](#copy()).

Can also be used as a [method](#method):
```
GetObject()->deepcopy()

### <a id="delete()" class="section-title" href="#delete()">delete({fname} [, {flags}])</a>
Without {flags} or with {flags} empty: Deletes the file by the
name {fname}.

This also works when {fname} is a symbolic link.  The symbolic
link itself is deleted, not what it points to.

When {flags} is "d": Deletes the directory by the name
{fname}.  This fails when directory {fname} is not empty.

When {flags} is "rf": Deletes the directory by the name
{fname} and everything in it, recursively.  BE CAREFUL!
Note: on MS-Windows it is not possible to delete a directory
that is being used.

The result is a Number, which is 0/false if the delete
operation was successful and -1/true when the deletion failed
or partly failed.

Can also be used as a [method](#method):
```
GetName()->delete()

### <a id="deletebufline()" class="section-title" href="#deletebufline()">deletebufline({buf}, {first} [, {last}])</a>
Delete lines {first} to {last} (inclusive) from buffer {buf}.
If {last} is omitted then delete line {first} only.
On success 0 is returned, on failure 1 is returned.

This function works only for loaded buffers. First call
[bufload()](#bufload()) if needed.

For the use of {buf}, see [bufname()](#bufname()) above.

{first} and {last} are used like with [getline()](#getline()). Note that
when using [line()](#line()) this refers to the current buffer. Use "$"
to refer to the last line in buffer {buf}.

Can also be used as a [method](#method):
```
GetBuffer()->deletebufline(1)

```

### <a id="dictwatcheradd()" class="section-title" href="#dictwatcheradd()">dictwatcheradd({dict}, {pattern}, {callback})</a>
Adds a watcher to a dictionary. A dictionary watcher is
identified by three components:

- A dictionary({dict});
- A key pattern({pattern}).
- A function({callback}).

After this is called, every change on {dict} and on keys
matching {pattern} will result in {callback} being invoked.

For example, to watch all global variables:
```
### <a id="silent! call dictwatcherdel(g:, '', 'OnDictChanged')" class="section-title" href="#silent! call dictwatcherdel(g:, '', 'OnDictChanged')">Note:</a>
function! OnDictChanged(d,k,z)
echomsg string(a:k) string(a:z)
endfunction
### <a id="call dictwatcheradd(g:, '', 'OnDictChanged')" class="section-title" href="#call dictwatcheradd(g:, '', 'OnDictChanged')">Note:</a>

```

For now {pattern} only accepts very simple patterns that can
### <a id="contain a '' at the end of the string, in which case it will" class="section-title" href="#contain a '' at the end of the string, in which case it will">Note:</a>
### <a id="match every key that begins with the substring before the ''." class="section-title" href="#match every key that begins with the substring before the ''.">Note:</a>
### <a id="That means if '' is not the last character of {pattern}, only" class="section-title" href="#That means if '' is not the last character of {pattern}, only">Note:</a>
keys that are exactly equal as {pattern} will be matched.

The {callback} receives three arguments:

- The dictionary being watched.
- The key which changed.
- A dictionary containing the new and old values for the key.

The type of change can be determined by examining the keys
present on the third argument:

- If contains both `old` and `new`, the key was updated.
- If it contains only `new`, the key was added.
- If it contains only `old`, the key was deleted.

This function can be used by plugins to implement options with
validation and parsing logic.

### <a id="dictwatcherdel()" class="section-title" href="#dictwatcherdel()">dictwatcherdel({dict}, {pattern}, {callback})</a>
Removes a watcher added  with [dictwatcheradd()](#dictwatcheradd()). All three
arguments must match the ones passed to [dictwatcheradd()](#dictwatcheradd()) in
order for the watcher to be successfully deleted.

### <a id="did_filetype()" class="section-title" href="#did_filetype()">Note:</a>
did_filetype()	Returns [TRUE](#TRUE) when autocommands are being executed and the
FileType event has been triggered at least once.  Can be used
to avoid triggering the FileType event again in the scripts
that detect the file type. [FileType](#FileType)
Returns [FALSE](#FALSE) when `:setf FALLBACK` was used.
When editing another file, the counter is reset, thus this
really checks if the FileType event has been triggered for the
current buffer.  This allows an autocommand that starts
editing another buffer to set 'filetype' and load a syntax
file.

### <a id="diff_filler()" class="section-title" href="#diff_filler()">diff_filler({lnum})</a>
Returns the number of filler lines above line {lnum}.
These are the lines that were inserted at this point in
another diff'ed window.  These filler lines are shown in the
display but don't exist in the buffer.
{lnum} is used like with [getline()](#getline()).  Thus "." is the current
line, "'m" mark m, etc.
Returns 0 if the current window is not in diff mode.

Can also be used as a [method](#method):
```
GetLnum()->diff_filler()

### <a id="diff_hlID()" class="section-title" href="#diff_hlID()">diff_hlID({lnum}, {col})</a>
Returns the highlight ID for diff mode at line {lnum} column
{col} (byte index).  When the current line does not have a
diff change zero is returned.
{lnum} is used like with [getline()](#getline()).  Thus "." is the current
line, "'m" mark m, etc.
{col} is 1 for the leftmost column, {lnum} is 1 for the first
line.
The highlight ID can be used with [synIDattr()](#synIDattr()) to obtain
syntax information about the highlighting.

Can also be used as a [method](#method):
```
GetLnum()->diff_hlID(col)

```


### <a id="digraph_get() E1214" class="section-title" href="#digraph_get() E1214">digraph_get({chars})</a>
Return the digraph of {chars}.  This should be a string with
exactly two characters.  If {chars} are not just two
characters, or the digraph of {chars} does not exist, an error
is given and an empty string is returned.

Also see [digraph_getlist()](#digraph_getlist()).

Examples:
```
" Get a built-in digraph
:echo digraph_get('00')		" Returns '∞'

" Get a user-defined digraph
:call digraph_set('aa', 'あ')
:echo digraph_get('aa')		" Returns 'あ'

```

Can also be used as a [method](#method):
```
GetChars()->digraph_get()

```


### <a id="digraph_getlist()" class="section-title" href="#digraph_getlist()">digraph_getlist([{listall}])</a>
Return a list of digraphs.  If the {listall} argument is given
and it is TRUE, return all digraphs, including the default
digraphs.  Otherwise, return only user-defined digraphs.

Also see [digraph_get()](#digraph_get()).

Examples:
```
" Get user-defined digraphs
:echo digraph_getlist()

" Get all the digraphs, including default digraphs
:echo digraph_getlist(1)

```

Can also be used as a [method](#method):
```
GetNumber()->digraph_getlist()

```


### <a id="digraph_set()" class="section-title" href="#digraph_set()">digraph_set({chars}, {digraph})</a>
Add digraph {chars} to the list.  {chars} must be a string
with two characters.  {digraph} is a string with one UTF-8
encoded character.  *E1215*
Be careful, composing characters are NOT ignored.  This
function is similar to [:digraphs](#:digraphs) command, but useful to add
digraphs start with a white space.

The function result is v:true if [digraph](#digraph) is registered.  If
this fails an error message is given and v:false is returned.

If you want to define multiple digraphs at once, you can use
[digraph_setlist()](#digraph_setlist()).

Example:
```
call digraph_set('  ', 'あ')

```

Can be used as a [method](#method):
```
GetString()->digraph_set('あ')

```


### <a id="digraph_setlist()" class="section-title" href="#digraph_setlist()">digraph_setlist({digraphlist})</a>
Similar to [digraph_set()](#digraph_set()) but this function can add multiple
digraphs at once.  {digraphlist} is a list composed of lists,
where each list contains two strings with {chars} and
### <a id="{digraph} as in [digraph_set()|. E1216" class="section-title" href="#{digraph} as in |digraph_set()](#digraph_set()|. E1216" class="section-title" href="#{digraph} as in |digraph_set()). E1216">Note:</a>
Example:
```
call digraph_setlist([['aa', 'あ'], ['ii', 'い']])

```

It is similar to the following:
```
for [chars, digraph] in [['aa', 'あ'], ['ii', 'い']]
call digraph_set(chars, digraph)
endfor

```
		Except that the function returns after the first error,
following digraphs will not be added.

Can be used as a [method](#method):
```
GetList()->digraph_setlist()

```


### <a id="empty()" class="section-title" href="#empty()">empty({expr})</a>
Return the Number 1 if {expr} is empty, zero otherwise.
- A [List| or |Dictionary](#List| or |Dictionary) is empty when it does not have any
items.
- A [String](#String) is empty when its length is zero.
- A [Number| and |Float](#Number| and |Float) are empty when their value is zero.
- [v:false| and |v:null| are empty, |v:true](#v:false| and |v:null| are empty, |v:true) is not.
- A [Blob](#Blob) is empty when its length is zero.

Can also be used as a [method](#method):
```
mylist->empty()

### <a id="environ()" class="section-title" href="#environ()">environ()</a>
Return all of environment variables as dictionary. You can
check if an environment variable exists like this:
```
:echo has_key(environ(), 'HOME')

```
		Note that the variable name may be CamelCase; to ignore case
use this:
```
:echo index(keys(environ()), 'HOME', 0, 1) != -1

### <a id="escape()" class="section-title" href="#escape()">escape({string}, {chars})</a>
Escape the characters in {chars} that occur in {string} with a
backslash.  Example:
```
:echo escape('c:\program files\vim', ' \')

```
		results in:
```
c:\\program\ files\\vim

```
		Also see [shellescape()| and |fnameescape()](#shellescape()| and |fnameescape()).

Can also be used as a [method](#method):
```
GetText()->escape(' \')

```

### <a id="eval()" class="section-title" href="#eval()">Note:</a>
eval({string})	Evaluate {string} and return the result.  Especially useful to
turn the result of [string()](#string()) back into the original value.
This works for Numbers, Floats, Strings, Blobs and composites
of them.  Also works for [Funcref](#Funcref)s that refer to existing
functions.

Can also be used as a [method](#method):
```
argv->join()->eval()

### <a id="eventhandler()" class="section-title" href="#eventhandler()">eventhandler()</a>
Returns 1 when inside an event handler.  That is that Vim got
interrupted while waiting for the user to type a character,
e.g., when dropping a file on Vim.  This means interactive
commands cannot be used.  Otherwise zero is returned.

### <a id="executable()" class="section-title" href="#executable()">executable({expr})</a>
This function checks if an executable with the name {expr}
exists.  {expr} must be the name of the program without any
arguments.
executable() uses the value of $PATH and/or the normal
searchpath for programs.		*PATHEXT*
On MS-Windows the ".exe", ".bat", etc. can optionally be
included.  Then the extensions in $PATHEXT are tried.  Thus if
"foo.exe" does not exist, "foo.exe.bat" can be found.  If
$PATHEXT is not set then ".exe;.com;.bat;.cmd" is used.  A dot
by itself can be used in $PATHEXT to try using the name
without an extension.  When 'shell' looks like a Unix shell,
then the name is also tried without adding an extension.
On MS-Windows it only checks if the file exists and is not a
directory, not if it's really executable.
On Windows an executable in the same directory as Vim is
always found (it is added to $PATH at [startup](#startup)).
The result is a Number:
1	exists
0	does not exist
-1	not implemented on this system
[exepath()](#exepath()) can be used to get the full path of an executable.

Can also be used as a [method](#method):
```
GetCommand()->executable()

### <a id="execute()" class="section-title" href="#execute()">execute({command} [, {silent}])</a>
Execute {command} and capture its output.
If {command} is a [String](#String), returns {command} output.
If {command} is a [List](#List), returns concatenated outputs.
Examples:
```
echo execute('echon "foo"')

```
			foo
```
echo execute(['echon "foo"', 'echon "bar"'])

```
			foobar

The optional {silent} argument can have these values:
""		no `:silent` used
"silent"	`:silent` used
"silent!"	`:silent!` used
The default is "silent".  Note that with "silent!", unlike
`:redir`, error messages are dropped.

To get a list of lines use [split()](#split()) on the result:
```
execute('args')->split("\n")


```
		This function is not available in the [sandbox](#sandbox).
Note: If nested, an outer execute() will not observe output of
the inner calls.
Note: Text attributes (highlights) are not captured.
To execute a command in another window than the current one
use `win_execute()`.

Can also be used as a [method](#method):
```
GetCommand()->execute()

### <a id="exepath()" class="section-title" href="#exepath()">exepath({expr})</a>
Returns the full path of {expr} if it is an executable and
given as a (partial or full) path or is found in $PATH.
Returns empty string otherwise.
If {expr} starts with "./" the [current-directory](#current-directory) is used.

Can also be used as a [method](#method):
```
GetCommand()->exepath()

```

### <a id="exists()" class="section-title" href="#exists()">Note:</a>
exists({expr})	The result is a Number, which is [TRUE](#TRUE) if {expr} is
defined, zero otherwise.

For checking for a supported feature use [has()](#has()).
For checking if a file exists use [filereadable()](#filereadable()).

The {expr} argument is a string, which contains one of these:
varname		internal variable (see
dict.key	[internal-variables](#internal-variables)).  Also works
list[i]		for [curly-braces-names|, |Dictionary](#curly-braces-names|, |Dictionary)
entries, [List](#List) items, etc.
Beware that evaluating an index may
cause an error message for an invalid
expression.  E.g.:
```
:let l = [1, 2, 3]
:echo exists("l[5]")

```
					   0
```
:echo exists("l[xx]")

```
					   E121: Undefined variable: xx
0
&option-name	Vim option (only checks if it exists,
not if it really works)
+option-name	Vim option that works.
$ENVNAME	environment variable (could also be
done by comparing with an empty
string)
### <a id="funcname	built-in function (see [functions|)" class="section-title" href="#funcname	built-in function (see |functions](#functions|)" class="section-title" href="#funcname	built-in function (see |functions))">Note:</a>
or user defined function (see
[user-function](#user-function)). Also works for a
variable that is a Funcref.
:cmdname	Ex command: built-in command, user
command or command modifier [:command](#:command).
Returns:
1  for match with start of a command
2  full match with a command
3  matches several user commands
To check for a supported command
always check the return value to be 2.
:2match		The [:2match](#:2match) command.
:3match		The [:3match](#:3match) command (but you
probably should not use it, it is
reserved for internal usage)
#event		autocommand defined for this event
#event#pattern	autocommand defined for this event and
pattern (the pattern is taken
literally and compared to the
autocommand patterns character by
character)
#group		autocommand group exists
#group#event	autocommand defined for this group and
event.
#group#event#pattern
autocommand defined for this group,
event and pattern.
##event		autocommand for this event is
supported.

Examples:
```
exists("&mouse")
exists("$HOSTNAME")
### <a id="exists("strftime")" class="section-title" href="#exists("strftime")">Note:</a>
### <a id="exists("s:MyFunc")" class="section-title" href="#exists("s:MyFunc")">Note:</a>
### <a id="exists("MyFunc")" class="section-title" href="#exists("MyFunc")">Note:</a>
exists("bufcount")
exists(":Make")
exists("#CursorHold")
### <a id="exists("#BufReadPre#.gz")" class="section-title" href="#exists("#BufReadPre#.gz")">Note:</a>
exists("#filetypeindent")
exists("#filetypeindent#FileType")
### <a id="exists("#filetypeindent#FileType#")" class="section-title" href="#exists("#filetypeindent#FileType#")">Note:</a>
exists("##ColorScheme")
### <a id="There must be no space between the symbol (&/$//#) and the" class="section-title" href="#There must be no space between the symbol (&/$//#) and the"><</a>
name.
There must be no extra characters after the name, although in
a few cases this is ignored.  That may become stricter in the
future, thus don't count on it!
Working example:
```
exists(":make")

```
		NOT working example:
```
exists(":make install")


```
		Note that the argument must be a string, not the name of the
variable itself.  For example:
```
exists(bufcount)

```
		This doesn't check for existence of the "bufcount" variable,
but gets the value of "bufcount", and checks if that exists.

Can also be used as a [method](#method):
```
Varname()->exists()

### <a id="exp()" class="section-title" href="#exp()">exp({expr})</a>
Return the exponential of {expr} as a [Float](#Float) in the range
[0, inf].
{expr} must evaluate to a [Float| or a |Number](#Float| or a |Number).
Returns 0.0 if {expr} is not a [Float| or a |Number](#Float| or a |Number).
Examples:
```
:echo exp(2)

```
			7.389056
```
:echo exp(-1)

```
			0.367879

Can also be used as a [method](#method):
```
Compute()->exp()

### <a id="expand()" class="section-title" href="#expand()">expand({string} [, {nosuf} [, {list}]])</a>
Expand wildcards and the following special keywords in 
{string}.  'wildignorecase' applies.

If {list} is given and it is [TRUE](#TRUE), a List will be returned.
Otherwise the result is a String and when there are several
matches, they are separated by <NL> characters.

If the expansion fails, the result is an empty string.  A name
for a non-existing file is not included, unless {string} does
not start with '%', '#' or '<', see below.

When {string} starts with '%', '#' or '<', the expansion is
done like for the [cmdline-special](#cmdline-special) variables with their
associated modifiers.  Here is a short overview:

%		current file name
#		alternate file name
#n		alternate file name n

```
cfile>		file name under the cursor

```
afile>		autocmd file name

```
abuf>		autocmd buffer number (as a String!)

```
amatch>	autocmd matched name

```
cexpr>		C expression under the cursor

```
sfile>		sourced script file or function name

```
slnum>		sourced script line number or function
line number

```
sflnum>	script file line number, also when in
a function

```
SID>		"<SNR>123_"  where "123" is the
current script ID  [<SID>](#<SID>)

```
script>	sourced script file, or script file
where the current function was defined

```
stack>		call stack

```
cword>		word under the cursor

```
cWORD>		WORD under the cursor

```
client>	the {clientid} of the last received
message
Modifiers:
:p		expand to full path
:h		head (last path component removed)
:t		tail (last path component only)
:r		root (one extension removed)
:e		extension only

Example:
```
:let &tags = expand("%:p:h") .. "/tags"

```
		Note that when expanding a string that starts with '%', '#' or
'<', any following text is ignored.  This does NOT work:
```
:let doesntwork = expand("%:h.bak")

```
		Use this:
```
:let doeswork = expand("%:h") .. ".bak"

```
		Also note that expanding "<cfile>" and others only returns the
referenced file name without further expansion.  If "<cfile>"
is "~/.cshrc", you need to do another expand() to have the
"~/" expanded into the path of the home directory:
```
:echo expand(expand("<cfile>"))

```

There cannot be white space between the variables and the
following modifier.  The [fnamemodify()](#fnamemodify()) function can be used
to modify normal file names.

When using '%' or '#', and the current or alternate file name
is not defined, an empty string is used.  Using "%:p" in a
buffer with no name, results in the current directory, with a
'/' added.
When 'verbose' is set then expanding '%', '#' and <> items
will result in an error message if the argument cannot be
expanded.

When {string} does not start with '%', '#' or '<', it is
expanded like a file name is expanded on the command line.
'suffixes' and 'wildignore' are used, unless the optional
{nosuf} argument is given and it is [TRUE](#TRUE).
Names for non-existing files are included.  The "**" item can
be used to search in a directory tree.  For example, to find
all "README" files in the current directory and below:
```
### <a id=":echo expand("/README")" class="section-title" href="#:echo expand("/README")">Note:</a>

```

expand() can also be used to expand variables and environment
variables that are only known in a shell.  But this can be
slow, because a shell may be used to do the expansion.  See
[expr-env-expand](#expr-env-expand).
The expanded variable is still handled like a list of file
names.  When an environment variable cannot be expanded, it is
left unchanged.  Thus ":echo expand('$FOOBAR')" results in
"$FOOBAR".

See [glob()| for finding existing files.  See |system()](#glob()| for finding existing files.  See |system()) for
getting the raw output of an external command.

Can also be used as a [method](#method):
```
Getpattern()->expand()

### <a id="expandcmd()" class="section-title" href="#expandcmd()">expandcmd({string})</a>
Expand special items in String {string} like what is done for
an Ex command such as `:edit`.  This expands special keywords,
like with [expand()](#expand()), and environment variables, anywhere in
{string}.  "~user" and "~/path" are only expanded at the
start.
Returns the expanded string.  If an error is encountered
during expansion, the unmodified {string} is returned.
Example:
```
:echo expandcmd('make %<.o')

```
			make /path/runtime/doc/builtin.o ~

Can also be used as a [method](#method):
```
GetCommand()->expandcmd()

```

### <a id="extend()" class="section-title" href="#extend()">extend({expr1}, {expr2} [, {expr3}])</a>
{expr1} and {expr2} must be both [Lists](#Lists) or both
[Dictionaries](#Dictionaries).

If they are [Lists](#Lists): Append {expr2} to {expr1}.
If {expr3} is given insert the items of {expr2} before the
item with index {expr3} in {expr1}.  When {expr3} is zero
insert before the first item.  When {expr3} is equal to
len({expr1}) then {expr2} is appended.
Examples:
```
:echo sort(extend(mylist, [7, 5]))
:call extend(mylist, [2, 3], 1)

```
		When {expr1} is the same List as {expr2} then the number of
items copied is equal to the original length of the List.
E.g., when {expr3} is 1 you get N new copies of the first item
(where N is the original length of the List).
Use [add()](#add()) to concatenate one item to a list.  To concatenate
two lists into a new list use the + operator:
```
:let newlist = [1, 2, 3] + [4, 5]

```

If they are [Dictionaries](#Dictionaries):
Add all entries from {expr2} to {expr1}.
If a key exists in both {expr1} and {expr2} then {expr3} is
used to decide what to do:
{expr3} = "keep": keep the value of {expr1}
{expr3} = "force": use the value of {expr2}
{expr3} = "error": give an error message		*E737*
When {expr3} is omitted then "force" is assumed.

{expr1} is changed when {expr2} is not empty.  If necessary
make a copy of {expr1} first.
{expr2} remains unchanged.
When {expr1} is locked and {expr2} is not empty the operation
fails.
Returns {expr1}.  Returns 0 on error.

Can also be used as a [method](#method):
```
mylist->extend(otherlist)

### <a id="feedkeys()" class="section-title" href="#feedkeys()">feedkeys({string} [, {mode}])</a>
Characters in {string} are queued for processing as if they
come from a mapping or were typed by the user.

By default the string is added to the end of the typeahead
buffer, thus if a mapping is still being executed the
characters come after them.  Use the 'i' flag to insert before
other characters, they will be executed next, before any
characters from a mapping.

The function does not wait for processing of keys contained in
{string}.

To include special keys into {string}, use double-quotes
and "\..." notation [expr-quote](#expr-quote). For example,
feedkeys("\<CR>") simulates pressing of the <Enter> key. But
feedkeys('\<CR>') pushes 5 characters.
The [<Ignore>](#<Ignore>) keycode may be used to exit the
wait-for-character without doing anything.

{mode} is a String, which can contain these character flags:
'm'	Remap keys. This is default.  If {mode} is absent,
keys are remapped.
'n'	Do not remap keys.
't'	Handle keys as if typed; otherwise they are handled as
if coming from a mapping.  This matters for undo,
opening folds, etc.
'i'	Insert the string instead of appending (see above).
'x'	Execute commands until typeahead is empty.  This is
similar to using ":normal!".  You can call feedkeys()
several times without 'x' and then one time with 'x'
(possibly with an empty {string}) to execute all the
typeahead.  Note that when Vim ends in Insert mode it
will behave as if <Esc> is typed, to avoid getting
stuck, waiting for a character to be typed before the
script continues.
Note that if you manage to call feedkeys() while
executing commands, thus calling it recursively, then
all typeahead will be consumed by the last call.
'!'	When used with 'x' will not end Insert mode. Can be
used in a test when a timer is set to exit Insert mode
a little later.  Useful for testing CursorHoldI.

Return value is always 0.

Can also be used as a [method](#method):
```
GetInput()->feedkeys()

### <a id="filereadable()" class="section-title" href="#filereadable()">filereadable({file})</a>
The result is a Number, which is [TRUE](#TRUE) when a file with the
name {file} exists, and can be read.  If {file} doesn't exist,
or is a directory, the result is [FALSE](#FALSE).  {file} is any
expression, which is used as a String.
If you don't care about the file being readable you can use
[glob()](#glob()).
{file} is used as-is, you may want to expand wildcards first:
```
echo filereadable('~/.vimrc')
0
echo filereadable(expand('~/.vimrc'))
1


```
		Can also be used as a [method](#method):
```
GetName()->filereadable()

### <a id="filewritable()" class="section-title" href="#filewritable()">filewritable({file})</a>
The result is a Number, which is 1 when a file with the
name {file} exists, and can be written.  If {file} doesn't
exist, or is not writable, the result is 0.  If {file} is a
directory, and we can write to it, the result is 2.

Can also be used as a [method](#method):
```
GetName()->filewritable()

### <a id="filter()" class="section-title" href="#filter()">filter({expr1}, {expr2})</a>
{expr1} must be a [List|, |Blob|, or a |Dictionary](#List|, |Blob|, or a |Dictionary).
For each item in {expr1} evaluate {expr2} and when the result
is zero remove the item from the [List| or |Dictionary](#List| or |Dictionary). For a
[Blob](#Blob) each byte is removed.

{expr2} must be a [string| or |Funcref](#string| or |Funcref).

If {expr2} is a [string|, inside {expr2} |v:val](#string|, inside {expr2} |v:val) has the value
of the current item.  For a [Dictionary| |v:key](#Dictionary| |v:key) has the key
of the current item and for a [List| |v:key](#List| |v:key) has the index of
the current item.  For a [Blob| |v:key](#Blob| |v:key) has the index of the
current byte.

Examples:
```
call filter(mylist, 'v:val !~ "OLD"')

```
		Removes the items where "OLD" appears.
```
call filter(mydict, 'v:key >= 8')

```
		Removes the items with a key below 8.
```
call filter(var, 0)

```
		Removes all the items, thus clears the [List| or |Dictionary](#List| or |Dictionary).

Note that {expr2} is the result of expression and is then
used as an expression again.  Often it is good to use a
[literal-string](#literal-string) to avoid having to double backslashes.

If {expr2} is a [Funcref](#Funcref) it must take two arguments:
1. the key or the index of the current item.
2. the value of the current item.
The function must return [TRUE](#TRUE) if the item should be kept.
Example that keeps the odd items of a list:
```
func Odd(idx, val)
return a:idx % 2 == 1
endfunc
call filter(mylist, function('Odd'))

```
		It is shorter when using a [lambda](#lambda):
```
### <a id="call filter(myList, {idx, val -> idx  val <= 42})" class="section-title" href="#call filter(myList, {idx, val -> idx  val <= 42})">Note:</a>

```
		If you do not use "val" you can leave it out:
```
call filter(myList, {idx -> idx % 2 == 1})

```

The operation is done in-place.  If you want a [List](#List) or
[Dictionary](#Dictionary) to remain unmodified make a copy first:
```
:let l = filter(copy(mylist), 'v:val =~ "KEEP"')


```
		Returns {expr1}, the [List|, |Blob| or |Dictionary](#List|, |Blob| or |Dictionary) that was
filtered.  When an error is encountered while evaluating
{expr2} no further items in {expr1} are processed.  When
{expr2} is a Funcref errors inside a function are ignored,
unless it was defined with the "abort" flag.

Can also be used as a [method](#method):
```
mylist->filter(expr2)

### <a id="finddir()" class="section-title" href="#finddir()">finddir({name} [, {path} [, {count}]])</a>
Find directory {name} in {path}.  Supports both downwards and
upwards recursive directory searches.  See [file-searching](#file-searching)
for the syntax of {path}.

Returns the path of the first found match.  When the found
directory is below the current directory a relative path is
returned.  Otherwise a full path is returned.
If {path} is omitted or empty then 'path' is used.

If the optional {count} is given, find {count}'s occurrence of
{name} in {path} instead of the first one.
When {count} is negative return all the matches in a [List](#List).

Returns an empty string if the directory is not found.

This is quite similar to the ex-command `:find`.

Can also be used as a [method](#method):
```
GetName()->finddir()

### <a id="findfile()" class="section-title" href="#findfile()">findfile({name} [, {path} [, {count}]])</a>
Just like [finddir()](#finddir()), but find a file instead of a directory.
Uses 'suffixesadd'.
Example:
```
:echo findfile("tags.vim", ".;")

```
		Searches from the directory of the current file upwards until
it finds the file "tags.vim".

Can also be used as a [method](#method):
```
GetName()->findfile()

### <a id="flatten()" class="section-title" href="#flatten()">flatten({list} [, {maxdepth}])</a>
Flatten {list} up to {maxdepth} levels.  Without {maxdepth}
the result is a [List](#List) without nesting, as if {maxdepth} is
a very large number.
The {list} is changed in place, make a copy first if you do
not want that.
### <a id="E900" class="section-title" href="#E900">Note:</a>
{maxdepth} means how deep in nested lists changes are made.
{list} is not modified when {maxdepth} is 0.
{maxdepth} must be positive number.

If there is an error the number zero is returned.

Example:
```
:echo flatten([1, [2, [3, 4]], 5])

```
			[1, 2, 3, 4, 5]
```
:echo flatten([1, [2, [3, 4]], 5], 1)

```
			[1, 2, [3, 4], 5]

Can also be used as a [method](#method):
```
mylist->flatten()

```

### <a id="float2nr()" class="section-title" href="#float2nr()">float2nr({expr})</a>
Convert {expr} to a Number by omitting the part after the
decimal point.
{expr} must evaluate to a [Float](#Float) or a Number.
Returns 0 if {expr} is not a [Float| or a |Number](#Float| or a |Number).
When the value of {expr} is out of range for a [Number](#Number) the
result is truncated to 0x7fffffff or -0x7fffffff (or when
64-bit Number support is enabled, 0x7fffffffffffffff or
-0x7fffffffffffffff).  NaN results in -0x80000000 (or when
64-bit Number support is enabled, -0x8000000000000000).
Examples:
```
echo float2nr(3.95)

```
			3
```
echo float2nr(-23.45)

```
			-23
```
echo float2nr(1.0e100)

```
			2147483647  (or 9223372036854775807)
```
echo float2nr(-1.0e150)

```
			-2147483647 (or -9223372036854775807)
```
echo float2nr(1.0e-100)

```
			0

Can also be used as a [method](#method):
```
Compute()->float2nr()

### <a id="floor()" class="section-title" href="#floor()">floor({expr})</a>
Return the largest integral value less than or equal to
{expr} as a [Float](#Float) (round down).
{expr} must evaluate to a [Float| or a |Number](#Float| or a |Number).
Returns 0.0 if {expr} is not a [Float| or a |Number](#Float| or a |Number).
Examples:
```
echo floor(1.856)

```
			1.0
```
echo floor(-5.456)

```
			-6.0
```
echo floor(4.0)

```
			4.0

Can also be used as a [method](#method):
```
Compute()->floor()

### <a id="fmod()" class="section-title" href="#fmod()">fmod({expr1}, {expr2})</a>
Return the remainder of {expr1} / {expr2}, even if the
division is not representable.  Returns {expr1} - i * {expr2}
for some integer i such that if {expr2} is non-zero, the
result has the same sign as {expr1} and magnitude less than
the magnitude of {expr2}.  If {expr2} is zero, the value
returned is zero.  The value returned is a [Float](#Float).
{expr1} and {expr2} must evaluate to a [Float| or a |Number](#Float| or a |Number).
Returns 0.0 if {expr1} or {expr2} is not a [Float](#Float) or a
[Number](#Number).
Examples:
```
:echo fmod(12.33, 1.22)

```
			0.13
```
:echo fmod(-12.33, 1.22)

```
			-0.13

Can also be used as a [method](#method):
```
Compute()->fmod(1.22)

### <a id="fnameescape()" class="section-title" href="#fnameescape()">fnameescape({string})</a>
Escape {string} for use as file name command argument.  All
characters that have a special meaning, such as '%' and '|'
are escaped with a backslash.
For most systems the characters escaped are
### <a id="" \t\n?[{`$\\%#'\"[!<"." class="section-title" href="#" \t\n?[{`$\\%#'\"](#!<"." class="section-title" href="#" \t\n?[{`$\\%#'\")!<".">Note:</a>
appears in a filename, it depends on the value of 'isfname'.
A leading '+' and '>' is also escaped (special after [:edit](#:edit)
and [:write|).  And a "-" by itself (special after |:cd](#:write|).  And a "-" by itself (special after |:cd)).
Returns an empty string on error.
Example:
```
:let fname = '+some str%nge|name'
:exe "edit " .. fnameescape(fname)

```
		results in executing:
```
edit \+some\ str\%nge\|name

```

Can also be used as a [method](#method):
```
GetName()->fnameescape()

### <a id="fnamemodify()" class="section-title" href="#fnamemodify()">fnamemodify({fname}, {mods})</a>
Modify file name {fname} according to {mods}.  {mods} is a
string of characters like it is used for file names on the
command line.  See [filename-modifiers](#filename-modifiers).
Example:
```
:echo fnamemodify("main.c", ":p:h")

```
		results in:
```
/home/user/vim/vim/src

```
		If {mods} is empty or an unsupported modifier is used then
{fname} is returned.
When {fname} is empty then with {mods} ":h" returns ".", so
that `:cd` can be used with it.  This is different from
expand('%:h') without a buffer name, which returns an empty
string.
Note: Environment variables don't work in {fname}, use
[expand()](#expand()) first then.

Can also be used as a [method](#method):
```
GetName()->fnamemodify(':p:h')

### <a id="foldclosed()" class="section-title" href="#foldclosed()">foldclosed({lnum})</a>
The result is a Number.  If the line {lnum} is in a closed
fold, the result is the number of the first line in that fold.
If the line {lnum} is not in a closed fold, -1 is returned.
{lnum} is used like with [getline()](#getline()).  Thus "." is the current
line, "'m" mark m, etc.

Can also be used as a [method](#method):
```
GetLnum()->foldclosed()

### <a id="foldclosedend()" class="section-title" href="#foldclosedend()">foldclosedend({lnum})</a>
The result is a Number.  If the line {lnum} is in a closed
fold, the result is the number of the last line in that fold.
If the line {lnum} is not in a closed fold, -1 is returned.
{lnum} is used like with [getline()](#getline()).  Thus "." is the current
line, "'m" mark m, etc.

Can also be used as a [method](#method):
```
GetLnum()->foldclosedend()

### <a id="foldlevel()" class="section-title" href="#foldlevel()">foldlevel({lnum})</a>
The result is a Number, which is the foldlevel of line {lnum}
in the current buffer.  For nested folds the deepest level is
returned.  If there is no fold at line {lnum}, zero is
returned.  It doesn't matter if the folds are open or closed.
When used while updating folds (from 'foldexpr') -1 is
returned for lines where folds are still to be updated and the
foldlevel is unknown.  As a special case the level of the
previous line is usually available.
{lnum} is used like with [getline()](#getline()).  Thus "." is the current
line, "'m" mark m, etc.

Can also be used as a [method](#method):
```
GetLnum()->foldlevel()

```

### <a id="foldtext()" class="section-title" href="#foldtext()">Note:</a>
foldtext()	Returns a String, to be displayed for a closed fold.  This is
the default function used for the 'foldtext' option and should
only be called from evaluating 'foldtext'.  It uses the
[v:foldstart|, |v:foldend| and |v:folddashes](#v:foldstart|, |v:foldend| and |v:folddashes) variables.
The returned string looks like this:
```
+-- 45 lines: abcdef

```
		The number of leading dashes depends on the foldlevel.  The
"45" is the number of lines in the fold.  "abcdef" is the text
in the first non-blank line of the fold.  Leading white space,
### <a id=""//" or "/" and the text from the 'foldmarker' and" class="section-title" href="#"//" or "/" and the text from the 'foldmarker' and">Note:</a>
'commentstring' options is removed.
When used to draw the actual foldtext, the rest of the line
will be filled with the fold char from the 'fillchars'
setting.
Returns an empty string when there is no fold.

### <a id="foldtextresult()" class="section-title" href="#foldtextresult()">foldtextresult({lnum})</a>
Returns the text that is displayed for the closed fold at line
{lnum}.  Evaluates 'foldtext' in the appropriate context.
When there is no closed fold at {lnum} an empty string is
returned.
{lnum} is used like with [getline()](#getline()).  Thus "." is the current
line, "'m" mark m, etc.
Useful when exporting folded text, e.g., to HTML.

Can also be used as a [method](#method):
```
GetLnum()->foldtextresult()

```

### <a id="fullcommand()" class="section-title" href="#fullcommand()">fullcommand({name})</a>
Get the full command name from a short abbreviated command
name; see [20.2](#20.2) for details on command abbreviations.

The string argument {name} may start with a `:` and can
include a [range], these are skipped and not returned.
Returns an empty string if a command doesn't exist or if it's
ambiguous (for user-defined commands).

For example `fullcommand('s')`, `fullcommand('sub')`,
`fullcommand(':%substitute')` all return "substitute".

Can also be used as a [method](#method):
```
GetName()->fullcommand()

```

### <a id="funcref()" class="section-title" href="#funcref()">Note:</a>
funcref({name} [, {arglist}] [, {dict}])
Just like [function()](#function()), but the returned Funcref will lookup
the function by reference, not by name.  This matters when the
function {name} is redefined later.

Unlike [function()](#function()), {name} must be an existing user function.
It only works for an autoloaded function if it has already
been loaded (to avoid mistakenly loading the autoload script
when only intending to use the function name, use [function()](#function())
instead). {name} cannot be a builtin function.
Returns 0 on error.

Can also be used as a [method](#method):
```
GetFuncname()->funcref([arg])

```

### <a id="function() partial E700 E922 E923" class="section-title" href="#function() partial E700 E922 E923">Note:</a>
function({name} [, {arglist}] [, {dict}])
Return a [Funcref](#Funcref) variable that refers to function {name}.
{name} can be the name of a user defined function or an
internal function.

{name} can also be a Funcref or a partial. When it is a
partial the dict stored in it will be used and the {dict}
argument is not allowed. E.g.:
```
let FuncWithArg = function(dict.Func, [arg])
let Broken = function(dict.Func, [arg], dict)

```

When using the Funcref the function will be found by {name},
also when it was redefined later. Use [funcref()](#funcref()) to keep the
same function.

When {arglist} or {dict} is present this creates a partial.
That means the argument list and/or the dictionary is stored in
the Funcref and will be used when the Funcref is called.

The arguments are passed to the function in front of other
arguments, but after any argument from [method](#method).  Example:
```
func Callback(arg1, arg2, name)
"...
let Partial = function('Callback', ['one', 'two'])
"...
call Partial('name')

```
		Invokes the function as with:
```
call Callback('one', 'two', 'name')


```
		With a [method](#method):
```
func Callback(one, two, three)
"...
let Partial = function('Callback', ['two'])
"...
eval 'one'->Partial('three')

```
		Invokes the function as with:
```
call Callback('one', 'two', 'three')


```
		The function() call can be nested to add more arguments to the
Funcref.  The extra arguments are appended to the list of
arguments.  Example:
```
func Callback(arg1, arg2, name)
"...
let Func = function('Callback', ['one'])
let Func2 = function(Func, ['two'])
"...
call Func2('name')

```
		Invokes the function as with:
```
call Callback('one', 'two', 'name')


```
		The Dictionary is only useful when calling a "dict" function.
In that case the {dict} is passed in as "self". Example:
```
function Callback() dict
echo "called for " .. self.name
endfunction
"...
let context = {"name": "example"}
let Func = function('Callback', context)
"...
call Func()	" will echo: called for example

```
		The use of function() is not needed when there are no extra
arguments, these two are equivalent, if Callback() is defined
as context.Callback():
```
let Func = function('Callback', context)
let Func = context.Callback


```
		The argument list and the Dictionary can be combined:
```
function Callback(arg1, count) dict
"...
let context = {"name": "example"}
let Func = function('Callback', ['one'], context)
"...
call Func(500)

```
		Invokes the function as with:
```
call context.Callback('one', 500)

```

Returns 0 on error.

Can also be used as a [method](#method):
```
GetFuncname()->function([arg])

### <a id="garbagecollect()" class="section-title" href="#garbagecollect()">garbagecollect([{atexit}])</a>
Cleanup unused [Lists| and |Dictionaries](#Lists| and |Dictionaries) that have circular
references.

There is hardly ever a need to invoke this function, as it is
automatically done when Vim runs out of memory or is waiting
for the user to press a key after 'updatetime'.  Items without
circular references are always freed when they become unused.
This is useful if you have deleted a very big [List](#List) and/or
[Dictionary](#Dictionary) with circular references in a script that runs
for a long time.

When the optional {atexit} argument is one, garbage
collection will also be done when exiting Vim, if it wasn't
done before.  This is useful when checking for memory leaks.

The garbage collection is not done immediately but only when
it's safe to perform.  This is when waiting for the user to
type a character.

### <a id="get()" class="section-title" href="#get()">get({list}, {idx} [, {default}])</a>
Get item {idx} from [List](#List) {list}.  When this item is not
available return {default}.  Return zero when {default} is
omitted.
Can also be used as a [method](#method):
```
mylist->get(idx)
get({blob}, {idx} [, {default}])
Get byte {idx} from [Blob](#Blob) {blob}.  When this byte is not
available return {default}.  Return -1 when {default} is
omitted.
get({dict}, {key} [, {default}])
Get item with key {key} from [Dictionary](#Dictionary) {dict}.  When this
item is not available return {default}.  Return zero when
{default} is omitted.  Useful example:
```
let val = get(g:, 'var_name', 'default')

```
		This gets the value of g:var_name if it exists, and uses
"default" when it does not exist.
get({func}, {what})
Get item {what} from Funcref {func}.  Possible values for
{what} are:
"name"	The function name
"func"	The function
"dict"	The dictionary
"args"	The list with arguments
Returns zero on error.

### <a id="getbufinfo()" class="section-title" href="#getbufinfo()">Note:</a>
getbufinfo([{buf}])
getbufinfo([{dict}])
Get information about buffers as a List of Dictionaries.

Without an argument information about all the buffers is
returned.

When the argument is a [Dictionary](#Dictionary) only the buffers matching
the specified criteria are returned.  The following keys can
be specified in {dict}:
buflisted	include only listed buffers.
bufloaded	include only loaded buffers.
bufmodified	include only modified buffers.

Otherwise, {buf} specifies a particular buffer to return
information for.  For the use of {buf}, see [bufname()](#bufname())
above.  If the buffer is found the returned List has one item.
Otherwise the result is an empty list.

Each returned List item is a dictionary with the following
entries:
bufnr		Buffer number.
changed		TRUE if the buffer is modified.
changedtick	Number of changes made to the buffer.
hidden		TRUE if the buffer is hidden.
lastused	Timestamp in seconds, like
[localtime()](#localtime()), when the buffer was
last used.
listed		TRUE if the buffer is listed.
lnum		Line number used for the buffer when
opened in the current window.
Only valid if the buffer has been
displayed in the window in the past.
If you want the line number of the
last known cursor position in a given
window, use [line()](#line()):
```
:echo line('.', {winid})

```

linecount	Number of lines in the buffer (only
valid when loaded)
loaded		TRUE if the buffer is loaded.
name		Full path to the file in the buffer.
signs		List of signs placed in the buffer.
Each list item is a dictionary with
the following fields:
id	  sign identifier
lnum  line number
name  sign name
variables	A reference to the dictionary with
buffer-local variables.
windows		List of [window-ID](#window-ID)s that display this
buffer

Examples:
```
for buf in getbufinfo()
echo buf.name
endfor
for buf in getbufinfo({'buflisted':1})
if buf.changed
....
endif
endfor

```

To get buffer-local options use:
```
getbufvar({bufnr}, '&option_name')

```

Can also be used as a [method](#method):
```
GetBufnr()->getbufinfo()

```

### <a id="getbufline()" class="section-title" href="#getbufline()">Note:</a>
getbufline({buf}, {lnum} [, {end}])
Return a [List](#List) with the lines starting from {lnum} to {end}
(inclusive) in the buffer {buf}.  If {end} is omitted, a
[List](#List) with only the line {lnum} is returned.

For the use of {buf}, see [bufname()](#bufname()) above.

For {lnum} and {end} "$" can be used for the last line of the
buffer.  Otherwise a number must be used.

When {lnum} is smaller than 1 or bigger than the number of
lines in the buffer, an empty [List](#List) is returned.

When {end} is greater than the number of lines in the buffer,
it is treated as {end} is set to the number of lines in the
buffer.  When {end} is before {lnum} an empty [List](#List) is
returned.

This function works only for loaded buffers.  For unloaded and
non-existing buffers, an empty [List](#List) is returned.

Example:
```
:let lines = getbufline(bufnr("myfile"), 1, "$")


```
		Can also be used as a [method](#method):
```
GetBufnr()->getbufline(lnum)

### <a id="getbufvar()" class="section-title" href="#getbufvar()">getbufvar({buf}, {varname} [, {def}])</a>
The result is the value of option or local buffer variable
{varname} in buffer {buf}.  Note that the name without "b:"
must be used.
The {varname} argument is a string.
When {varname} is empty returns a [Dictionary](#Dictionary) with all the
buffer-local variables.
When {varname} is equal to "&" returns a [Dictionary](#Dictionary) with all
the buffer-local options.
Otherwise, when {varname} starts with "&" returns the value of
a buffer-local option.
This also works for a global or buffer-local option, but it
doesn't work for a global variable, window-local variable or
window-local option.
For the use of {buf}, see [bufname()](#bufname()) above.
When the buffer or variable doesn't exist {def} or an empty
string is returned, there is no error message.
Examples:
```
:let bufmodified = getbufvar(1, "&mod")
:echo "todo myvar = " .. getbufvar("todo", "myvar")


```
		Can also be used as a [method](#method):
```
GetBufnr()->getbufvar(varname)

```

### <a id="getchangelist()" class="section-title" href="#getchangelist()">getchangelist([{buf}])</a>
Returns the [changelist](#changelist) for the buffer {buf}. For the use
of {buf}, see [bufname()](#bufname()) above. If buffer {buf} doesn't
exist, an empty list is returned.

The returned list contains two entries: a list with the change
locations and the current position in the list.  Each
entry in the change list is a dictionary with the following
entries:
col		column number
coladd		column offset for 'virtualedit'
lnum		line number
If buffer {buf} is the current buffer, then the current
position refers to the position in the list. For other
buffers, it is set to the length of the list.

Can also be used as a [method](#method):
```
GetBufnr()->getchangelist()

### <a id="getchar()" class="section-title" href="#getchar()">getchar([expr])</a>
Get a single character from the user or input stream.
If [expr] is omitted, wait until a character is available.
If [expr] is 0, only get a character when one is available.
Return zero otherwise.
If [expr] is 1, only check if a character is available, it is
not consumed.  Return zero if no character available.
If you prefer always getting a string use [getcharstr()](#getcharstr()).

Without [expr] and when [expr] is 0 a whole character or
special key is returned.  If it is a single character, the
result is a Number.  Use [nr2char()](#nr2char()) to convert it to a String.
Otherwise a String is returned with the encoded character.
For a special key it's a String with a sequence of bytes
starting with 0x80 (decimal: 128).  This is the same value as
the String "\<Key>", e.g., "\<Left>".  The returned value is
also a String when a modifier (shift, control, alt) was used
that is not included in the character.

When [expr] is 0 and Esc is typed, there will be a short delay
while Vim waits to see if this is the start of an escape
sequence.

When [expr] is 1 only the first byte is returned.  For a
one-byte character it is the character itself as a number.
Use nr2char() to convert it to a String.

Use getcharmod() to obtain any additional modifiers.

When the user clicks a mouse button, the mouse event will be
returned.  The position can then be found in [v:mouse_col](#v:mouse_col),
[v:mouse_lnum|, |v:mouse_winid| and |v:mouse_win](#v:mouse_lnum|, |v:mouse_winid| and |v:mouse_win).
[getmousepos()](#getmousepos()) can also be used.  Mouse move events will be
ignored.
This example positions the mouse as it would normally happen:
```
let c = getchar()
if c == "\<LeftMouse>" && v:mouse_win > 0
exe v:mouse_win .. "wincmd w"
exe v:mouse_lnum
exe "normal " .. v:mouse_col .. "|"
endif

```

There is no prompt, you will somehow have to make clear to the
user that a character has to be typed.  The screen is not
redrawn, e.g. when resizing the window.

There is no mapping for the character.
Key codes are replaced, thus when the user presses the <Del>
key you get the code for the <Del> key, not the raw character
sequence.  Examples:
```
getchar() == "\<Del>"
getchar() == "\<S-Left>"

```
		This example redefines "f" to ignore case:
```
:nmap f :call FindChar()<CR>
:function FindChar()
:  let c = nr2char(getchar())
:  while col('.') < col('$') - 1
:    normal l
:    if getline('.')[col('.') - 1] ==? c
:      break
:    endif
:  endwhile
:endfunction

```

### <a id="getcharmod()" class="section-title" href="#getcharmod()">getcharmod()</a>
The result is a Number which is the state of the modifiers for
the last obtained character with getchar() or in another way.
These values are added together:
2	shift
4	control
8	alt (meta)
16	meta (when it's different from ALT)
32	mouse double click
64	mouse triple click
96	mouse quadruple click (== 32 + 64)
128	command (Macintosh only)
Only the modifiers that have not been included in the
character itself are obtained.  Thus Shift-a results in "A"
without a modifier.  Returns 0 if no modifiers are used.

### <a id="getcharpos()" class="section-title" href="#getcharpos()">Note:</a>
getcharpos({expr})
Get the position for String {expr}. Same as [getpos()](#getpos()) but the
column number in the returned List is a character index
instead of a byte index.

Example:
With the cursor on '세' in line 5 with text "여보세요":
```
getcharpos('.')		returns [0, 5, 3, 0]
getpos('.')		returns [0, 5, 7, 0]

```

Can also be used as a [method](#method):
```
GetMark()->getcharpos()

### <a id="getcharsearch()" class="section-title" href="#getcharsearch()">getcharsearch()</a>
Return the current character search information as a {dict}
with the following entries:

char	character previously used for a character
search ([t|, |f|, |T|, or |F](#t|, |f|, |T|, or |F)); empty string
if no character search has been performed
forward	direction of character search; 1 for forward,
0 for backward
until	type of character search; 1 for a [t| or |T](#t| or |T)
character search, 0 for an [f| or |F](#f| or |F)
character search

This can be useful to always have [;| and |,](#;| and |,) search
forward/backward regardless of the direction of the previous
character search:
```
:nnoremap <expr> ; getcharsearch().forward ? ';' : ','
:nnoremap <expr> , getcharsearch().forward ? ',' : ';'

```
		Also see [setcharsearch()](#setcharsearch()).


### <a id="getcharstr()" class="section-title" href="#getcharstr()">getcharstr([expr])</a>
Get a single character from the user or input stream as a
string.
If [expr] is omitted, wait until a character is available.
If [expr] is 0 or false, only get a character when one is
available.  Return an empty string otherwise.
If [expr] is 1 or true, only check if a character is
available, it is not consumed.  Return an empty string
if no character is available.
Otherwise this works like [getchar()](#getchar()), except that a number
result is converted to a string.

### <a id="getcmdcompltype()" class="section-title" href="#getcmdcompltype()">getcmdcompltype()</a>
Return the type of the current command-line completion.
Only works when the command line is being edited, thus
requires use of [c_CTRL-\_e| or |c_CTRL-R_=](#c_CTRL-\_e| or |c_CTRL-R_=).
See [:command-completion](#:command-completion) for the return string.
Also see [getcmdtype()|, |setcmdpos()|, |getcmdline()](#getcmdtype()|, |setcmdpos()|, |getcmdline()) and
[setcmdline()](#setcmdline()).
Returns an empty string when completion is not defined.

### <a id="getcmdline()" class="section-title" href="#getcmdline()">getcmdline()</a>
Return the current command-line.  Only works when the command
line is being edited, thus requires use of [c_CTRL-\_e](#c_CTRL-\_e) or
[c_CTRL-R_=](#c_CTRL-R_=).
Example:
```
:cmap <F7> <C-\>eescape(getcmdline(), ' \')<CR>

```
		Also see [getcmdtype()|, |getcmdpos()|, |setcmdpos()](#getcmdtype()|, |getcmdpos()|, |setcmdpos()) and
[setcmdline()](#setcmdline()).
Returns an empty string when entering a password or using
[inputsecret()](#inputsecret()).

### <a id="getcmdpos()" class="section-title" href="#getcmdpos()">getcmdpos()</a>
Return the position of the cursor in the command line as a
byte count.  The first column is 1.
Only works when editing the command line, thus requires use of
[c_CTRL-\_e| or |c_CTRL-R_=](#c_CTRL-\_e| or |c_CTRL-R_=) or an expression mapping.
Returns 0 otherwise.
Also see [getcmdtype()|, |setcmdpos()|, |getcmdline()](#getcmdtype()|, |setcmdpos()|, |getcmdline()) and
[setcmdline()](#setcmdline()).

### <a id="getcmdscreenpos()" class="section-title" href="#getcmdscreenpos()">getcmdscreenpos()</a>
Return the screen position of the cursor in the command line
as a byte count.  The first column is 1.
Instead of [getcmdpos()](#getcmdpos()), it adds the prompt position.
Only works when editing the command line, thus requires use of
[c_CTRL-\_e| or |c_CTRL-R_=](#c_CTRL-\_e| or |c_CTRL-R_=) or an expression mapping.
Returns 0 otherwise.
Also see [getcmdpos()|, |setcmdpos()|, |getcmdline()](#getcmdpos()|, |setcmdpos()|, |getcmdline()) and
[setcmdline()](#setcmdline()).

### <a id="getcmdtype()" class="section-title" href="#getcmdtype()">getcmdtype()</a>
Return the current command-line type. Possible return values
are:
:	normal Ex command
>	debug mode command [debug-mode](#debug-mode)
/	forward search command
?	backward search command
@	[input()](#input()) command
-	[:insert| or |:append](#:insert| or |:append) command
=	[i_CTRL-R_=](#i_CTRL-R_=)
Only works when editing the command line, thus requires use of
[c_CTRL-\_e| or |c_CTRL-R_=](#c_CTRL-\_e| or |c_CTRL-R_=) or an expression mapping.
Returns an empty string otherwise.
Also see [getcmdpos()|, |setcmdpos()| and |getcmdline()](#getcmdpos()|, |setcmdpos()| and |getcmdline()).

### <a id="getcmdwintype()" class="section-title" href="#getcmdwintype()">getcmdwintype()</a>
Return the current [command-line-window](#command-line-window) type. Possible return
values are the same as [getcmdtype()](#getcmdtype()). Returns an empty string
when not in the command-line window.

### <a id="getcompletion()" class="section-title" href="#getcompletion()">getcompletion({pat}, {type} [, {filtered}])</a>
Return a list of command-line completion matches. The String
{type} argument specifies what for.  The following completion
types are supported:

arglist		file names in argument list
augroup		autocmd groups
buffer		buffer names
behave		:behave suboptions
cmdline		[cmdline-completion](#cmdline-completion) result
color		color schemes
command		Ex command
compiler	compilers
diff_buffer     [:diffget| and |:diffput](#:diffget| and |:diffput) completion
dir		directory names
environment	environment variable names
event		autocommand events
expression	Vim expression
file		file and directory names
file_in_path	file and directory names in ['path'](#'path')
filetype	filetype names ['filetype'](#'filetype')
function	function name
help		help subjects
highlight	highlight groups
history		:history suboptions
locale		locale names (as output of locale -a)
mapclear	buffer argument
mapping		mapping name
menu		menus
messages	[:messages](#:messages) suboptions
option		options
packadd		optional package [pack-add](#pack-add) names
shellcmd	Shell command
sign		[:sign](#:sign) suboptions
syntax		syntax file names ['syntax'](#'syntax')
syntime		[:syntime](#:syntime) suboptions
tag		tags
tag_listfiles	tags, file names
user		user names
var		user variables

If {pat} is an empty string, then all the matches are
returned.  Otherwise only items matching {pat} are returned.
See [wildcards](#wildcards) for the use of special characters in {pat}.

If the optional {filtered} flag is set to 1, then 'wildignore'
is applied to filter the results.  Otherwise all the matches
are returned. The 'wildignorecase' option always applies.

If {type} is "cmdline", then the [cmdline-completion](#cmdline-completion) result is
returned.  For example, to complete the possible values after
a ":call" command:
```
echo getcompletion('call ', 'cmdline')

```

If there are no matches, an empty list is returned.  An
invalid value for {type} produces an error.

Can also be used as a [method](#method):
```
GetPattern()->getcompletion('color')

```

### <a id="getcurpos()" class="section-title" href="#getcurpos()">Note:</a>
getcurpos([{winid}])
Get the position of the cursor.  This is like getpos('.'), but
includes an extra "curswant" in the list:
[0, lnum, col, off, curswant] ~
The "curswant" number is the preferred column when moving the
cursor vertically.  Also see [getcursorcharpos()](#getcursorcharpos()) and
[getpos()](#getpos()).
The first "bufnum" item is always zero. The byte position of
the cursor is returned in "col". To get the character
position, use [getcursorcharpos()](#getcursorcharpos()).

The optional {winid} argument can specify the window.  It can
be the window number or the [window-ID](#window-ID).  The last known
cursor position is returned, this may be invalid for the
current value of the buffer if it is not the current window.
If {winid} is invalid a list with zeroes is returned.

This can be used to save and restore the cursor position:
```
let save_cursor = getcurpos()
MoveTheCursorAround
call setpos('.', save_cursor)

```
		Note that this only works within the window.  See
[winrestview()](#winrestview()) for restoring more state.

Can also be used as a [method](#method):
```
GetWinid()->getcurpos()

```

### <a id="getcursorcharpos()" class="section-title" href="#getcursorcharpos()">Note:</a>
getcursorcharpos([{winid}])
Same as [getcurpos()](#getcurpos()) but the column number in the returned
List is a character index instead of a byte index.

Example:
With the cursor on '보' in line 3 with text "여보세요":
```
getcursorcharpos()	returns [0, 3, 2, 0, 3]
getcurpos()		returns [0, 3, 4, 0, 3]

```

Can also be used as a [method](#method):
```
GetWinid()->getcursorcharpos()

### <a id="getcwd()" class="section-title" href="#getcwd()">getcwd([{winnr} [, {tabnr}]])</a>
With no arguments, returns the name of the effective
[current-directory](#current-directory). With {winnr} or {tabnr} the working
directory of that scope is returned, and 'autochdir' is
ignored.
Tabs and windows are identified by their respective numbers,
0 means current tab or window. Missing tab number implies 0.
Thus the following are equivalent:
```
getcwd(0)
getcwd(0, 0)

```
		If {winnr} is -1 it is ignored, only the tab is resolved.
{winnr} can be the window number or the [window-ID](#window-ID).
If both {winnr} and {tabnr} are -1 the global working
directory is returned.
Throw error if the arguments are invalid. [E5000| |E5001| |E5002](#E5000| |E5001| |E5002)

Can also be used as a [method](#method):
```
GetWinnr()->getcwd()

### <a id="getenv()" class="section-title" href="#getenv()">getenv({name})</a>
Return the value of environment variable {name}.  The {name}
argument is a string, without a leading '$'.  Example:
```
myHome = getenv('HOME')


```
		When the variable does not exist [v:null](#v:null) is returned.  That
is different from a variable set to an empty string.
See also [expr-env](#expr-env).

Can also be used as a [method](#method):
```
GetVarname()->getenv()

### <a id="getfontname()" class="section-title" href="#getfontname()">getfontname([{name}])</a>
Without an argument returns the name of the normal font being
used.  Like what is used for the Normal highlight group
[hl-Normal](#hl-Normal).
With an argument a check is done whether String {name} is a
valid font name.  If not then an empty string is returned.
Otherwise the actual font name is returned, or {name} if the
GUI does not support obtaining the real name.
Only works when the GUI is running, thus not in your vimrc or
gvimrc file.  Use the [GUIEnter](#GUIEnter) autocommand to use this
function just after the GUI has started.

### <a id="getfperm()" class="section-title" href="#getfperm()">getfperm({fname})</a>
The result is a String, which is the read, write, and execute
permissions of the given file {fname}.
If {fname} does not exist or its directory cannot be read, an
empty string is returned.
The result is of the form "rwxrwxrwx", where each group of
"rwx" flags represent, in turn, the permissions of the owner
of the file, the group the file belongs to, and other users.
If a user does not have a given permission the flag for this
is replaced with the string "-".  Examples:
```
:echo getfperm("/etc/passwd")
:echo getfperm(expand("~/.config/nvim/init.vim"))

```
		This will hopefully (from a security point of view) display
the string "rw-r--r--" or even "rw-------".

Can also be used as a [method](#method):
```
GetFilename()->getfperm()

```

For setting permissions use [setfperm()](#setfperm()).

### <a id="getfsize()" class="section-title" href="#getfsize()">getfsize({fname})</a>
The result is a Number, which is the size in bytes of the
given file {fname}.
If {fname} is a directory, 0 is returned.
If the file {fname} can't be found, -1 is returned.
If the size of {fname} is too big to fit in a Number then -2
is returned.

Can also be used as a [method](#method):
```
GetFilename()->getfsize()

### <a id="getftime()" class="section-title" href="#getftime()">getftime({fname})</a>
The result is a Number, which is the last modification time of
the given file {fname}.  The value is measured as seconds
since 1st Jan 1970, and may be passed to strftime().  See also
[localtime()| and |strftime()](#localtime()| and |strftime()).
If the file {fname} can't be found -1 is returned.

Can also be used as a [method](#method):
```
GetFilename()->getftime()

### <a id="getftype()" class="section-title" href="#getftype()">getftype({fname})</a>
The result is a String, which is a description of the kind of
file of the given file {fname}.
If {fname} does not exist an empty string is returned.
Here is a table over different kinds of files and their
results:
Normal file		"file"
Directory		"dir"
Symbolic link		"link"
Block device		"bdev"
Character device	"cdev"
Socket			"socket"
FIFO			"fifo"
All other		"other"
Example:
```
getftype("/home")

```
		Note that a type such as "link" will only be returned on
systems that support it.  On some systems only "dir" and
"file" are returned.

Can also be used as a [method](#method):
```
GetFilename()->getftype()

### <a id="getjumplist()" class="section-title" href="#getjumplist()">getjumplist([{winnr} [, {tabnr}]])</a>
Returns the [jumplist](#jumplist) for the specified window.

Without arguments use the current window.
With {winnr} only use this window in the current tab page.
{winnr} can also be a [window-ID](#window-ID).
With {winnr} and {tabnr} use the window in the specified tab
page.  If {winnr} or {tabnr} is invalid, an empty list is
returned.

The returned list contains two entries: a list with the jump
locations and the last used jump position number in the list.
Each entry in the jump location list is a dictionary with
the following entries:
bufnr		buffer number
col		column number
coladd		column offset for 'virtualedit'
filename	filename if available
lnum		line number

Can also be used as a [method](#method):
```
GetWinnr()->getjumplist()

### <a id="getline()" class="section-title" href="#getline()"><</a>
getline({lnum} [, {end}])
Without {end} the result is a String, which is line {lnum}
from the current buffer.  Example:
```
getline(1)

```
		When {lnum} is a String that doesn't start with a
digit, [line()](#line()) is called to translate the String into a Number.
To get the line under the cursor:
```
getline(".")

```
		When {lnum} is a number smaller than 1 or bigger than the
number of lines in the buffer, an empty string is returned.

When {end} is given the result is a [List](#List) where each item is
a line from the current buffer in the range {lnum} to {end},
including line {end}.
{end} is used in the same way as {lnum}.
Non-existing lines are silently omitted.
When {end} is before {lnum} an empty [List](#List) is returned.
Example:
```
:let start = line('.')
:let end = search("^$") - 1
:let lines = getline(start, end)


```
		Can also be used as a [method](#method):
```
ComputeLnum()->getline()


```
		To get lines from another buffer see [getbufline()](#getbufline())

### <a id="getloclist()" class="section-title" href="#getloclist()">getloclist({nr} [, {what}])</a>
Returns a [List](#List) with all the entries in the location list for
window {nr}.  {nr} can be the window number or the [window-ID](#window-ID).
When {nr} is zero the current window is used.

For a location list window, the displayed location list is
returned.  For an invalid window number {nr}, an empty list is
returned. Otherwise, same as [getqflist()](#getqflist()).

If the optional {what} dictionary argument is supplied, then
returns the items listed in {what} as a dictionary. Refer to
[getqflist()](#getqflist()) for the supported items in {what}.

In addition to the items supported by [getqflist()](#getqflist()) in {what},
the following item is supported by [getloclist()](#getloclist()):

filewinid	id of the window used to display files
from the location list. This field is
applicable only when called from a
location list window. See
[location-list-file-window](#location-list-file-window) for more
details.

Returns a [Dictionary](#Dictionary) with default values if there is no
location list for the window {nr}.
Returns an empty Dictionary if window {nr} does not exist.

Examples (See also [getqflist-examples](#getqflist-examples)):
```
:echo getloclist(3, {'all': 0})
:echo getloclist(5, {'filewinid': 0})


### <a id="getmarklist()" class="section-title" href="#getmarklist()">getmarklist([{buf}])</a>
Without the {buf} argument returns a [List](#List) with information
about all the global marks. [mark](#mark)

If the optional {buf} argument is specified, returns the
local marks defined in buffer {buf}.  For the use of {buf},
see [bufname()](#bufname()).  If {buf} is invalid, an empty list is
returned.

Each item in the returned List is a [Dict](#Dict) with the following:
mark   name of the mark prefixed by "'"
pos	   a [List](#List) with the position of the mark:
[bufnum, lnum, col, off]
Refer to [getpos()](#getpos()) for more information.
file   file name

Refer to [getpos()](#getpos()) for getting information about a specific
mark.

Can also be used as a [method](#method):
```
GetBufnr()->getmarklist()

### <a id="getmatches()" class="section-title" href="#getmatches()">getmatches([{win}])</a>
Returns a [List](#List) with all matches previously defined for the
current window by [matchadd()| and the |:match](#matchadd()| and the |:match) commands.
[getmatches()| is useful in combination with |setmatches()](#getmatches()| is useful in combination with |setmatches()),
as [setmatches()](#setmatches()) can restore a list of matches saved by
[getmatches()](#getmatches()).
If {win} is specified, use the window with this number or
window ID instead of the current window.  If {win} is invalid,
an empty list is returned.
Example:
```
:echo getmatches()

```
			[{"group": "MyGroup1", "pattern": "TODO",
"priority": 10, "id": 1}, {"group": "MyGroup2",
"pattern": "FIXME", "priority": 10, "id": 2}]
```
:let m = getmatches()
:call clearmatches()
:echo getmatches()

```
			[]
```
:call setmatches(m)
:echo getmatches()

```
			[{"group": "MyGroup1", "pattern": "TODO",
"priority": 10, "id": 1}, {"group": "MyGroup2",
"pattern": "FIXME", "priority": 10, "id": 2}]
```
:unlet m

```

### <a id="getmousepos()" class="section-title" href="#getmousepos()">getmousepos()</a>
Returns a Dictionary with the last known position of the
mouse.  This can be used in a mapping for a mouse click.  The
items are:
screenrow	screen row
screencol	screen column
winid		Window ID of the click
winrow		row inside "winid"
wincol		column inside "winid"
line		text line inside "winid"
column		text column inside "winid"
All numbers are 1-based.

If not over a window, e.g. when in the command line, then only
"screenrow" and "screencol" are valid, the others are zero.

When on the status line below a window or the vertical
separator right of a window, the "line" and "column" values
are zero.

When the position is after the text then "column" is the
length of the text in bytes plus one.

If the mouse is over a focusable floating window then that
window is used.

When using [getchar()| the Vim variables |v:mouse_lnum](#getchar()| the Vim variables |v:mouse_lnum),
[v:mouse_col| and |v:mouse_winid](#v:mouse_col| and |v:mouse_winid) also provide these values.

### <a id="getpid()" class="section-title" href="#getpid()">Note:</a>
getpid()	Return a Number which is the process ID of the Vim process.
This is a unique number, until Vim exits.

### <a id="getpos()" class="section-title" href="#getpos()">Note:</a>
getpos({expr})	Get the position for String {expr}.  For possible values of
{expr} see [line()](#line()).  For getting the cursor position see
[getcurpos()](#getcurpos()).
The result is a [List](#List) with four numbers:
[bufnum, lnum, col, off]
"bufnum" is zero, unless a mark like '0 or 'A is used, then it
is the buffer number of the mark.
"lnum" and "col" are the position in the buffer.  The first
column is 1.
The "off" number is zero, unless 'virtualedit' is used.  Then
it is the offset in screen columns from the start of the
character.  E.g., a position within a <Tab> or after the last
character.
Note that for '< and '> Visual mode matters: when it is "V"
(visual line mode) the column of '< is zero and the column of
'> is a large number.
The column number in the returned List is the byte position
within the line. To get the character position in the line,
use [getcharpos()](#getcharpos()).
The column number can be very large, e.g. 2147483647, in which
case it means "after the end of the line".
If {expr} is invalid, returns a list with all zeros.
This can be used to save and restore the position of a mark:
```
let save_a_mark = getpos("'a")
...
call setpos("'a", save_a_mark)

```
		Also see [getcharpos()|, |getcurpos()| and |setpos()](#getcharpos()|, |getcurpos()| and |setpos()).

Can also be used as a [method](#method):
```
GetMark()->getpos()

### <a id="getqflist()" class="section-title" href="#getqflist()">getqflist([{what}])</a>
Returns a [List](#List) with all the current quickfix errors.  Each
list item is a dictionary with these entries:
bufnr	number of buffer that has the file name, use
bufname() to get the name
module	module name
lnum	line number in the buffer (first line is 1)
end_lnum
end of line number if the item is multiline
col	column number (first column is 1)
end_col	end of column number if the item has range
vcol	[TRUE](#TRUE): "col" is visual column
[FALSE](#FALSE): "col" is byte index
nr	error number
pattern	search pattern used to locate the error
text	description of the error
type	type of the error, 'E', '1', etc.
valid	[TRUE](#TRUE): recognized error message

When there is no error list or it's empty, an empty list is
returned. Quickfix list entries with a non-existing buffer
number are returned with "bufnr" set to zero (Note: some
functions accept buffer number zero for the alternate buffer,
you may need to explicitly check for zero).

Useful application: Find pattern matches in multiple files and
do something with them:
```
### <a id=":vimgrep /theword/jg .c" class="section-title" href="#:vimgrep /theword/jg .c">Note:</a>
:for d in getqflist()
:   echo bufname(d.bufnr) ':' d.lnum '=' d.text
:endfor

```

If the optional {what} dictionary argument is supplied, then
returns only the items listed in {what} as a dictionary. The
following string items are supported in {what}:
changedtick	get the total number of changes made
to the list [quickfix-changedtick](#quickfix-changedtick)
context	get the [quickfix-context](#quickfix-context)
efm	errorformat to use when parsing "lines". If
not present, then the 'errorformat' option
value is used.
id	get information for the quickfix list with
[quickfix-ID](#quickfix-ID); zero means the id for the
current list or the list specified by "nr"
idx	get information for the quickfix entry at this
index in the list specified by "id" or "nr".
If set to zero, then uses the current entry.
See [quickfix-index](#quickfix-index)
items	quickfix list entries
lines	parse a list of lines using 'efm' and return
the resulting entries.  Only a [List](#List) type is
accepted.  The current quickfix list is not
modified. See [quickfix-parse](#quickfix-parse).
nr	get information for this quickfix list; zero
means the current quickfix list and "$" means
the last quickfix list
qfbufnr number of the buffer displayed in the quickfix
window. Returns 0 if the quickfix buffer is
not present. See [quickfix-buffer](#quickfix-buffer).
size	number of entries in the quickfix list
title	get the list title [quickfix-title](#quickfix-title)
winid	get the quickfix [window-ID](#window-ID)
all	all of the above quickfix properties
Non-string items in {what} are ignored. To get the value of a
particular item, set it to zero.
If "nr" is not present then the current quickfix list is used.
If both "nr" and a non-zero "id" are specified, then the list
specified by "id" is used.
To get the number of lists in the quickfix stack, set "nr" to
"$" in {what}. The "nr" value in the returned dictionary
contains the quickfix stack size.
When "lines" is specified, all the other items except "efm"
are ignored.  The returned dictionary contains the entry
"items" with the list of entries.

The returned dictionary contains the following entries:
changedtick	total number of changes made to the
list [quickfix-changedtick](#quickfix-changedtick)
context	quickfix list context. See [quickfix-context](#quickfix-context)
If not present, set to "".
id	quickfix list ID [quickfix-ID](#quickfix-ID). If not
present, set to 0.
idx	index of the quickfix entry in the list. If not
present, set to 0.
items	quickfix list entries. If not present, set to
an empty list.
nr	quickfix list number. If not present, set to 0
qfbufnr	number of the buffer displayed in the quickfix
window. If not present, set to 0.
size	number of entries in the quickfix list. If not
present, set to 0.
title	quickfix list title text. If not present, set
to "".
winid	quickfix [window-ID](#window-ID). If not present, set to 0

Examples (See also [getqflist-examples](#getqflist-examples)):
```
:echo getqflist({'all': 1})
:echo getqflist({'nr': 2, 'title': 1})
:echo getqflist({'lines' : ["F1:10:L10"]})

```

### <a id="getreg()" class="section-title" href="#getreg()">getreg([{regname} [, 1 [, {list}]]])</a>
The result is a String, which is the contents of register
{regname}.  Example:
```
### <a id=":let cliptext = getreg('')" class="section-title" href="#:let cliptext = getreg('')">Note:</a>

```
		When register {regname} was not set the result is an empty
string.
The {regname} argument must be a string.

getreg('=') returns the last evaluated value of the expression
register.  (For use in maps.)
getreg('=', 1) returns the expression itself, so that it can
be restored with [setreg()](#setreg()).  For other registers the extra
argument is ignored, thus you can always give it.

If {list} is present and [TRUE](#TRUE), the result type is changed
to [List](#List). Each list item is one text line. Use it if you care
about zero bytes possibly present inside register: without
third argument both NLs and zero bytes are represented as NLs
(see [NL-used-for-Nul](#NL-used-for-Nul)).
When the register was not set an empty list is returned.

If {regname} is not specified, [v:register](#v:register) is used.

Can also be used as a [method](#method):
```
GetRegname()->getreg()

### <a id="getreginfo()" class="section-title" href="#getreginfo()">getreginfo([{regname}])</a>
Returns detailed information about register {regname} as a
Dictionary with the following entries:
regcontents	List of lines contained in register
{regname}, like
getreg({regname}, 1, 1).
regtype		the type of register {regname}, as in
[getregtype()](#getregtype()).
isunnamed	Boolean flag, v:true if this register
is currently pointed to by the unnamed
register.
points_to	for the unnamed register, gives the
single letter name of the register
currently pointed to (see [quotequote](#quotequote)).
For example, after deleting a line
with `dd`, this field will be "1",
which is the register that got the
deleted text.

The {regname} argument is a string.  If {regname} is invalid
or not set, an empty Dictionary will be returned.
If {regname} is not specified, [v:register](#v:register) is used.
The returned Dictionary can be passed to [setreg()](#setreg()).

Can also be used as a [method](#method):
```
GetRegname()->getreginfo()

### <a id="getregtype()" class="section-title" href="#getregtype()">getregtype([{regname}])</a>
The result is a String, which is type of register {regname}.
The value will be one of:
"v"			for [charwise](#charwise) text
"V"			for [linewise](#linewise) text
"<CTRL-V>{width}"	for [blockwise-visual](#blockwise-visual) text
""			for an empty or unknown register

```
CTRL-V> is one character with value 0x16.
The {regname} argument is a string.  If {regname} is not
specified, [v:register](#v:register) is used.

Can also be used as a [method](#method):
```
GetRegname()->getregtype()

### <a id="gettabinfo()" class="section-title" href="#gettabinfo()">gettabinfo([{tabnr}])</a>
If {tabnr} is not specified, then information about all the
tab pages is returned as a [List](#List). Each List item is a
[Dictionary](#Dictionary).  Otherwise, {tabnr} specifies the tab page
number and information about that one is returned.  If the tab
page does not exist an empty List is returned.

Each List item is a [Dictionary](#Dictionary) with the following entries:
tabnr		tab page number.
variables	a reference to the dictionary with
tabpage-local variables
windows		List of [window-ID](#window-ID)s in the tab page.

Can also be used as a [method](#method):
```
GetTabnr()->gettabinfo()

### <a id="gettabvar()" class="section-title" href="#gettabvar()">gettabvar({tabnr}, {varname} [, {def}])</a>
Get the value of a tab-local variable {varname} in tab page
{tabnr}. [t:var](#t:var)
Tabs are numbered starting with one.
The {varname} argument is a string.  When {varname} is empty a
dictionary with all tab-local variables is returned.
Note that the name without "t:" must be used.
When the tab or variable doesn't exist {def} or an empty
string is returned, there is no error message.

Can also be used as a [method](#method):
```
GetTabnr()->gettabvar(varname)

### <a id="gettabwinvar()" class="section-title" href="#gettabwinvar()">gettabwinvar({tabnr}, {winnr}, {varname} [, {def}])</a>
Get the value of window-local variable {varname} in window
{winnr} in tab page {tabnr}.
The {varname} argument is a string.  When {varname} is empty a
dictionary with all window-local variables is returned.
When {varname} is equal to "&" get the values of all
window-local options in a [Dictionary](#Dictionary).
Otherwise, when {varname} starts with "&" get the value of a
window-local option.
Note that {varname} must be the name without "w:".
Tabs are numbered starting with one.  For the current tabpage
use [getwinvar()](#getwinvar()).
{winnr} can be the window number or the [window-ID](#window-ID).
When {winnr} is zero the current window is used.
This also works for a global option, buffer-local option and
window-local option, but it doesn't work for a global variable
or buffer-local variable.
When the tab, window or variable doesn't exist {def} or an
empty string is returned, there is no error message.
Examples:
```
:let list_is_on = gettabwinvar(1, 2, '&list')
:echo "myvar = " .. gettabwinvar(3, 1, 'myvar')

```

To obtain all window-local variables use:
```
gettabwinvar({tabnr}, {winnr}, '&')


```
		Can also be used as a [method](#method):
```
GetTabnr()->gettabwinvar(winnr, varname)

### <a id="gettagstack()" class="section-title" href="#gettagstack()">gettagstack([{winnr}])</a>
The result is a Dict, which is the tag stack of window {winnr}.
{winnr} can be the window number or the [window-ID](#window-ID).
When {winnr} is not specified, the current window is used.
When window {winnr} doesn't exist, an empty Dict is returned.

The returned dictionary contains the following entries:
curidx		Current index in the stack. When at
top of the stack, set to (length + 1).
Index of bottom of the stack is 1.
items		List of items in the stack. Each item
is a dictionary containing the
entries described below.
length		Number of entries in the stack.

Each item in the stack is a dictionary with the following
entries:
bufnr		buffer number of the current jump
from		cursor position before the tag jump.
See [getpos()](#getpos()) for the format of the
returned list.
matchnr		current matching tag number. Used when
multiple matching tags are found for a
name.
tagname		name of the tag

See [tagstack](#tagstack) for more information about the tag stack.

Can also be used as a [method](#method):
```
GetWinnr()->gettagstack()

### <a id="getwininfo()" class="section-title" href="#getwininfo()">getwininfo([{winid}])</a>
Returns information about windows as a [List](#List) with Dictionaries.

If {winid} is given Information about the window with that ID
is returned, as a [List](#List) with one item.  If the window does not
exist the result is an empty list.

Without {winid} information about all the windows in all the
tab pages is returned.

Each List item is a [Dictionary](#Dictionary) with the following entries:
botline		last complete displayed buffer line
bufnr		number of buffer in the window
height		window height (excluding winbar)
loclist		1 if showing a location list
quickfix	1 if quickfix or location list window
terminal	1 if a terminal window
tabnr		tab page number
topline		first displayed buffer line
variables	a reference to the dictionary with
window-local variables
width		window width
winbar		1 if the window has a toolbar, 0
otherwise
wincol		leftmost screen column of the window;
"col" from [win_screenpos()](#win_screenpos())
textoff		number of columns occupied by any
'foldcolumn', 'signcolumn' and line
number in front of the text
winid		[window-ID](#window-ID)
winnr		window number
winrow		topmost screen line of the window;
"row" from [win_screenpos()](#win_screenpos())

Can also be used as a [method](#method):
```
GetWinnr()->getwininfo()

### <a id="getwinpos()" class="section-title" href="#getwinpos()">getwinpos([{timeout}])</a>
The result is a [List](#List) with two numbers, the result of
[getwinposx()| and |getwinposy()](#getwinposx()| and |getwinposy()) combined:
[x-pos, y-pos]
{timeout} can be used to specify how long to wait in msec for
a response from the terminal.  When omitted 100 msec is used.

Use a longer time for a remote terminal.
When using a value less than 10 and no response is received
within that time, a previously reported position is returned,
if available.  This can be used to poll for the position and
do some work in the meantime:
```
while 1
let res = getwinpos(1)
if res[0] >= 0
break
endif
" Do some work here
endwhile

```

Can also be used as a [method](#method):
```
GetTimeout()->getwinpos()

```

### <a id="getwinposx()" class="section-title" href="#getwinposx()">Note:</a>
getwinposx()	The result is a Number, which is the X coordinate in pixels of
the left hand side of the GUI Vim window.  The result will be
-1 if the information is not available.
The value can be used with `:winpos`.

### <a id="getwinposy()" class="section-title" href="#getwinposy()">Note:</a>
getwinposy()	The result is a Number, which is the Y coordinate in pixels of
the top of the GUI Vim window.  The result will be -1 if the
information is not available.
The value can be used with `:winpos`.

### <a id="getwinvar()" class="section-title" href="#getwinvar()">getwinvar({winnr}, {varname} [, {def}])</a>
Like [gettabwinvar()](#gettabwinvar()) for the current tabpage.
Examples:
```
:let list_is_on = getwinvar(2, '&list')
:echo "myvar = " .. getwinvar(1, 'myvar')


```
		Can also be used as a [method](#method):
```
GetWinnr()->getwinvar(varname)

```

### <a id="glob()" class="section-title" href="#glob()">glob({expr} [, {nosuf} [, {list} [, {alllinks}]]])</a>
Expand the file wildcards in {expr}.  See [wildcards](#wildcards) for the
use of special characters.

Unless the optional {nosuf} argument is given and is [TRUE](#TRUE),
the 'suffixes' and 'wildignore' options apply: Names matching
one of the patterns in 'wildignore' will be skipped and
'suffixes' affect the ordering of matches.
'wildignorecase' always applies.

When {list} is present and it is [TRUE| the result is a |List](#TRUE| the result is a |List)
with all matching files. The advantage of using a List is,
you also get filenames containing newlines correctly.
Otherwise the result is a String and when there are several
matches, they are separated by <NL> characters.

If the expansion fails, the result is an empty String or List.

You can also use [readdir()](#readdir()) if you need to do complicated
things, such as limiting the number of matches.

A name for a non-existing file is not included.  A symbolic
link is only included if it points to an existing file.
However, when the {alllinks} argument is present and it is
[TRUE](#TRUE) then all symbolic links are included.

For most systems backticks can be used to get files names from
any external command.  Example:
```
:let tagfiles = glob("`find . -name tags -print`")
:let &tags = substitute(tagfiles, "\n", ",", "g")

```
		The result of the program inside the backticks should be one
item per line.  Spaces inside an item are allowed.

See [expand()](#expand()) for expanding special Vim variables.  See
[system()](#system()) for getting the raw output of an external command.

Can also be used as a [method](#method):
```
GetExpr()->glob()

### <a id="glob2regpat()" class="section-title" href="#glob2regpat()">glob2regpat({string})</a>
Convert a file pattern, as used by glob(), into a search
pattern.  The result can be used to match with a string that
is a file name.  E.g.
```
### <a id="if filename =~ glob2regpat('Make.mak')" class="section-title" href="#if filename =~ glob2regpat('Make.mak')">Note:</a>

```
		This is equivalent to:
```
### <a id="if filename =~ '^Make.\.mak$'" class="section-title" href="#if filename =~ '^Make.\.mak$'">Note:</a>

```
		When {string} is an empty string the result is "^$", match an
empty string.
Note that the result depends on the system.  On MS-Windows
a backslash usually means a path separator.

Can also be used as a [method](#method):
```
GetExpr()->glob2regpat()
### <a id="globpath()" class="section-title" href="#globpath()"><</a>
globpath({path}, {expr} [, {nosuf} [, {list} [, {allinks}]]])
Perform glob() for String {expr} on all directories in {path}
and concatenate the results.  Example:
```
:echo globpath(&rtp, "syntax/c.vim")

```

{path} is a comma-separated list of directory names.  Each
directory name is prepended to {expr} and expanded like with
[glob()](#glob()).  A path separator is inserted when needed.
To add a comma inside a directory name escape it with a
backslash.  Note that on MS-Windows a directory may have a
trailing backslash, remove it if you put a comma after it.
If the expansion fails for one of the directories, there is no
error message.

Unless the optional {nosuf} argument is given and is [TRUE](#TRUE),
the 'suffixes' and 'wildignore' options apply: Names matching
one of the patterns in 'wildignore' will be skipped and
'suffixes' affect the ordering of matches.

When {list} is present and it is [TRUE| the result is a |List](#TRUE| the result is a |List)
with all matching files. The advantage of using a List is, you
also get filenames containing newlines correctly. Otherwise
the result is a String and when there are several matches,
they are separated by <NL> characters.  Example:
```
:echo globpath(&rtp, "syntax/c.vim", 0, 1)

```

{allinks} is used as with [glob()](#glob()).

### <a id="The "" item can be used to search in a directory tree." class="section-title" href="#The "" item can be used to search in a directory tree.">Note:</a>
For example, to find all "README.txt" files in the directories
in 'runtimepath' and below:
```
### <a id=":echo globpath(&rtp, "/README.txt")" class="section-title" href="#:echo globpath(&rtp, "/README.txt")">Note:</a>
### <a id="Upwards search and limiting the depth of "" is not" class="section-title" href="#Upwards search and limiting the depth of "" is not"><</a>
supported, thus using 'path' will not always work properly.

Can also be used as a [method](#method), the base is passed as the
second argument:
```
GetExpr()->globpath(&rtp)

```

### <a id="has()" class="section-title" href="#has()">Note:</a>
has({feature})	Returns 1 if {feature} is supported, 0 otherwise.  The
{feature} argument is a feature name like "nvim-0.2.1" or
"win32", see below.  See also [exists()](#exists()).

To get the system name use [vim.loop](#vim.loop).os_uname() in Lua:
```
:lua print(vim.loop.os_uname().sysname)


```
		If the code has a syntax error then Vimscript may skip the
rest of the line.  Put [:if| and |:endif](#:if| and |:endif) on separate lines to
avoid the syntax error:
```
if has('feature')
let x = this->breaks->without->the->feature
endif

```

Vim's compile-time feature-names (prefixed with "+") are not
recognized because Nvim is always compiled with all possible
features. [feature-compile](#feature-compile)

Feature names can be:
1.  Nvim version. For example the "nvim-0.2.1" feature means
that Nvim is version 0.2.1 or later:
```
:if has("nvim-0.2.1")


```
		2.  Runtime condition or other pseudo-feature. For example the
"win32" feature checks if the current system is Windows:
```
:if has("win32")
### <a id="feature-list" class="section-title" href="#feature-list"><</a>
List of supported pseudo-feature names:
acl		[ACL](#ACL) support.
bsd		BSD system (not macOS, use "mac" for that).
clipboard	[clipboard](#clipboard) provider is available.
fname_case	Case in file names matters (for Darwin and MS-Windows
this is not present).
iconv		Can use [iconv()](#iconv()) for conversion.
linux		Linux system.
mac		MacOS system.
nvim		This is Nvim.
python3		Legacy Vim [python3| interface. |has-python](#python3| interface. |has-python)
pythonx		Legacy Vim [python_x| interface. |has-pythonx](#python_x| interface. |has-pythonx)
sun		SunOS system.
ttyin		input is a terminal (tty).
ttyout		output is a terminal (tty).
unix		Unix system.
### <a id="vim_starting	True during [startup|." class="section-title" href="#vim_starting	True during |startup](#startup|." class="section-title" href="#vim_starting	True during |startup).">Note:</a>
win32		Windows system (32 or 64 bit).
win64		Windows system (64 bit).
wsl		WSL (Windows Subsystem for Linux) system.

### <a id="has-patch" class="section-title" href="#has-patch">Note:</a>
3.  Vim patch. For example the "patch123" feature means that
Vim patch 123 at the current [v:version](#v:version) was included:
```
:if v:version > 602 || v:version == 602 && has("patch148")


```
		4.  Vim version. For example the "patch-7.4.237" feature means
that Nvim is Vim-compatible to version 7.4.237 or later.
```
:if has("patch-7.4.237")


### <a id="has_key()" class="section-title" href="#has_key()">has_key({dict}, {key})</a>
The result is a Number, which is TRUE if [Dictionary](#Dictionary) {dict}
has an entry with key {key}.  FALSE otherwise. The {key}
argument is a string.

Can also be used as a [method](#method):
```
mydict->has_key(key)

### <a id="haslocaldir()" class="section-title" href="#haslocaldir()">haslocaldir([{winnr} [, {tabnr}]])</a>
The result is a Number, which is 1 when the window has set a
local path via [:lcd](#:lcd) or when {winnr} is -1 and the tabpage
has set a local path via [:tcd](#:tcd), otherwise 0.

Tabs and windows are identified by their respective numbers,
0 means current tab or window. Missing argument implies 0.
Thus the following are equivalent:
```
haslocaldir()
haslocaldir(0)
haslocaldir(0, 0)

```
		With {winnr} use that window in the current tabpage.
With {winnr} and {tabnr} use the window in that tabpage.
{winnr} can be the window number or the [window-ID](#window-ID).
If {winnr} is -1 it is ignored, only the tab is resolved.
Throw error if the arguments are invalid. [E5000| |E5001| |E5002](#E5000| |E5001| |E5002)

Can also be used as a [method](#method):
```
GetWinnr()->haslocaldir()

### <a id="hasmapto()" class="section-title" href="#hasmapto()">hasmapto({what} [, {mode} [, {abbr}]])</a>
The result is a Number, which is TRUE if there is a mapping
that contains {what} in somewhere in the rhs (what it is
mapped to) and this mapping exists in one of the modes
indicated by {mode}.
The arguments {what} and {mode} are strings.
When {abbr} is there and it is [TRUE](#TRUE) use abbreviations
instead of mappings.  Don't forget to specify Insert and/or
Command-line mode.
Both the global mappings and the mappings local to the current
buffer are checked for a match.
If no matching mapping is found FALSE is returned.
The following characters are recognized in {mode}:
n	Normal mode
v	Visual and Select mode
x	Visual mode
s	Select mode
o	Operator-pending mode
i	Insert mode
l	Language-Argument ("r", "f", "t", etc.)
c	Command-line mode
When {mode} is omitted, "nvo" is used.

This function is useful to check if a mapping already exists
to a function in a Vim script.  Example:
```
:if !hasmapto('\ABCdoit')
:   map <Leader>d \ABCdoit
:endif

```
		This installs the mapping to "\ABCdoit" only if there isn't
already a mapping to "\ABCdoit".

Can also be used as a [method](#method):
```
GetRHS()->hasmapto()

### <a id="histadd()" class="section-title" href="#histadd()">histadd({history}, {item})</a>
Add the String {item} to the history {history} which can be
one of:					*hist-names*
"cmd"	 or ":"	  command line history
"search" or "/"   search pattern history
"expr"	 or "="   typed expression history
"input"  or "@"	  input line history
"debug"  or ">"   debug command history
empty		  the current or last used history
The {history} string does not need to be the whole name, one
character is sufficient.
If {item} does already exist in the history, it will be
shifted to become the newest entry.
The result is a Number: TRUE if the operation was successful,
otherwise FALSE is returned.

Example:
```
:call histadd("input", strftime("%Y %b %d"))
:let date=input("Enter date: ")

```
		This function is not available in the [sandbox](#sandbox).

Can also be used as a [method](#method), the base is passed as the
second argument:
```
GetHistory()->histadd('search')

### <a id="histdel()" class="section-title" href="#histdel()">histdel({history} [, {item}])</a>
Clear {history}, i.e. delete all its entries.  See [hist-names](#hist-names)
for the possible values of {history}.

If the parameter {item} evaluates to a String, it is used as a
regular expression.  All entries matching that expression will
be removed from the history (if there are any).
Upper/lowercase must match, unless "\c" is used [/\c](#/\c).
If {item} evaluates to a Number, it will be interpreted as
an index, see [:history-indexing](#:history-indexing).  The respective entry will
be removed if it exists.

The result is TRUE for a successful operation, otherwise FALSE
is returned.

Examples:
Clear expression register history:
```
:call histdel("expr")

```

### <a id="Remove all entries starting with "" from the search history: >" class="section-title" href="#Remove all entries starting with "" from the search history: >">Note:</a>
### <a id=":call histdel("/", '^\')" class="section-title" href="#:call histdel("/", '^\')">Note:</a>

```

The following three are equivalent:
```
:call histdel("search", histnr("search"))
:call histdel("search", -1)
:call histdel("search", '^' .. histget("search", -1) .. '$')

```

To delete the last search pattern and use the last-but-one for
the "n" command and 'hlsearch':
```
:call histdel("search", -1)
:let @/ = histget("search", -1)

```

Can also be used as a [method](#method):
```
GetHistory()->histdel()

### <a id="histget()" class="section-title" href="#histget()">histget({history} [, {index}])</a>
The result is a String, the entry with Number {index} from
{history}.  See [hist-names](#hist-names) for the possible values of
{history}, and [:history-indexing](#:history-indexing) for {index}.  If there is
no such entry, an empty String is returned.  When {index} is
omitted, the most recent item from the history is used.

Examples:
Redo the second last search from history.
```
:execute '/' .. histget("search", -2)


```
		Define an Ex command ":H {num}" that supports re-execution of
the {num}th entry from the output of [:history](#:history).
```
:command -nargs=1 H execute histget("cmd", 0+<args>)

```

Can also be used as a [method](#method):
```
GetHistory()->histget()

### <a id="histnr()" class="section-title" href="#histnr()">histnr({history})</a>
The result is the Number of the current entry in {history}.
See [hist-names](#hist-names) for the possible values of {history}.
If an error occurred, -1 is returned.

Example:
```
:let inp_index = histnr("expr")


```
		Can also be used as a [method](#method):
```
GetHistory()->histnr()

```

### <a id="hlexists()" class="section-title" href="#hlexists()">hlexists({name})</a>
The result is a Number, which is TRUE if a highlight group
called {name} exists.  This is when the group has been
defined in some way.  Not necessarily when highlighting has
been defined for it, it may also have been used for a syntax
item.

Can also be used as a [method](#method):
```
GetName()->hlexists()

```

### <a id="hlID()" class="section-title" href="#hlID()">Note:</a>
hlID({name})	The result is a Number, which is the ID of the highlight group
with name {name}.  When the highlight group doesn't exist,
zero is returned.
This can be used to retrieve information about the highlight
group.  For example, to get the background color of the
"Comment" group:
```
:echo synIDattr(synIDtrans(hlID("Comment")), "bg")

```

Can also be used as a [method](#method):
```
GetName()->hlID()

### <a id="hostname()" class="section-title" href="#hostname()">hostname()</a>
The result is a String, which is the name of the machine on
which Vim is currently running.  Machine names greater than
256 characters long are truncated.

### <a id="iconv()" class="section-title" href="#iconv()">iconv({string}, {from}, {to})</a>
The result is a String, which is the text {string} converted
from encoding {from} to encoding {to}.
When the conversion completely fails an empty string is
returned.  When some characters could not be converted they
are replaced with "?".
The encoding names are whatever the iconv() library function
can accept, see ":!man 3 iconv".
Note that Vim uses UTF-8 for all Unicode encodings, conversion
from/to UCS-2 is automatically changed to use UTF-8.  You
cannot use UCS-2 in a string anyway, because of the NUL bytes.

Can also be used as a [method](#method):
```
GetText()->iconv('latin1', 'utf-8')

```

### <a id="indent()" class="section-title" href="#indent()">Note:</a>
indent({lnum})	The result is a Number, which is indent of line {lnum} in the
current buffer.  The indent is counted in spaces, the value
of 'tabstop' is relevant.  {lnum} is used just like in
[getline()](#getline()).
When {lnum} is invalid -1 is returned.

Can also be used as a [method](#method):
```
GetLnum()->indent()

### <a id="index()" class="section-title" href="#index()">index({object}, {expr} [, {start} [, {ic}]])</a>
If {object} is a [List](#List) return the lowest index where the item
has a value equal to {expr}.  There is no automatic
conversion, so the String "4" is different from the Number 4.
And the Number 4 is different from the Float 4.0.  The value
of 'ignorecase' is not used here, case always matters.

If {object} is a [Blob](#Blob) return the lowest index where the byte
value is equal to {expr}.

If {start} is given then start looking at the item with index
{start} (may be negative for an item relative to the end).
When {ic} is given and it is [TRUE](#TRUE), ignore case.  Otherwise
case must match.
-1 is returned when {expr} is not found in {object}.
Example:
```
:let idx = index(words, "the")
:if index(numbers, 123) >= 0


```
		Can also be used as a [method](#method):
```
GetObject()->index(what)

### <a id="input()" class="section-title" href="#input()">input({prompt} [, {text} [, {completion}]])</a>
input({opts})
The result is a String, which is whatever the user typed on
the command-line.  The {prompt} argument is either a prompt
string, or a blank string (for no prompt).  A '\n' can be used
in the prompt to start a new line.

In the second form it accepts a single dictionary with the
following keys, any of which may be omitted:

Key           Default  Description ~
prompt        ""       Same as {prompt} in the first form.
default       ""       Same as {text} in the first form.
completion    nothing  Same as {completion} in the first form.
cancelreturn  ""       The value returned when the dialog is
cancelled.
highlight     nothing  Highlight handler: [Funcref](#Funcref).

The highlighting set with [:echohl](#:echohl) is used for the prompt.
The input is entered just like a command-line, with the same
editing commands and mappings.  There is a separate history
for lines typed for input().
Example:
```
:if input("Coffee or beer? ") == "beer"
:  echo "Cheers!"
:endif

```

If the optional {text} argument is present and not empty, this
is used for the default reply, as if the user typed this.
Example:
```
:let color = input("Color? ", "white")


```
		The optional {completion} argument specifies the type of
completion supported for the input.  Without it completion is
not performed.  The supported completion types are the same as
that can be supplied to a user-defined command using the
"-complete=" argument.  Refer to [:command-completion](#:command-completion) for
more information.  Example:
```
let fname = input("File: ", "", "file")

### <a id="input()-highlight E5400 E5402" class="section-title" href="#input()-highlight E5400 E5402"><</a>
The optional `highlight` key allows specifying function which
will be used for highlighting user input.  This function
receives user input as its only argument and must return
a list of 3-tuples [hl_start_col, hl_end_col + 1, hl_group]
where
hl_start_col is the first highlighted column,
hl_end_col is the last highlighted column (+ 1!),
hl_group is [:hi](#:hi) group used for highlighting.
### <a id="E5403 E5404 E5405 E5406" class="section-title" href="#E5403 E5404 E5405 E5406">Note:</a>
Both hl_start_col and hl_end_col + 1 must point to the start
of the multibyte character (highlighting must not break
multibyte characters), hl_end_col + 1 may be equal to the
input length.  Start column must be in range [0, len(input)),
end column must be in range (hl_start_col, len(input)],
sections must be ordered so that next hl_start_col is greater
then or equal to previous hl_end_col.

Example (try some input with parentheses):
```
highlight RBP1 guibg=Red ctermbg=red
highlight RBP2 guibg=Yellow ctermbg=yellow
highlight RBP3 guibg=Green ctermbg=green
highlight RBP4 guibg=Blue ctermbg=blue
let g:rainbow_levels = 4
function! RainbowParens(cmdline)
let ret = []
let i = 0
let lvl = 0
while i < len(a:cmdline)
if a:cmdline[i] is# '('
call add(ret, [i, i + 1, 'RBP' .. ((lvl % g:rainbow_levels) + 1)])
let lvl += 1
elseif a:cmdline[i] is# ')'
let lvl -= 1
call add(ret, [i, i + 1, 'RBP' .. ((lvl % g:rainbow_levels) + 1)])
endif
let i += 1
endwhile
return ret
endfunction
call input({'prompt':'>','highlight':'RainbowParens'})

```

Highlight function is called at least once for each new
displayed input string, before command-line is redrawn.  It is
expected that function is pure for the duration of one input()
call, i.e. it produces the same output for the same input, so
output may be memoized.  Function is run like under [:silent](#:silent)
modifier. If the function causes any errors, it will be
skipped for the duration of the current input() call.

Highlighting is disabled if command-line contains arabic
characters.

NOTE: This function must not be used in a startup file, for
the versions that only run in GUI mode (e.g., the Win32 GUI).
Note: When input() is called from within a mapping it will
consume remaining characters from that mapping, because a
mapping is handled like the characters were typed.
Use [inputsave()| before input() and |inputrestore()](#inputsave()| before input() and |inputrestore())
after input() to avoid that.  Another solution is to avoid
that further characters follow in the mapping, e.g., by using
[:execute| or |:normal](#:execute| or |:normal).

Example with a mapping:
```
:nmap \x :call GetFoo()<CR>:exe "/" .. Foo<CR>
:function GetFoo()
:  call inputsave()
:  let g:Foo = input("enter search pattern: ")
:  call inputrestore()
:endfunction


```
		Can also be used as a [method](#method):
```
GetPrompt()->input()

### <a id="inputlist()" class="section-title" href="#inputlist()">inputlist({textlist})</a>
{textlist} must be a [List| of strings.  This |List](#List| of strings.  This |List) is
displayed, one string per line.  The user will be prompted to
enter a number, which is returned.
The user can also select an item by clicking on it with the
mouse, if the mouse is enabled in the command line ('mouse' is
"a" or includes "c").  For the first string 0 is returned.
When clicking above the first item a negative number is
returned.  When clicking on the prompt one more than the
length of {textlist} is returned.
Make sure {textlist} has less than 'lines' entries, otherwise
it won't work.  It's a good idea to put the entry number at
the start of the string.  And put a prompt in the first item.
Example:
```
let color = inputlist(['Select color:', '1. red',
\ '2. green', '3. blue'])


```
		Can also be used as a [method](#method):
```
GetChoices()->inputlist()

### <a id="inputrestore()" class="section-title" href="#inputrestore()">inputrestore()</a>
Restore typeahead that was saved with a previous [inputsave()](#inputsave()).
Should be called the same number of times inputsave() is
called.  Calling it more often is harmless though.
Returns TRUE when there is nothing to restore, FALSE otherwise.

### <a id="inputsave()" class="section-title" href="#inputsave()">inputsave()</a>
Preserve typeahead (also from mappings) and clear it, so that
a following prompt gets input from the user.  Should be
followed by a matching inputrestore() after the prompt.  Can
be used several times, in which case there must be just as
many inputrestore() calls.
Returns TRUE when out of memory, FALSE otherwise.

### <a id="inputsecret()" class="section-title" href="#inputsecret()">inputsecret({prompt} [, {text}])</a>
This function acts much like the [input()](#input()) function with but
two exceptions:
a) the user's response will be displayed as a sequence of
### <a id="asterisks ("") thereby keeping the entry secret, and" class="section-title" href="#asterisks ("") thereby keeping the entry secret, and">Note:</a>
b) the user's response will not be recorded on the input
[history](#history) stack.
The result is a String, which is whatever the user actually
typed on the command-line in response to the issued prompt.
NOTE: Command-line completion is not supported.

Can also be used as a [method](#method):
```
GetPrompt()->inputsecret()

### <a id="insert()" class="section-title" href="#insert()">insert({object}, {item} [, {idx}])</a>
When {object} is a [List| or a |Blob](#List| or a |Blob) insert {item} at the start
of it.

If {idx} is specified insert {item} before the item with index
{idx}.  If {idx} is zero it goes before the first item, just
like omitting {idx}.  A negative {idx} is also possible, see
[list-index](#list-index).  -1 inserts just before the last item.

Returns the resulting [List| or |Blob](#List| or |Blob).  Examples:
```
:let mylist = insert([2, 3, 5], 1)
:call insert(mylist, 4, -1)
:call insert(mylist, 6, len(mylist))

```
		The last example can be done simpler with [add()](#add()).
Note that when {item} is a [List](#List) it is inserted as a single
item.  Use [extend()| to concatenate |Lists](#extend()| to concatenate |Lists).

Can also be used as a [method](#method):
```
mylist->insert(item)

### <a id="interrupt()" class="section-title" href="#interrupt()">interrupt()</a>
Interrupt script execution.  It works more or less like the
user typing CTRL-C, most commands won't execute and control
returns to the user.  This is useful to abort execution
from lower down, e.g. in an autocommand.  Example:
```
:function s:check_typoname(file)
:   if fnamemodify(a:file, ':t') == '['
:       echomsg 'Maybe typo'
:       call interrupt()
:   endif
:endfunction
### <a id=":au BufWritePre  call s:check_typoname(expand('<amatch>'))" class="section-title" href="#:au BufWritePre  call s:check_typoname(expand('<amatch>'))">Note:</a>

### <a id="invert()" class="section-title" href="#invert()">invert({expr})</a>
Bitwise invert.  The argument is converted to a number.  A
List, Dict or Float argument causes an error.  Example:
```
:let bits = invert(bits)

```
		Can also be used as a [method](#method):
```
:let bits = bits->invert()

### <a id="isdirectory()" class="section-title" href="#isdirectory()">isdirectory({directory})</a>
The result is a Number, which is [TRUE](#TRUE) when a directory
with the name {directory} exists.  If {directory} doesn't
exist, or isn't a directory, the result is [FALSE](#FALSE).  {directory}
is any expression, which is used as a String.

Can also be used as a [method](#method):
```
GetName()->isdirectory()

### <a id="isinf()" class="section-title" href="#isinf()">isinf({expr})</a>
Return 1 if {expr} is a positive infinity, or -1 a negative
infinity, otherwise 0.
```
:echo isinf(1.0 / 0.0)

```
			1
```
:echo isinf(-1.0 / 0.0)

```
			-1

Can also be used as a [method](#method):
```
Compute()->isinf()

### <a id="islocked() E786" class="section-title" href="#islocked() E786">islocked({expr})</a>
The result is a Number, which is [TRUE](#TRUE) when {expr} is the
name of a locked variable.
The string argument {expr} must be the name of a variable,
[List| item or |Dictionary](#List| item or |Dictionary) entry, not the variable itself!
Example:
```
:let alist = [0, ['a', 'b'], 2, 3]
:lockvar 1 alist
:echo islocked('alist')		" 1
:echo islocked('alist[1]')	" 0


```
		When {expr} is a variable that does not exist you get an error
message.  Use [exists()](#exists()) to check for existence.

Can also be used as a [method](#method):
```
GetName()->islocked()

### <a id="id()" class="section-title" href="#id()">id({expr})</a>
Returns a [String](#String) which is a unique identifier of the
container type ([List|, |Dict|, |Blob| and |Partial](#List|, |Dict|, |Blob| and |Partial)). It is
guaranteed that for the mentioned types `id(v1) ==# id(v2)`
returns true iff `type(v1) == type(v2) && v1 is v2`.
Note that [v:_null_string|, |v:_null_list|, |v:_null_dict](#v:_null_string|, |v:_null_list|, |v:_null_dict) and
[v:_null_blob](#v:_null_blob) have the same `id()` with different types
because they are internally represented as NULL pointers.
`id()` returns a hexadecimal representanion of the pointers to
the containers (i.e. like `0x994a40`), same as `printf("%p",
{expr})`, but it is advised against counting on the exact
format of the return value.

It is not guaranteed that `id(no_longer_existing_container)`
will not be equal to some other `id()`: new containers may
reuse identifiers of the garbage-collected ones.

### <a id="items()" class="section-title" href="#items()">items({dict})</a>
Return a [List](#List) with all the key-value pairs of {dict}.  Each
[List](#List) item is a list with two items: the key of a {dict}
entry and the value of this entry.  The [List](#List) is in arbitrary
order.  Also see [keys()| and |values()](#keys()| and |values()).
Example:
```
for [key, value] in items(mydict)
echo key .. ': ' .. value
endfor


```
		Can also be used as a [method](#method):
```
mydict->items()

### <a id="isnan()" class="section-title" href="#isnan()">isnan({expr})</a>
Return [TRUE](#TRUE) if {expr} is a float with value NaN.
```
echo isnan(0.0 / 0.0)

```
			1

Can also be used as a [method](#method):
```
Compute()->isnan()

### <a id="jobpid()" class="section-title" href="#jobpid()">jobpid({job})</a>
Return the PID (process id) of [job-id](#job-id) {job}.

### <a id="jobresize()" class="section-title" href="#jobresize()">jobresize({job}, {width}, {height})</a>
Resize the pseudo terminal window of [job-id](#job-id) {job} to {width}
columns and {height} rows.
Fails if the job was not started with `"pty":v:true`.

### <a id="jobstart()" class="section-title" href="#jobstart()">jobstart({cmd} [, {opts}])</a>
Spawns {cmd} as a job.
If {cmd} is a List it runs directly (no 'shell').
If {cmd} is a String it runs in the 'shell', like this:
```
:call jobstart(split(&shell) + split(&shellcmdflag) + ['{cmd}'])

```
		(See [shell-unquoting](#shell-unquoting) for details.)

Example:
```
:call jobstart('nvim -h', {'on_stdout':{j,d,e->append(line('.'),d)}})

```

Returns [job-id](#job-id) on success, 0 on invalid arguments (or job
table is full), -1 if {cmd}[0] or 'shell' is not executable.
The returned job-id is a valid [channel-id](#channel-id) representing the
job's stdio streams. Use [chansend()| (or |rpcnotify()](#chansend()| (or |rpcnotify()) and
[rpcrequest()](#rpcrequest()) if "rpc" was enabled) to send data to stdin and
[chanclose()](#chanclose()) to close the streams without stopping the job.

See [job-control| and |RPC](#job-control| and |RPC).

NOTE: on Windows if {cmd} is a List:
- cmd[0] must be an executable (not a "built-in"). If it is
in $PATH it can be called by name, without an extension:
```
:call jobstart(['ping', 'neovim.io'])

```
		    If it is a full or partial path, extension is required:
```
:call jobstart(['System32\ping.exe', 'neovim.io'])

```
		  - {cmd} is collapsed to a string of quoted args as expected
by CommandLineToArgvW https://msdn.microsoft.com/bb776391
unless cmd[0] is some form of "cmd.exe".

### <a id="jobstart-env" class="section-title" href="#jobstart-env">Note:</a>
The job environment is initialized as follows:
$NVIM                is set to [v:servername](#v:servername) of the parent Nvim
$NVIM_LISTEN_ADDRESS is unset
$NVIM_LOG_FILE       is unset
$VIM                 is unset
$VIMRUNTIME          is unset
You can set these with the `env` option.

### <a id="jobstart-options" class="section-title" href="#jobstart-options">Note:</a>
{opts} is a dictionary with these keys:
clear_env:  (boolean) `env` defines the job environment
exactly, instead of merging current environment.
cwd:	      (string, default=[current-directory](#current-directory)) Working
directory of the job.
detach:     (boolean) Detach the job process: it will not be
killed when Nvim exits. If the process exits
before Nvim, `on_exit` will be invoked.
env:	      (dict) Map of environment variable name:value
pairs extending (or replace with "clear_env")
the current environment. [jobstart-env](#jobstart-env)
height:     (number) Height of the `pty` terminal.
[on_exit](#on_exit):    (function) Callback invoked when the job exits.
[on_stdout](#on_stdout):  (function) Callback invoked when the job emits
stdout data.
[on_stderr](#on_stderr):  (function) Callback invoked when the job emits
stderr data.
overlapped: (boolean) Set FILE_FLAG_OVERLAPPED for the
standard input/output passed to the child process.
Normally you do not need to set this.
(Only available on MS-Windows, On other
platforms, this option is silently ignored.)
pty:	      (boolean) Connect the job to a new pseudo
terminal, and its streams to the master file
descriptor. `on_stdout` receives all output,
`on_stderr` is ignored. [terminal-start](#terminal-start)
rpc:	      (boolean) Use [msgpack-rpc](#msgpack-rpc) to communicate with
the job over stdio. Then `on_stdout` is ignored,
but `on_stderr` can still be used.
stderr_buffered: (boolean) Collect data until EOF (stream closed)
before invoking `on_stderr`. [channel-buffered](#channel-buffered)
stdout_buffered: (boolean) Collect data until EOF (stream
closed) before invoking `on_stdout`. [channel-buffered](#channel-buffered)
stdin:      (string) Either "pipe" (default) to connect the
job's stdin to a channel or "null" to disconnect
stdin.
width:      (number) Width of the `pty` terminal.

{opts} is passed as [self](#self) dictionary to the callback; the
caller may set other keys to pass application-specific data.

Returns:
- [channel-id](#channel-id) on success
- 0 on invalid arguments
- -1 if {cmd}[0] is not executable.
See also [job-control|, |channel|, |msgpack-rpc](#job-control|, |channel|, |msgpack-rpc).

### <a id="jobstop()" class="section-title" href="#jobstop()">jobstop({id})</a>
Stop [job-id](#job-id) {id} by sending SIGTERM to the job process. If
the process does not terminate after a timeout then SIGKILL
will be sent. When the job terminates its [on_exit](#on_exit) handler
(if any) will be invoked.
See [job-control](#job-control).

Returns 1 for valid job id, 0 for invalid id, including jobs have
exited or stopped.

### <a id="jobwait()" class="section-title" href="#jobwait()">jobwait({jobs} [, {timeout}])</a>
Waits for jobs and their [on_exit](#on_exit) handlers to complete.

{jobs} is a List of [job-id](#job-id)s to wait for.
{timeout} is the maximum waiting time in milliseconds. If
omitted or -1, wait forever.

Timeout of 0 can be used to check the status of a job:
```
let running = jobwait([{job-id}], 0)[0] == -1

```

During jobwait() callbacks for jobs not in the {jobs} list may
be invoked. The screen will not redraw unless [:redraw](#:redraw) is
invoked by a callback.

Returns a list of len({jobs}) integers, where each integer is
the status of the corresponding job:
Exit-code, if the job exited
-1 if the timeout was exceeded
-2 if the job was interrupted (by [CTRL-C](#CTRL-C))
-3 if the job-id is invalid

### <a id="join()" class="section-title" href="#join()">join({list} [, {sep}])</a>
Join the items in {list} together into one String.
When {sep} is specified it is put in between the items.  If
{sep} is omitted a single space is used.
Note that {sep} is not added at the end.  You might want to
add it there too:
```
let lines = join(mylist, "\n") .. "\n"

```
		String items are used as-is.  [Lists| and |Dictionaries](#Lists| and |Dictionaries) are
converted into a string like with [string()](#string()).
The opposite function is [split()](#split()).

Can also be used as a [method](#method):
```
mylist->join()

### <a id="json_decode()" class="section-title" href="#json_decode()">json_decode({expr})</a>
Convert {expr} from JSON object.  Accepts [readfile()](#readfile())-style
list as the input, as well as regular string.  May output any
Vim value. In the following cases it will output
[msgpack-special-dict](#msgpack-special-dict):
1. Dictionary contains duplicate key.
2. Dictionary contains empty key.
3. String contains NUL byte.  Two special dictionaries: for
dictionary and for string will be emitted in case string
with NUL byte was a dictionary key.

Note: function treats its input as UTF-8 always.  The JSON
standard allows only a few encodings, of which UTF-8 is
recommended and the only one required to be supported.
Non-UTF-8 characters are an error.

Can also be used as a [method](#method):
```
ReadObject()->json_decode()

### <a id="json_encode()" class="section-title" href="#json_encode()">json_encode({expr})</a>
Convert {expr} into a JSON string.  Accepts
[msgpack-special-dict](#msgpack-special-dict) as the input.  Will not convert
[Funcref](#Funcref)s, mappings with non-string keys (can be created as
[msgpack-special-dict](#msgpack-special-dict)), values with self-referencing
containers, strings which contain non-UTF-8 characters,
pseudo-UTF-8 strings which contain codepoints reserved for
surrogate pairs (such strings are not valid UTF-8 strings).
Non-printable characters are converted into "\u1234" escapes
or special escapes like "\t", other are dumped as-is.
[Blob](#Blob)s are converted to arrays of the individual bytes.

Can also be used as a [method](#method):
```
GetObject()->json_encode()

### <a id="keys()" class="section-title" href="#keys()">keys({dict})</a>
Return a [List| with all the keys of {dict}.  The |List](#List| with all the keys of {dict}.  The |List) is in
arbitrary order.  Also see [items()| and |values()](#items()| and |values()).

Can also be used as a [method](#method):
```
mydict->keys()

### <a id="keytrans()" class="section-title" href="#keytrans()">keytrans({string})</a>
Turn the internal byte representation of keys into a form that
can be used for [:map](#:map).  E.g.
```
:let xx = "\<C-Home>"
:echo keytrans(xx)

```
			<C-Home>

Can also be used as a [method](#method):
```
"\<C-Home>"->keytrans()

### <a id="len() E701" class="section-title" href="#len() E701"><</a>
len({expr})	The result is a Number, which is the length of the argument.
When {expr} is a String or a Number the length in bytes is
used, as with [strlen()](#strlen()).
When {expr} is a [List| the number of items in the |List](#List| the number of items in the |List) is
returned.
When {expr} is a [Blob](#Blob) the number of bytes is returned.
When {expr} is a [Dictionary](#Dictionary) the number of entries in the
[Dictionary](#Dictionary) is returned.
Otherwise an error is given and returns zero.

Can also be used as a [method](#method):
```
mylist->len()

### <a id="libcall() E364 E368" class="section-title" href="#libcall() E364 E368"><</a>
libcall({libname}, {funcname}, {argument})
Call function {funcname} in the run-time library {libname}
with single argument {argument}.
This is useful to call functions in a library that you
especially made to be used with Vim.  Since only one argument
is possible, calling standard library functions is rather
limited.
The result is the String returned by the function.  If the
function returns NULL, this will appear as an empty string ""
to Vim.
If the function returns a number, use libcallnr()!
If {argument} is a number, it is passed to the function as an
int; if {argument} is a string, it is passed as a
null-terminated string.

libcall() allows you to write your own 'plug-in' extensions to
Vim without having to recompile the program.  It is NOT a
means to call system functions!  If you try to do so Vim will
very probably crash.

For Win32, the functions you write must be placed in a DLL
and use the normal C calling convention (NOT Pascal which is
used in Windows System DLLs).  The function must take exactly
one parameter, either a character pointer or a long integer,
and must return a character pointer or NULL.  The character
pointer returned must point to memory that will remain valid
after the function has returned (e.g. in static data in the
DLL).  If it points to allocated memory, that memory will
leak away.  Using a static buffer in the function should work,
it's then freed when the DLL is unloaded.

WARNING: If the function returns a non-valid pointer, Vim may
crash!	This also happens if the function returns a number,
because Vim thinks it's a pointer.
For Win32 systems, {libname} should be the filename of the DLL
without the ".DLL" suffix.  A full path is only required if
the DLL is not in the usual places.
For Unix: When compiling your own plugins, remember that the
object code must be compiled as position-independent ('PIC').
Examples:
```
:echo libcall("libc.so", "getenv", "HOME")


```
		Can also be used as a [method](#method), the base is passed as the
third argument:
```
GetValue()->libcall("libc.so", "getenv")

```

### <a id="libcallnr()" class="section-title" href="#libcallnr()">Note:</a>
libcallnr({libname}, {funcname}, {argument})
Just like [libcall()](#libcall()), but used for a function that returns an
int instead of a string.
Examples:
```
:echo libcallnr("/usr/lib/libc.so", "getpid", "")
:call libcallnr("libc.so", "printf", "Hello World!\n")
:call libcallnr("libc.so", "sleep", 10)

```

Can also be used as a [method](#method), the base is passed as the
third argument:
```
GetValue()->libcallnr("libc.so", "printf")

```

### <a id="line()" class="section-title" href="#line()">line({expr} [, {winid}])</a>
The result is a Number, which is the line number of the file
position given with {expr}.  The {expr} argument is a string.
The accepted positions are:
.	    the cursor position
$	    the last line in the current buffer
'x	    position of mark x (if the mark is not set, 0 is
returned)
w0	    first line visible in current window (one if the
display isn't updated, e.g. in silent Ex mode)
w$	    last line visible in current window (this is one
less than "w0" if no lines are visible)
v	    In Visual mode: the start of the Visual area (the
cursor is the end).  When not in Visual mode
returns the cursor position.  Differs from ['<](#'<) in
that it's updated right away.
Note that a mark in another file can be used.  The line number
then applies to another buffer.
To get the column number use [col()](#col()).  To get both use
[getpos()](#getpos()).
With the optional {winid} argument the values are obtained for
that window instead of the current window.
Returns 0 for invalid values of {expr} and {winid}.
Examples:
```
line(".")		line number of the cursor
line(".", winid)	idem, in window "winid"
line("'t")		line number of mark t
line("'" .. marker)	line number of mark marker

```

To jump to the last known position when opening a file see
[last-position-jump](#last-position-jump).

Can also be used as a [method](#method):
```
GetValue()->line()

### <a id="line2byte()" class="section-title" href="#line2byte()">line2byte({lnum})</a>
Return the byte count from the start of the buffer for line
{lnum}.  This includes the end-of-line character, depending on
the 'fileformat' option for the current buffer.  The first
line returns 1. UTF-8 encoding is used, 'fileencoding' is
ignored.  This can also be used to get the byte count for the
line just below the last line:
```
line2byte(line("$") + 1)

```
		This is the buffer size plus one.  If 'fileencoding' is empty
it is the file size plus one.  {lnum} is used like with
[getline()](#getline()).  When {lnum} is invalid -1 is returned.
Also see [byte2line()|, |go| and |:goto](#byte2line()|, |go| and |:goto).

Can also be used as a [method](#method):
```
GetLnum()->line2byte()

### <a id="lispindent()" class="section-title" href="#lispindent()">lispindent({lnum})</a>
Get the amount of indent for line {lnum} according the lisp
indenting rules, as with 'lisp'.
The indent is counted in spaces, the value of 'tabstop' is
relevant.  {lnum} is used just like in [getline()](#getline()).
When {lnum} is invalid, -1 is returned.

Can also be used as a [method](#method):
```
GetLnum()->lispindent()

### <a id="list2str()" class="section-title" href="#list2str()">list2str({list} [, {utf8}])</a>
Convert each number in {list} to a character string can
concatenate them all.  Examples:
```
list2str([32])		returns " "
list2str([65, 66, 67])	returns "ABC"

```
		The same can be done (slowly) with:
```
join(map(list, {nr, val -> nr2char(val)}), '')

```
		[str2list()](#str2list()) does the opposite.

UTF-8 encoding is always used, {utf8} option has no effect,
and exists only for backwards-compatibility.
With UTF-8 composing characters work as expected:
```
list2str([97, 769])	returns "á"

```

Returns an empty string on error.

Can also be used as a [method](#method):
```
GetList()->list2str()

### <a id="localtime()" class="section-title" href="#localtime()">localtime()</a>
Return the current time, measured as seconds since 1st Jan
1970.  See also [strftime()|, |strptime()| and |getftime()](#strftime()|, |strptime()| and |getftime()).


### <a id="log()" class="section-title" href="#log()">log({expr})</a>
Return the natural logarithm (base e) of {expr} as a [Float](#Float).
{expr} must evaluate to a [Float| or a |Number](#Float| or a |Number) in the range
(0, inf].
Returns 0.0 if {expr} is not a [Float| or a |Number](#Float| or a |Number).
Examples:
```
:echo log(10)

```
			2.302585
```
:echo log(exp(5))

```
			5.0

Can also be used as a [method](#method):
```
Compute()->log()

### <a id="log10()" class="section-title" href="#log10()">log10({expr})</a>
Return the logarithm of Float {expr} to base 10 as a [Float](#Float).
{expr} must evaluate to a [Float| or a |Number](#Float| or a |Number).
Returns 0.0 if {expr} is not a [Float| or a |Number](#Float| or a |Number).
Examples:
```
:echo log10(1000)

```
			3.0
```
:echo log10(0.01)

```
			-2.0

Can also be used as a [method](#method):
```
Compute()->log10()

luaeval({expr} [, {expr}])
Evaluate Lua expression {expr} and return its result converted
to Vim data structures. See [lua-eval](#lua-eval) for more details.

Can also be used as a [method](#method):
```
GetExpr()->luaeval()

### <a id="map()" class="section-title" href="#map()">map({expr1}, {expr2})</a>
{expr1} must be a [List|, |Blob| or |Dictionary](#List|, |Blob| or |Dictionary).
Replace each item in {expr1} with the result of evaluating
{expr2}.  For a [Blob](#Blob) each byte is replaced.

{expr2} must be a [string| or |Funcref](#string| or |Funcref).

If {expr2} is a [string|, inside {expr2} |v:val](#string|, inside {expr2} |v:val) has the value
of the current item.  For a [Dictionary| |v:key](#Dictionary| |v:key) has the key
of the current item and for a [List| |v:key](#List| |v:key) has the index of
the current item.  For a [Blob| |v:key](#Blob| |v:key) has the index of the
current byte.
Example:
```
:call map(mylist, '"> " .. v:val .. " <"')

```
		This puts "> " before and " <" after each item in "mylist".

Note that {expr2} is the result of an expression and is then
used as an expression again.  Often it is good to use a
[literal-string](#literal-string) to avoid having to double backslashes.  You
still have to double ' quotes

If {expr2} is a [Funcref](#Funcref) it is called with two arguments:
1. The key or the index of the current item.
2. the value of the current item.
The function must return the new value of the item. Example
that changes each value by "key-value":
```
func KeyValue(key, val)
return a:key .. '-' .. a:val
endfunc
call map(myDict, function('KeyValue'))

```
		It is shorter when using a [lambda](#lambda):
```
call map(myDict, {key, val -> key .. '-' .. val})

```
		If you do not use "val" you can leave it out:
```
call map(myDict, {key -> 'item: ' .. key})

```
		If you do not use "key" you can use a short name:
```
call map(myDict, {_, val -> 'item: ' .. val})

```

The operation is done in-place.  If you want a [List](#List) or
[Dictionary](#Dictionary) to remain unmodified make a copy first:
```
:let tlist = map(copy(mylist), ' v:val .. "\t"')


```
		Returns {expr1}, the [List|, |Blob| or |Dictionary](#List|, |Blob| or |Dictionary) that was
filtered.  When an error is encountered while evaluating
{expr2} no further items in {expr1} are processed.  When
{expr2} is a Funcref errors inside a function are ignored,
unless it was defined with the "abort" flag.

Can also be used as a [method](#method):
```
mylist->map(expr2)


### <a id="maparg()" class="section-title" href="#maparg()">maparg({name} [, {mode} [, {abbr} [, {dict}]]])</a>
When {dict} is omitted or zero: Return the rhs of mapping
{name} in mode {mode}.  The returned String has special
characters translated like in the output of the ":map" command
listing.

When there is no mapping for {name}, an empty String is
returned if {dict} is FALSE, otherwise returns an empty Dict.
When the mapping for {name} is empty, then "<Nop>" is
returned.

The {name} can have special key names, like in the ":map"
command.

{mode} can be one of these strings:
"n"	Normal
"v"	Visual (including Select)
"o"	Operator-pending
"i"	Insert
"c"	Cmd-line
"s"	Select
"x"	Visual
"l"	langmap [language-mapping](#language-mapping)
"t"	Terminal
""	Normal, Visual and Operator-pending
When {mode} is omitted, the modes for "" are used.

When {abbr} is there and it is [TRUE](#TRUE) use abbreviations
instead of mappings.

When {dict} is there and it is [TRUE](#TRUE) return a dictionary
containing all the information of the mapping with the
following items:
"lhs"	     The {lhs} of the mapping as it would be typed
"lhsraw"   The {lhs} of the mapping as raw bytes
"lhsrawalt" The {lhs} of the mapping as raw bytes, alternate
form, only present when it differs from "lhsraw"
"rhs"	     The {rhs} of the mapping as typed.
"silent"   1 for a [:map-silent](#:map-silent) mapping, else 0.
"noremap"  1 if the {rhs} of the mapping is not remappable.
"script"   1 if mapping was defined with <script>.
"expr"     1 for an expression mapping ([:map-<expr>](#:map-<expr>)).
"buffer"   1 for a buffer local mapping ([:map-local](#:map-local)).
"mode"     Modes for which the mapping is defined. In
addition to the modes mentioned above, these
characters will be used:
" "     Normal, Visual and Operator-pending
"!"     Insert and Commandline mode
([mapmode-ic](#mapmode-ic))
"sid"	     The script local ID, used for <sid> mappings
([<SID>](#<SID>)).
"lnum"     The line number in "sid", zero if unknown.
"nowait"   Do not wait for other, longer mappings.
([:map-<nowait>](#:map-<nowait>)).

The dictionary can be used to restore a mapping with
[mapset()](#mapset()).

The mappings local to the current buffer are checked first,
then the global mappings.
This function can be used to map a key even when it's already
mapped, and have it do the original mapping too.  Sketch:
```
exe 'nnoremap <Tab> ==' .. maparg('<Tab>', 'n')


```
		Can also be used as a [method](#method):
```
GetKey()->maparg('n')

### <a id="mapcheck()" class="section-title" href="#mapcheck()">mapcheck({name} [, {mode} [, {abbr}]])</a>
Check if there is a mapping that matches with {name} in mode
{mode}.  See [maparg()](#maparg()) for {mode} and special names in
{name}.
When {abbr} is there and it is non-zero use abbreviations
instead of mappings.
A match happens with a mapping that starts with {name} and
with a mapping which is equal to the start of {name}.

matches mapping "a"	"ab"	"abc" ~
mapcheck("a")	yes	yes	 yes
mapcheck("abc")	yes	yes	 yes
mapcheck("ax")	yes	no	 no
mapcheck("b")	no	no	 no

The difference with maparg() is that mapcheck() finds a
mapping that matches with {name}, while maparg() only finds a
mapping for {name} exactly.
When there is no mapping that starts with {name}, an empty
String is returned.  If there is one, the RHS of that mapping
is returned.  If there are several mappings that start with
{name}, the RHS of one of them is returned.  This will be
"<Nop>" if the RHS is empty.
The mappings local to the current buffer are checked first,
then the global mappings.
This function can be used to check if a mapping can be added
without being ambiguous.  Example:
```
:if mapcheck("_vv") == ""
:   map _vv :set guifont=7x13<CR>
:endif

```
		This avoids adding the "_vv" mapping when there already is a
mapping for "_v" or for "_vvv".

Can also be used as a [method](#method):
```
GetKey()->mapcheck('n')

### <a id="mapset()" class="section-title" href="#mapset()">mapset({mode}, {abbr}, {dict})</a>
Restore a mapping from a dictionary returned by [maparg()](#maparg()).
{mode} and {abbr} should be the same as for the call to
### <a id="[maparg()|. E460" class="section-title" href="#|maparg()](#maparg()|. E460" class="section-title" href="#|maparg()). E460">Note:</a>
{mode} is used to define the mode in which the mapping is set,
not the "mode" entry in {dict}.
Example for saving and restoring a mapping:
```
let save_map = maparg('K', 'n', 0, 1)
nnoremap K somethingelse
...
call mapset('n', 0, save_map)

```
		Note that if you are going to replace a map in several modes,
e.g. with `:map!`, you need to save the mapping for all of
them, since they can differ.


### <a id="match()" class="section-title" href="#match()">match({expr}, {pat} [, {start} [, {count}]])</a>
When {expr} is a [List](#List) then this returns the index of the
first item where {pat} matches.  Each item is used as a
String, [Lists| and |Dictionaries](#Lists| and |Dictionaries) are used as echoed.

Otherwise, {expr} is used as a String.  The result is a
Number, which gives the index (byte offset) in {expr} where
{pat} matches.

A match at the first character or [List](#List) item returns zero.
If there is no match -1 is returned.

For getting submatches see [matchlist()](#matchlist()).
Example:
```
:echo match("testing", "ing")	" results in 4
:echo match([1, 'x'], '\a')	" results in 1

```
		See [string-match](#string-match) for how {pat} is used.
### <a id="strpbrk()" class="section-title" href="#strpbrk()">Note:</a>
Vim doesn't have a strpbrk() function.  But you can do:
```
:let sepidx = match(line, '[.,;: \t]')
### <a id="strcasestr()" class="section-title" href="#strcasestr()"><</a>
Vim doesn't have a strcasestr() function.  But you can add
"\c" to the pattern to ignore case:
```
:let idx = match(haystack, '\cneedle')

```

If {start} is given, the search starts from byte index
{start} in a String or item {start} in a [List](#List).
The result, however, is still the index counted from the
first character/item.  Example:
```
:echo match("testing", "ing", 2)

```
		result is again "4".
```
:echo match("testing", "ing", 4)

```
		result is again "4".
```
:echo match("testing", "t", 2)

```
		result is "3".
For a String, if {start} > 0 then it is like the string starts
{start} bytes later, thus "^" will match at {start}.  Except
when {count} is given, then it's like matches before the
{start} byte are ignored (this is a bit complicated to keep it
backwards compatible).
For a String, if {start} < 0, it will be set to 0.  For a list
the index is counted from the end.
If {start} is out of range ({start} > strlen({expr}) for a
String or {start} > len({expr}) for a [List](#List)) -1 is returned.

When {count} is given use the {count}'th match.  When a match
is found in a String the search for the next one starts one
character further.  Thus this example results in 1:
```
echo match("testing", "..", 0, 2)

```
		In a [List](#List) the search continues in the next item.
Note that when {count} is added the way {start} works changes,
see above.

See [pattern](#pattern) for the patterns that are accepted.
The 'ignorecase' option is used to set the ignore-caseness of
the pattern.  'smartcase' is NOT used.  The matching is always
done like 'magic' is set and 'cpoptions' is empty.
Note that a match at the start is preferred, thus when the
### <a id="pattern is using "" (any number of matches) it tends to find" class="section-title" href="#pattern is using "" (any number of matches) it tends to find">Note:</a>
zero matches at the start instead of a number of matches
further down in the text.

Can also be used as a [method](#method):
```
GetText()->match('word')
GetList()->match('word')

```

### <a id="matchadd() E798 E799 E801 E957" class="section-title" href="#matchadd() E798 E799 E801 E957">Note:</a>
matchadd({group}, {pattern} [, {priority} [, {id} [, {dict}]]])
Defines a pattern to be highlighted in the current window (a
"match").  It will be highlighted with {group}.  Returns an
identification number (ID), which can be used to delete the
match using [matchdelete()](#matchdelete()).  The ID is bound to the window.
Matching is case sensitive and magic, unless case sensitivity
or magicness are explicitly overridden in {pattern}.  The
'magic', 'smartcase' and 'ignorecase' options are not used.
The "Conceal" value is special, it causes the match to be
concealed.

The optional {priority} argument assigns a priority to the
match.  A match with a high priority will have its
highlighting overrule that of a match with a lower priority.
A priority is specified as an integer (negative numbers are no
exception).  If the {priority} argument is not specified, the
default priority is 10.  The priority of 'hlsearch' is zero,
hence all matches with a priority greater than zero will
overrule it.  Syntax highlighting (see 'syntax') is a separate
mechanism, and regardless of the chosen priority a match will
always overrule syntax highlighting.

The optional {id} argument allows the request for a specific
match ID.  If a specified ID is already taken, an error
message will appear and the match will not be added.  An ID
is specified as a positive integer (zero excluded).  IDs 1, 2
and 3 are reserved for [:match|, |:2match| and |:3match](#:match|, |:2match| and |:3match),
respectively.  3 is reserved for use by the [matchparen](#matchparen)
plugin.
If the {id} argument is not specified or -1, [matchadd()](#matchadd())
automatically chooses a free ID, which is at least 1000.

The optional {dict} argument allows for further custom
values. Currently this is used to specify a match specific
conceal character that will be shown for [hl-Conceal](#hl-Conceal)
highlighted matches. The dict can have the following members:

conceal	    Special character to show instead of the
match (only for [hl-Conceal](#hl-Conceal) highlighted
matches, see [:syn-cchar](#:syn-cchar))
window	    Instead of the current window use the
window with this number or window ID.

The number of matches is not limited, as it is the case with
the [:match](#:match) commands.

Returns -1 on error.

Example:
```
:highlight MyGroup ctermbg=green guibg=green
:let m = matchadd("MyGroup", "TODO")

```
		Deletion of the pattern:
```
:call matchdelete(m)


```
		A list of matches defined by [matchadd()| and |:match](#matchadd()| and |:match) are
available from [getmatches()](#getmatches()).  All matches can be deleted in
one operation by [clearmatches()](#clearmatches()).

Can also be used as a [method](#method):
```
GetGroup()->matchadd('TODO')

```

### <a id="matchaddpos()" class="section-title" href="#matchaddpos()">Note:</a>
matchaddpos({group}, {pos} [, {priority} [, {id} [, {dict}]]])
Same as [matchadd()](#matchadd()), but requires a list of positions {pos}
instead of a pattern. This command is faster than [matchadd()](#matchadd())
because it does not require to handle regular expressions and
sets buffer line boundaries to redraw screen. It is supposed
to be used when fast match additions and deletions are
required, for example to highlight matching parentheses.
### <a id="E5030 E5031" class="section-title" href="#E5030 E5031">Note:</a>
{pos} is a list of positions.  Each position can be one of
these:
- A number.  This whole line will be highlighted.  The first
line has number 1.
- A list with one number, e.g., [23]. The whole line with this
number will be highlighted.
- A list with two numbers, e.g., [23, 11]. The first number is
the line number, the second one is the column number (first
column is 1, the value must correspond to the byte index as
[col()](#col()) would return).  The character at this position will
be highlighted.
- A list with three numbers, e.g., [23, 11, 3]. As above, but
the third number gives the length of the highlight in bytes.

Entries with zero and negative line numbers are silently
ignored, as well as entries with negative column numbers and
lengths.

Returns -1 on error.

Example:
```
:highlight MyGroup ctermbg=green guibg=green
:let m = matchaddpos("MyGroup", [[23, 24], 34])

```
		Deletion of the pattern:
```
:call matchdelete(m)


```
		Matches added by [matchaddpos()](#matchaddpos()) are returned by
[getmatches()](#getmatches()).

Can also be used as a [method](#method):
```
GetGroup()->matchaddpos([23, 11])

### <a id="matcharg()" class="section-title" href="#matcharg()">matcharg({nr})</a>
Selects the {nr} match item, as set with a [:match](#:match),
[:2match| or |:3match](#:2match| or |:3match) command.
Return a [List](#List) with two elements:
The name of the highlight group used
The pattern used.
When {nr} is not 1, 2 or 3 returns an empty [List](#List).
When there is no match item set returns ['', ''].
This is useful to save and restore a [:match](#:match).
Highlighting matches using the [:match](#:match) commands are limited
to three matches. [matchadd()](#matchadd()) does not have this limitation.

Can also be used as a [method](#method):
```
GetMatch()->matcharg()

### <a id="matchdelete() E802 E803" class="section-title" href="#matchdelete() E802 E803">matchdelete({id} [, {win}])</a>
Deletes a match with ID {id} previously defined by [matchadd()](#matchadd())
or one of the [:match](#:match) commands.  Returns 0 if successful,
otherwise -1.  See example for [matchadd()](#matchadd()).  All matches can
be deleted in one operation by [clearmatches()](#clearmatches()).
If {win} is specified, use the window with this number or
window ID instead of the current window.

Can also be used as a [method](#method):
```
GetMatch()->matchdelete()

### <a id="matchend()" class="section-title" href="#matchend()">matchend({expr}, {pat} [, {start} [, {count}]])</a>
Same as [match()](#match()), but return the index of first character
after the match.  Example:
```
:echo matchend("testing", "ing")

```
		results in "7".
### <a id="strspn() strcspn()" class="section-title" href="#strspn() strcspn()">Note:</a>
Vim doesn't have a strspn() or strcspn() function, but you can
do it with matchend():
```
:let span = matchend(line, '[a-zA-Z]')
:let span = matchend(line, '[^a-zA-Z]')

```
		Except that -1 is returned when there are no matches.

The {start}, if given, has the same meaning as for [match()](#match()).
```
:echo matchend("testing", "ing", 2)

```
		results in "7".
```
:echo matchend("testing", "ing", 5)

```
		result is "-1".
When {expr} is a [List| the result is equal to |match()](#List| the result is equal to |match()).

Can also be used as a [method](#method):
```
GetText()->matchend('word')

### <a id="matchfuzzy()" class="section-title" href="#matchfuzzy()">matchfuzzy({list}, {str} [, {dict}])</a>
If {list} is a list of strings, then returns a [List](#List) with all
the strings in {list} that fuzzy match {str}. The strings in
the returned list are sorted based on the matching score.

The optional {dict} argument always supports the following
items:
matchseq	When this item is present return only matches
that contain the characters in {str} in the
given sequence.
limit	Maximum number of matches in {list} to be
returned.  Zero means no limit.

If {list} is a list of dictionaries, then the optional {dict}
argument supports the following additional items:
key		Key of the item which is fuzzy matched against
{str}. The value of this item should be a
string.
text_cb	[Funcref](#Funcref) that will be called for every item
in {list} to get the text for fuzzy matching.
This should accept a dictionary item as the
argument and return the text for that item to
use for fuzzy matching.

{str} is treated as a literal string and regular expression
matching is NOT supported.  The maximum supported {str} length
is 256.

When {str} has multiple words each separated by white space,
then the list of strings that have all the words is returned.

If there are no matching strings or there is an error, then an
empty list is returned. If length of {str} is greater than
256, then returns an empty list.

When {limit} is given, matchfuzzy() will find up to this
number of matches in {list} and return them in sorted order.

Refer to [fuzzy-matching](#fuzzy-matching) for more information about fuzzy
matching strings.

Example:
```
:echo matchfuzzy(["clay", "crow"], "cay")

```
		results in ["clay"].
```
:echo getbufinfo()->map({_, v -> v.name})->matchfuzzy("ndl")

```
		results in a list of buffer names fuzzy matching "ndl".
```
:echo getbufinfo()->matchfuzzy("ndl", {'key' : 'name'})

```
		results in a list of buffer information dicts with buffer
names fuzzy matching "ndl".
```
:echo getbufinfo()->matchfuzzy("spl",
\ {'text_cb' : {v -> v.name}})

```
		results in a list of buffer information dicts with buffer
names fuzzy matching "spl".
```
:echo v:oldfiles->matchfuzzy("test")

```
		results in a list of file names fuzzy matching "test".
```
:let l = readfile("buffer.c")->matchfuzzy("str")

```
		results in a list of lines in "buffer.c" fuzzy matching "str".
```
:echo ['one two', 'two one']->matchfuzzy('two one')

```
		results in ['two one', 'one two'].
```
:echo ['one two', 'two one']->matchfuzzy('two one',
\ {'matchseq': 1})

```
		results in ['two one'].

### <a id="matchfuzzypos()" class="section-title" href="#matchfuzzypos()">matchfuzzypos({list}, {str} [, {dict}])</a>
Same as [matchfuzzy()](#matchfuzzy()), but returns the list of matched
strings, the list of character positions where characters
in {str} matches and a list of matching scores.  You can
use [byteidx()](#byteidx()) to convert a character position to a byte
position.

If {str} matches multiple times in a string, then only the
positions for the best match is returned.

If there are no matching strings or there is an error, then a
list with three empty list items is returned.

Example:
```
:echo matchfuzzypos(['testing'], 'tsg')

```
		results in [["testing"], [[0, 2, 6]], [99]]
```
:echo matchfuzzypos(['clay', 'lacy'], 'la')

```
		results in [["lacy", "clay"], [[0, 1], [1, 2]], [153, 133]]
```
:echo [{'text': 'hello', 'id' : 10}]
\ ->matchfuzzypos('ll', {'key' : 'text'})

```
		results in [[{"id": 10, "text": "hello"}], [[2, 3]], [127]]

### <a id="matchlist()" class="section-title" href="#matchlist()">matchlist({expr}, {pat} [, {start} [, {count}]])</a>
Same as [match()|, but return a |List](#match()|, but return a |List).  The first item in the
list is the matched string, same as what matchstr() would
return.  Following items are submatches, like "\1", "\2", etc.
in [:substitute](#:substitute).  When an optional submatch didn't match an
empty string is used.  Example:
```
### <a id="echo matchlist('acd', '\(a\)\?\(b\)\?\(c\)\?\(.\)')" class="section-title" href="#echo matchlist('acd', '\(a\)\?\(b\)\?\(c\)\?\(.\)')">Note:</a>

```
		Results in: ['acd', 'a', '', 'c', 'd', '', '', '', '', '']
When there is no match an empty list is returned.

You can pass in a List, but that is not very useful.

Can also be used as a [method](#method):
```
GetText()->matchlist('word')

### <a id="matchstr()" class="section-title" href="#matchstr()">matchstr({expr}, {pat} [, {start} [, {count}]])</a>
Same as [match()](#match()), but return the matched string.  Example:
```
:echo matchstr("testing", "ing")

```
		results in "ing".
When there is no match "" is returned.
The {start}, if given, has the same meaning as for [match()](#match()).
```
:echo matchstr("testing", "ing", 2)

```
		results in "ing".
```
:echo matchstr("testing", "ing", 5)

```
		result is "".
When {expr} is a [List](#List) then the matching item is returned.
The type isn't changed, it's not necessarily a String.

Can also be used as a [method](#method):
```
GetText()->matchstr('word')

### <a id="matchstrpos()" class="section-title" href="#matchstrpos()">matchstrpos({expr}, {pat} [, {start} [, {count}]])</a>
Same as [matchstr()](#matchstr()), but return the matched string, the start
position and the end position of the match.  Example:
```
:echo matchstrpos("testing", "ing")

```
		results in ["ing", 4, 7].
When there is no match ["", -1, -1] is returned.
The {start}, if given, has the same meaning as for [match()](#match()).
```
:echo matchstrpos("testing", "ing", 2)

```
		results in ["ing", 4, 7].
```
:echo matchstrpos("testing", "ing", 5)

```
		result is ["", -1, -1].
When {expr} is a [List](#List) then the matching item, the index
of first item where {pat} matches, the start position and the
end position of the match are returned.
```
:echo matchstrpos([1, '__x'], '\a')

```
		result is ["x", 1, 2, 3].
The type isn't changed, it's not necessarily a String.

Can also be used as a [method](#method):
```
GetText()->matchstrpos('word')

```


### <a id="max()" class="section-title" href="#max()">Note:</a>
max({expr})	Return the maximum value of all items in {expr}. Example:
```
echo max([apples, pears, oranges])


```
		{expr} can be a [List| or a |Dictionary](#List| or a |Dictionary).  For a Dictionary,
it returns the maximum of all values in the Dictionary.
If {expr} is neither a List nor a Dictionary, or one of the
items in {expr} cannot be used as a Number this results in
an error.  An empty [List| or |Dictionary](#List| or |Dictionary) results in zero.

Can also be used as a [method](#method):
```
mylist->max()


### <a id="menu_get()" class="section-title" href="#menu_get()">menu_get({path} [, {modes}])</a>
Returns a [List| of |Dictionaries| describing |menus](#List| of |Dictionaries| describing |menus) (defined
by [:menu|, |:amenu|, …), including |hidden-menus](#:menu|, |:amenu|, …), including |hidden-menus).

{path} matches a menu by name, or all menus if {path} is an
empty string.  Example:
```
:echo menu_get('File','')
:echo menu_get('')

```

{modes} is a string of zero or more modes (see [maparg()](#maparg()) or
[creating-menus](#creating-menus) for the list of modes). "a" means "all".

Example:
```
nnoremenu &Test.Test inormal
inoremenu Test.Test insert
vnoremenu Test.Test x
echo menu_get("")


```
		returns something like this:
```

[ {
"hidden": 0,
"name": "Test",
"priority": 500,
"shortcut": 84,
"submenus": [ {
"hidden": 0,
"mappings": {
i": {
"enabled": 1,
"noremap": 1,
"rhs": "insert",
"sid": 1,
"silent": 0
},
n": { ... },
s": { ... },
v": { ... }
},
"name": "Test",
"priority": 500,
"shortcut": 0
} ]
} ]

```


### <a id="menu_info()" class="section-title" href="#menu_info()">menu_info({name} [, {mode}])</a>
Return information about the specified menu {name} in
mode {mode}. The menu name should be specified without the
shortcut character ('&'). If {name} is "", then the top-level
menu names are returned.

{mode} can be one of these strings:
"n"	Normal
"v"	Visual (including Select)
"o"	Operator-pending
"i"	Insert
"c"	Cmd-line
"s"	Select
"x"	Visual
"t"	Terminal-Job
""	Normal, Visual and Operator-pending
"!"	Insert and Cmd-line
When {mode} is omitted, the modes for "" are used.

Returns a [Dictionary](#Dictionary) containing the following items:
accel		menu item accelerator text [menu-text](#menu-text)
display	display name (name without '&')
enabled	v:true if this menu item is enabled
Refer to [:menu-enable](#:menu-enable)
icon		name of the icon file (for toolbar)
[toolbar-icon](#toolbar-icon)
iconidx	index of a built-in icon
modes		modes for which the menu is defined. In
addition to the modes mentioned above, these
characters will be used:
" "	Normal, Visual and Operator-pending
name		menu item name.
noremenu	v:true if the {rhs} of the menu item is not
remappable else v:false.
priority	menu order priority [menu-priority](#menu-priority)
rhs		right-hand-side of the menu item. The returned
string has special characters translated like
in the output of the ":menu" command listing.
When the {rhs} of a menu item is empty, then
"<Nop>" is returned.
script	v:true if script-local remapping of {rhs} is
allowed else v:false.  See [:menu-script](#:menu-script).
shortcut	shortcut key (character after '&' in
the menu name) [menu-shortcut](#menu-shortcut)
silent	v:true if the menu item is created
with <silent> argument [:menu-silent](#:menu-silent)
submenus	[List](#List) containing the names of
all the submenus.  Present only if the menu
item has submenus.

Returns an empty dictionary if the menu item is not found.

Examples:
```
:echo menu_info('Edit.Cut')
:echo menu_info('File.Save', 'n')

" Display the entire menu hierarchy in a buffer
func ShowMenu(name, pfx)
let m = menu_info(a:name)
call append(line('$'), a:pfx .. m.display)
for child in m->get('submenus', [])
call ShowMenu(a:name .. '.' .. escape(child, '.'),
\ a:pfx .. '    ')
endfor
endfunc
new
for topmenu in menu_info('').submenus
call ShowMenu(topmenu, '')
endfor

```

Can also be used as a [method](#method):
```
GetMenuName()->menu_info('v')


### <a id="min()" class="section-title" href="#min()"><</a>
min({expr})	Return the minimum value of all items in {expr}. Example:
```
echo min([apples, pears, oranges])


```
		{expr} can be a [List| or a |Dictionary](#List| or a |Dictionary).  For a Dictionary,
it returns the minimum of all values in the Dictionary.
If {expr} is neither a List nor a Dictionary, or one of the
items in {expr} cannot be used as a Number this results in
an error.  An empty [List| or |Dictionary](#List| or |Dictionary) results in zero.

Can also be used as a [method](#method):
```
mylist->min()

### <a id="mkdir() E739" class="section-title" href="#mkdir() E739"><</a>
mkdir({name} [, {path} [, {prot}]])
Create directory {name}.

If {path} is "p" then intermediate directories are created as
necessary.  Otherwise it must be "".

If {prot} is given it is used to set the protection bits of
the new directory.  The default is 0o755 (rwxr-xr-x: r/w for
the user, readable for others).  Use 0o700 to make it
unreadable for others.

{prot} is applied for all parts of {name}.  Thus if you create
/tmp/foo/bar then /tmp/foo will be created with 0o700. Example:
```
:call mkdir($HOME .. "/tmp/foo/bar", "p", 0o700)


```
		This function is not available in the [sandbox](#sandbox).

If you try to create an existing directory with {path} set to
"p" mkdir() will silently exit.

The function result is a Number, which is TRUE if the call was
successful or FALSE if the directory creation failed or partly
failed.

Can also be used as a [method](#method):
```
GetName()->mkdir()

```

### <a id="mode()" class="section-title" href="#mode()">Note:</a>
mode([expr])	Return a string that indicates the current mode.
If [expr] is supplied and it evaluates to a non-zero Number or
a non-empty String ([non-zero-arg](#non-zero-arg)), then the full mode is
returned, otherwise only the first letter is returned.

n	    Normal
no	    Operator-pending
nov	    Operator-pending (forced charwise [o_v](#o_v))
noV	    Operator-pending (forced linewise [o_V](#o_V))
noCTRL-V Operator-pending (forced blockwise [o_CTRL-V](#o_CTRL-V))
CTRL-V is one character
niI	    Normal using [i_CTRL-O| in |Insert-mode](#i_CTRL-O| in |Insert-mode)
niR	    Normal using [i_CTRL-O| in |Replace-mode](#i_CTRL-O| in |Replace-mode)
niV	    Normal using [i_CTRL-O| in |Virtual-Replace-mode](#i_CTRL-O| in |Virtual-Replace-mode)
nt	    Normal in [terminal-emulator](#terminal-emulator) (insert goes to
Terminal mode)
ntT	    Normal using [t_CTRL-\_CTRL-O| in |Terminal-mode](#t_CTRL-\_CTRL-O| in |Terminal-mode)
v	    Visual by character
vs	    Visual by character using [v_CTRL-O](#v_CTRL-O) in Select mode
V	    Visual by line
Vs	    Visual by line using [v_CTRL-O](#v_CTRL-O) in Select mode
CTRL-V   Visual blockwise
CTRL-Vs  Visual blockwise using [v_CTRL-O](#v_CTRL-O) in Select mode
s	    Select by character
S	    Select by line
CTRL-S   Select blockwise
i	    Insert
ic	    Insert mode completion [compl-generic](#compl-generic)
ix	    Insert mode [i_CTRL-X](#i_CTRL-X) completion
R	    Replace [R](#R)
Rc	    Replace mode completion [compl-generic](#compl-generic)
Rx	    Replace mode [i_CTRL-X](#i_CTRL-X) completion
Rv	    Virtual Replace [gR](#gR)
Rvc	    Virtual Replace mode completion [compl-generic](#compl-generic)
Rvx	    Virtual Replace mode [i_CTRL-X](#i_CTRL-X) completion
c	    Command-line editing
cv	    Vim Ex mode [gQ](#gQ)
r	    Hit-enter prompt
rm	    The -- more -- prompt
r?	    A [:confirm](#:confirm) query of some sort
!	    Shell or external command is executing
t	    Terminal mode: keys go to the job

This is useful in the 'statusline' option or RPC calls. In
most other places it always returns "c" or "n".
Note that in the future more modes and more specific modes may
be added. It's better not to compare the whole string but only
the leading character(s).
Also see [visualmode()](#visualmode()).

Can also be used as a [method](#method):
```
DoFull()->mode()

### <a id="msgpackdump()" class="section-title" href="#msgpackdump()">msgpackdump({list} [, {type}])</a>
Convert a list of VimL objects to msgpack. Returned value is a
[readfile()|-style list. When {type} contains "B", a |Blob](#readfile()|-style list. When {type} contains "B", a |Blob) is
returned instead. Example:
```
call writefile(msgpackdump([{}]), 'fname.mpack', 'b')

```
		or, using a [Blob](#Blob):
```
call writefile(msgpackdump([{}], 'B'), 'fname.mpack')

```

This will write the single 0x80 byte to a `fname.mpack` file
(dictionary with zero items is represented by 0x80 byte in
messagepack).

Limitations:				*E5004* *E5005*
1. [Funcref](#Funcref)s cannot be dumped.
2. Containers that reference themselves cannot be dumped.
3. Dictionary keys are always dumped as STR strings.
4. Other strings and [Blob](#Blob)s are always dumped as BIN strings.
5. Points 3. and 4. do not apply to [msgpack-special-dict](#msgpack-special-dict)s.

### <a id="msgpackparse()" class="section-title" href="#msgpackparse()">msgpackparse({data})</a>
Convert a [readfile()|-style list or a |Blob](#readfile()|-style list or a |Blob) to a list of
VimL objects.
Example:
```
let fname = expand('~/.config/nvim/shada/main.shada')
let mpack = readfile(fname, 'b')
let shada_objects = msgpackparse(mpack)

```
		This will read ~/.config/nvim/shada/main.shada file to
`shada_objects` list.

Limitations:
1. Mapping ordering is not preserved unless messagepack
mapping is dumped using generic mapping
([msgpack-special-map](#msgpack-special-map)).
2. Since the parser aims to preserve all data untouched
(except for 1.) some strings are parsed to
[msgpack-special-dict](#msgpack-special-dict) format which is not convenient to
use.
### <a id="msgpack-special-dict" class="section-title" href="#msgpack-special-dict">Note:</a>
Some messagepack strings may be parsed to special
dictionaries. Special dictionaries are dictionaries which

1. Contain exactly two keys: `_TYPE` and `_VAL`.
2. `_TYPE` key is one of the types found in [v:msgpack_types](#v:msgpack_types)
variable.
3. Value for `_VAL` has the following format (Key column
contains name of the key from [v:msgpack_types](#v:msgpack_types)):

Key	Value ~
nil	Zero, ignored when dumping.  Not returned by
[msgpackparse()| since |v:null](#msgpackparse()| since |v:null) was introduced.
boolean	One or zero.  When dumping it is only checked that
value is a [Number|.  Not returned by |msgpackparse()](#Number|.  Not returned by |msgpackparse())
since [v:true| and |v:false](#v:true| and |v:false) were introduced.
integer	[List](#List) with four numbers: sign (-1 or 1), highest two
bits, number with bits from 62nd to 31st, lowest 31
bits. I.e. to get actual number one will need to use
code like
```
### <a id="_VAL[0]  ((_VAL[1] << 62)" class="section-title" href="#_VAL[0]  ((_VAL[1] << 62)">Note:</a>
& (_VAL[2] << 31)
& _VAL[3])

```
			Special dictionary with this type will appear in
[msgpackparse()](#msgpackparse()) output under one of the following
circumstances:
1. [Number](#Number) is 32-bit and value is either above
INT32_MAX or below INT32_MIN.
2. [Number](#Number) is 64-bit and value is above INT64_MAX. It
cannot possibly be below INT64_MIN because msgpack
C parser does not support such values.
float	[Float](#Float). This value cannot possibly appear in
[msgpackparse()](#msgpackparse()) output.
string	[readfile()](#readfile())-style list of strings. This value will
appear in [msgpackparse()](#msgpackparse()) output if string contains
zero byte or if string is a mapping key and mapping is
being represented as special dictionary for other
reasons.
binary	[String|, or |Blob](#String|, or |Blob) if binary string contains zero
byte. This value cannot appear in [msgpackparse()](#msgpackparse())
output since blobs were introduced.
array	[List|. This value cannot appear in |msgpackparse()](#List|. This value cannot appear in |msgpackparse())
output.
### <a id="msgpack-special-map" class="section-title" href="#msgpack-special-map">Note:</a>
map	[List| of |List](#List| of |List)s with two items (key and value) each.
This value will appear in [msgpackparse()](#msgpackparse()) output if
parsed mapping contains one of the following keys:
1. Any key that is not a string (including keys which
are binary strings).
2. String with NUL byte inside.
3. Duplicate key.
4. Empty key.
ext	[List](#List) with two values: first is a signed integer
representing extension type. Second is
[readfile()](#readfile())-style list of strings.

### <a id="nextnonblank()" class="section-title" href="#nextnonblank()">nextnonblank({lnum})</a>
Return the line number of the first line at or below {lnum}
that is not blank.  Example:
```
if getline(nextnonblank(1)) =~ "Java"

```
		When {lnum} is invalid or there is no non-blank line at or
below it, zero is returned.
{lnum} is used like with [getline()](#getline()).
See also [prevnonblank()](#prevnonblank()).

Can also be used as a [method](#method):
```
GetLnum()->nextnonblank()

### <a id="nr2char()" class="section-title" href="#nr2char()">nr2char({expr} [, {utf8}])</a>
Return a string with a single character, which has the number
value {expr}.  Examples:
```
nr2char(64)		returns "@"
nr2char(32)		returns " "

```
		Example for "utf-8":
```
nr2char(300)		returns I with bow character

```
		UTF-8 encoding is always used, {utf8} option has no effect,
and exists only for backwards-compatibility.
Note that a NUL character in the file is specified with
nr2char(10), because NULs are represented with newline
characters.  nr2char(0) is a real NUL and terminates the
string, thus results in an empty string.

Can also be used as a [method](#method):
```
GetNumber()->nr2char()

### <a id="E5555 nvim_...() eval-api" class="section-title" href="#E5555 nvim_...() eval-api">nvim_...({...})</a>
Call nvim [api](#api) functions. The type checking of arguments will
be stricter than for most other builtins. For instance,
if Integer is expected, a [Number](#Number) must be passed in, a
[String](#String) will not be autoconverted.
Buffer numbers, as returned by [bufnr()](#bufnr()) could be used as
first argument to nvim_buf_... functions.  All functions
expecting an object (buffer, window or tabpage) can
also take the numerical value 0 to indicate the current
(focused) object.

### <a id="or()" class="section-title" href="#or()">or({expr}, {expr})</a>
Bitwise OR on the two arguments.  The arguments are converted
to a number.  A List, Dict or Float argument causes an error.
Also see `and()` and `xor()`.
Example:
```
:let bits = or(bits, 0x80)

```
		Can also be used as a [method](#method):
```
:let bits = bits->or(0x80)


```
		Rationale: The reason this is a function and not using the "|"
character like many languages, is that Vi has always used "|"
to separate commands.  In many places it would not be clear if
"|" is an operator or a command separator.


### <a id="pathshorten()" class="section-title" href="#pathshorten()">pathshorten({path} [, {len}])</a>
Shorten directory names in the path {path} and return the
result.  The tail, the file name, is kept as-is.  The other
components in the path are reduced to {len} letters in length.
If {len} is omitted or smaller than 1 then 1 is used (single
letters).  Leading '~' and '.' characters are kept.  Examples:
```
:echo pathshorten('~/.config/nvim/autoload/file1.vim')

```
			~/.c/n/a/file1.vim ~
```
:echo pathshorten('~/.config/nvim/autoload/file2.vim', 2)

```
			~/.co/nv/au/file2.vim ~
It doesn't matter if the path exists or not.
Returns an empty string on error.

Can also be used as a [method](#method):
```
GetDirectories()->pathshorten()

### <a id="perleval()" class="section-title" href="#perleval()">perleval({expr})</a>
Evaluate [perl](#perl) expression {expr} and return its result
converted to Vim data structures.
Numbers and strings are returned as they are (strings are
copied though).
Lists are represented as Vim [List](#List) type.
Dictionaries are represented as Vim [Dictionary](#Dictionary) type,
non-string keys result in error.

Note: If you want an array or hash, {expr} must return a
reference to it.
Example:
```
:echo perleval('[1 .. 4]')

```
			[1, 2, 3, 4]

Can also be used as a [method](#method):
```
GetExpr()->perleval()

### <a id="pow()" class="section-title" href="#pow()">pow({x}, {y})</a>
Return the power of {x} to the exponent {y} as a [Float](#Float).
{x} and {y} must evaluate to a [Float| or a |Number](#Float| or a |Number).
Returns 0.0 if {x} or {y} is not a [Float| or a |Number](#Float| or a |Number).
Examples:
```
:echo pow(3, 3)

```
			27.0
```
:echo pow(2, 16)

```
			65536.0
```
:echo pow(32, 0.20)

```
			2.0

Can also be used as a [method](#method):
```
Compute()->pow(3)

### <a id="prevnonblank()" class="section-title" href="#prevnonblank()">prevnonblank({lnum})</a>
Return the line number of the first line at or above {lnum}
that is not blank.  Example:
```
let ind = indent(prevnonblank(v:lnum - 1))

```
		When {lnum} is invalid or there is no non-blank line at or
above it, zero is returned.
{lnum} is used like with [getline()](#getline()).
Also see [nextnonblank()](#nextnonblank()).

Can also be used as a [method](#method):
```
GetLnum()->prevnonblank()

### <a id="printf()" class="section-title" href="#printf()">printf({fmt}, {expr1} ...)</a>
Return a String with {fmt}, where "%" items are replaced by
the formatted form of their respective arguments.  Example:
```
printf("%4d: E%d %.30s", lnum, errno, msg)

```
		May result in:
"  99: E42 asdfasdfasdfasdfasdfasdfasdfas" ~

When used as a [method](#method) the base is passed as the second
argument:
```
Compute()->printf("result: %d")

```

You can use `call()` to pass the items as a list.

Often used items are:
%s	string
%6S	string right-aligned in 6 display cells
%6s	string right-aligned in 6 bytes
%.9s	string truncated to 9 bytes
%c	single byte
%d	decimal number
%5d	decimal number padded with spaces to 5 characters
%b	binary number
%08b	binary number padded with zeros to at least 8 characters
%B	binary number using upper case letters
%x	hex number
%04x	hex number padded with zeros to at least 4 characters
%X	hex number using upper case letters
%o	octal number
%f	floating point number as 12.23, inf, -inf or nan
%F	floating point number as 12.23, INF, -INF or NAN
%e	floating point number as 1.23e3, inf, -inf or nan
%E	floating point number as 1.23E3, INF, -INF or NAN
%g	floating point number, as %f or %e depending on value
%G	floating point number, as %F or %E depending on value
%%	the % character itself
%p	representation of the pointer to the container

Conversion specifications start with '%' and end with the
conversion type.  All other characters are copied unchanged to
the result.

The "%" starts a conversion specification.  The following
arguments appear in sequence:

%  [flags]  [field-width]  [.precision]  type

flags
Zero or more of the following flags:

#	      The value should be converted to an "alternate
form".  For c, d, and s conversions, this option
has no effect.  For o conversions, the precision
of the number is increased to force the first
character of the output string to a zero (except
if a zero value is printed with an explicit
precision of zero).
For x and X conversions, a non-zero result has
the string "0x" (or "0X" for X conversions)
prepended to it.

0 (zero)  Zero padding.  For all conversions the converted
value is padded on the left with zeros rather
than blanks.  If a precision is given with a
numeric conversion (d, o, x, and X), the 0 flag
is ignored.

-	      A negative field width flag; the converted value
is to be left adjusted on the field boundary.
The converted value is padded on the right with
blanks, rather than on the left with blanks or
zeros.  A - overrides a 0 if both are given.

' ' (space)  A blank should be left before a positive
number produced by a signed conversion (d).

+	      A sign must always be placed before a number
produced by a signed conversion.  A + overrides
a space if both are used.

field-width
An optional decimal digit string specifying a minimum
field width.  If the converted value has fewer bytes
than the field width, it will be padded with spaces on
the left (or right, if the left-adjustment flag has
been given) to fill out the field width.  For the S
conversion the count is in cells.

.precision
An optional precision, in the form of a period '.'
followed by an optional digit string.  If the digit
string is omitted, the precision is taken as zero.
This gives the minimum number of digits to appear for
d, o, x, and X conversions, the maximum number of
bytes to be printed from a string for s conversions,
or the maximum number of cells to be printed from a
string for S conversions.
For floating point it is the number of digits after
the decimal point.

type
A character that specifies the type of conversion to
be applied, see below.

A field width or precision, or both, may be indicated by an
### <a id="asterisk '' instead of a digit string." class="section-title" href="#asterisk '' instead of a digit string.">Note:</a>
Number argument supplies the field width or precision.  A
negative field width is treated as a left adjustment flag
followed by a positive field width; a negative precision is
treated as though it were missing.  Example:
```
### <a id=":echo printf("%d: %.s", nr, width, line)" class="section-title" href="#:echo printf("%d: %.s", nr, width, line)">Note:</a>

```
		This limits the length of the text used from "line" to
"width" bytes.

The conversion specifiers and their meanings are:

### <a id="printf-d printf-b printf-B printf-o printf-x printf-X" class="section-title" href="#printf-d printf-b printf-B printf-o printf-x printf-X">Note:</a>
dbBoxX	The Number argument is converted to signed decimal (d),
unsigned binary (b and B), unsigned octal (o), or
unsigned hexadecimal (x and X) notation.  The letters
"abcdef" are used for x conversions; the letters
"ABCDEF" are used for X conversions.  The precision, if
any, gives the minimum number of digits that must
appear; if the converted value requires fewer digits, it
is padded on the left with zeros.  In no case does a
non-existent or small field width cause truncation of a
numeric field; if the result of a conversion is wider
than the field width, the field is expanded to contain
the conversion result.
The 'h' modifier indicates the argument is 16 bits.
The 'l' modifier indicates the argument is 32 bits.
The 'L' modifier indicates the argument is 64 bits.
Generally, these modifiers are not useful. They are
ignored when type is known from the argument.

i	alias for d
D	alias for ld
U	alias for lu
O	alias for lo

### <a id="printf-c" class="section-title" href="#printf-c">Note:</a>
c	The Number argument is converted to a byte, and the
resulting character is written.

### <a id="printf-s" class="section-title" href="#printf-s">Note:</a>
s	The text of the String argument is used.  If a
precision is specified, no more bytes than the number
specified are used.
If the argument is not a String type, it is
automatically converted to text with the same format
as ":echo".
### <a id="printf-S" class="section-title" href="#printf-S">Note:</a>
S	The text of the String argument is used.  If a
precision is specified, no more display cells than the
number specified are used.

### <a id="printf-f E807" class="section-title" href="#printf-f E807">Note:</a>
f F	The Float argument is converted into a string of the
form 123.456.  The precision specifies the number of
digits after the decimal point.  When the precision is
zero the decimal point is omitted.  When the precision
is not specified 6 is used.  A really big number
(out of range or dividing by zero) results in "inf"
or "-inf" with %f (INF or -INF with %F).
"0.0 / 0.0" results in "nan" with %f (NAN with %F).
Example:
```
echo printf("%.2f", 12.115)

```
				12.12
Note that roundoff depends on the system libraries.
Use [round()](#round()) when in doubt.

### <a id="printf-e printf-E" class="section-title" href="#printf-e printf-E">Note:</a>
e E	The Float argument is converted into a string of the
form 1.234e+03 or 1.234E+03 when using 'E'.  The
precision specifies the number of digits after the
decimal point, like with 'f'.

### <a id="printf-g printf-G" class="section-title" href="#printf-g printf-G">Note:</a>
g G	The Float argument is converted like with 'f' if the
value is between 0.001 (inclusive) and 10000000.0
(exclusive).  Otherwise 'e' is used for 'g' and 'E'
for 'G'.  When no precision is specified superfluous
zeroes and '+' signs are removed, except for the zero
immediately after the decimal point.  Thus 10000000.0
results in 1.0e7.

### <a id="printf-%" class="section-title" href="#printf-%">Note:</a>
%	A '%' is written.  No argument is converted.  The
complete conversion specification is "%%".

When a Number argument is expected a String argument is also
accepted and automatically converted.
When a Float or String argument is expected a Number argument
is also accepted and automatically converted.
Any other argument type results in an error message.

### <a id="E766 E767" class="section-title" href="#E766 E767">Note:</a>
The number of {exprN} arguments must exactly match the number
of "%" items.  If there are not sufficient or too many
arguments an error is given.  Up to 18 arguments can be used.

### <a id="prompt_getprompt()" class="section-title" href="#prompt_getprompt()">prompt_getprompt({buf})</a>
Returns the effective prompt text for buffer {buf}.  {buf} can
be a buffer name or number.  See [prompt-buffer](#prompt-buffer).

If the buffer doesn't exist or isn't a prompt buffer, an empty
string is returned.

Can also be used as a [method](#method):
```
GetBuffer()->prompt_getprompt()

### <a id="prompt_setcallback()" class="section-title" href="#prompt_setcallback()">prompt_setcallback({buf}, {expr})</a>
Set prompt callback for buffer {buf} to {expr}.  When {expr}
is an empty string the callback is removed.  This has only
effect if {buf} has 'buftype' set to "prompt".

The callback is invoked when pressing Enter.  The current
buffer will always be the prompt buffer.  A new line for a
prompt is added before invoking the callback, thus the prompt
for which the callback was invoked will be in the last but one
line.
If the callback wants to add text to the buffer, it must
insert it above the last line, since that is where the current
prompt is.  This can also be done asynchronously.
The callback is invoked with one argument, which is the text
that was entered at the prompt.  This can be an empty string
if the user only typed Enter.
Example:
```
call prompt_setcallback(bufnr(''), function('s:TextEntered'))
func s:TextEntered(text)
if a:text == 'exit' || a:text == 'quit'
stopinsert
close
else
call append(line('$') - 1, 'Entered: "' .. a:text .. '"')
" Reset 'modified' to allow the buffer to be closed.
set nomodified
endif
endfunc


```
		Can also be used as a [method](#method):
```
GetBuffer()->prompt_setcallback(callback)

### <a id="prompt_setinterrupt()" class="section-title" href="#prompt_setinterrupt()">prompt_setinterrupt({buf}, {expr})</a>
Set a callback for buffer {buf} to {expr}.  When {expr} is an
empty string the callback is removed.  This has only effect if
{buf} has 'buftype' set to "prompt".

This callback will be invoked when pressing CTRL-C in Insert
mode.  Without setting a callback Vim will exit Insert mode,
as in any buffer.

Can also be used as a [method](#method):
```
GetBuffer()->prompt_setinterrupt(callback)

### <a id="prompt_setprompt()" class="section-title" href="#prompt_setprompt()">prompt_setprompt({buf}, {text})</a>
Set prompt for buffer {buf} to {text}.  You most likely want
{text} to end in a space.
The result is only visible if {buf} has 'buftype' set to
"prompt".  Example:
```
call prompt_setprompt(bufnr(''), 'command: ')

```

Can also be used as a [method](#method):
```
GetBuffer()->prompt_setprompt('command: ')

### <a id="pum_getpos()" class="section-title" href="#pum_getpos()">pum_getpos()</a>
If the popup menu (see [ins-completion-menu](#ins-completion-menu)) is not visible,
returns an empty [Dictionary](#Dictionary), otherwise, returns a
[Dictionary](#Dictionary) with the following keys:
height		nr of items visible
width		screen cells
row		top screen row (0 first row)
col		leftmost screen column (0 first col)
size		total nr of items
scrollbar	[TRUE](#TRUE) if scrollbar is visible

The values are the same as in [v:event| during |CompleteChanged](#v:event| during |CompleteChanged).

### <a id="pumvisible()" class="section-title" href="#pumvisible()">pumvisible()</a>
Returns non-zero when the popup menu is visible, zero
otherwise.  See [ins-completion-menu](#ins-completion-menu).
This can be used to avoid some things that would remove the
popup menu.

### <a id="py3eval()" class="section-title" href="#py3eval()">py3eval({expr})</a>
Evaluate Python expression {expr} and return its result
converted to Vim data structures.
Numbers and strings are returned as they are (strings are
copied though, Unicode strings are additionally converted to
UTF-8).
Lists are represented as Vim [List](#List) type.
Dictionaries are represented as Vim [Dictionary](#Dictionary) type with
keys converted to strings.

Can also be used as a [method](#method):
```
GetExpr()->py3eval()

```

### <a id="E858 E859" class="section-title" href="#E858 E859">Note:</a>
### <a id="pyeval()" class="section-title" href="#pyeval()">pyeval({expr})</a>
Evaluate Python expression {expr} and return its result
converted to Vim data structures.
Numbers and strings are returned as they are (strings are
copied though).
Lists are represented as Vim [List](#List) type.
Dictionaries are represented as Vim [Dictionary](#Dictionary) type,
non-string keys result in error.

Can also be used as a [method](#method):
```
GetExpr()->pyeval()

### <a id="pyxeval()" class="section-title" href="#pyxeval()">pyxeval({expr})</a>
Evaluate Python expression {expr} and return its result
converted to Vim data structures.
Uses Python 2 or 3, see [python_x](#python_x) and 'pyxversion'.
See also: [pyeval()|, |py3eval()](#pyeval()|, |py3eval())

Can also be used as a [method](#method):
```
GetExpr()->pyxeval()

```

### <a id="E726 E727" class="section-title" href="#E726 E727">Note:</a>
### <a id="range()" class="section-title" href="#range()">range({expr} [, {max} [, {stride}]])</a>
Returns a [List](#List) with Numbers:
- If only {expr} is specified: [0, 1, ..., {expr} - 1]
- If {max} is specified: [{expr}, {expr} + 1, ..., {max}]
- If {stride} is specified: [{expr}, {expr} + {stride}, ...,
{max}] (increasing {expr} with {stride} each time, not
producing a value past {max}).
When the maximum is one before the start the result is an
empty list.  When the maximum is more than one before the
start this is an error.
Examples:
```
range(4)		" [0, 1, 2, 3]
range(2, 4)		" [2, 3, 4]
range(2, 9, 3)		" [2, 5, 8]
range(2, -2, -1)	" [2, 1, 0, -1, -2]
range(0)		" []
range(2, 0)		" error!

```

Can also be used as a [method](#method):
```
GetExpr()->range()

```

### <a id="rand()" class="section-title" href="#rand()">rand([{expr}])</a>
### <a id="Return a pseudo-random Number generated with an xoshiro128" class="section-title" href="#Return a pseudo-random Number generated with an xoshiro128">Note:</a>
algorithm using seed {expr}.  The returned number is 32 bits,
also on 64 bits systems, for consistency.
{expr} can be initialized by [srand()](#srand()) and will be updated by
rand().  If {expr} is omitted, an internal seed value is used
and updated.
Returns -1 if {expr} is invalid.

Examples:
```
:echo rand()
:let seed = srand()
:echo rand(seed)
:echo rand(seed) % 16  " random number 0 - 15

```

Can also be used as a [method](#method):
```
seed->rand()

```

### <a id="readdir()" class="section-title" href="#readdir()">Note:</a>
readdir({directory} [, {expr}])
Return a list with file and directory names in {directory}.
You can also use [glob()](#glob()) if you don't need to do complicated
things, such as limiting the number of matches.

When {expr} is omitted all entries are included.
When {expr} is given, it is evaluated to check what to do:
If {expr} results in -1 then no further entries will
be handled.
If {expr} results in 0 then this entry will not be
added to the list.
If {expr} results in 1 then this entry will be added
to the list.
Each time {expr} is evaluated [v:val](#v:val) is set to the entry name.
When {expr} is a function the name is passed as the argument.
For example, to get a list of files ending in ".txt":
```
readdir(dirname, {n -> n =~ '.txt$'})

```
		To skip hidden and backup files:
```
readdir(dirname, {n -> n !~ '^\.\|\~$'})


```
		If you want to get a directory tree:
```
function! s:tree(dir)
return {a:dir : map(readdir(a:dir),
\ {_, x -> isdirectory(x) ?
\          {x : s:tree(a:dir .. '/' .. x)} : x})}
endfunction
echo s:tree(".")

```

Returns an empty List on error.

Can also be used as a [method](#method):
```
GetDirName()->readdir()

```

### <a id="readfile()" class="section-title" href="#readfile()">Note:</a>
readfile({fname} [, {type} [, {max}]])
Read file {fname} and return a [List](#List), each line of the file
as an item.  Lines are broken at NL characters.  Macintosh
files separated with CR will result in a single long line
(unless a NL appears somewhere).
All NUL characters are replaced with a NL character.
When {type} contains "b" binary mode is used:
- When the last line ends in a NL an extra empty list item is
added.
- No CR characters are removed.
When {type} contains "B" a [Blob](#Blob) is returned with the binary
data of the file unmodified.
Otherwise:
- CR characters that appear before a NL are removed.
- Whether the last line ends in a NL or not does not matter.
- Any UTF-8 byte order mark is removed from the text.
When {max} is given this specifies the maximum number of lines
to be read.  Useful if you only want to check the first ten
lines of a file:
```
:for line in readfile(fname, '', 10)
:  if line =~ 'Date' [ echo line ](# echo line ) endif
:endfor

```
		When {max} is negative -{max} lines from the end of the file
are returned, or as many as there are.
When {max} is zero the result is an empty list.
Note that without {max} the whole file is read into memory.
Also note that there is no recognition of encoding.  Read a
file into a buffer if you need to.
When the file can't be opened an error message is given and
the result is an empty list.
Also see [writefile()](#writefile()).

Can also be used as a [method](#method):
```
GetFileName()->readfile()

### <a id="reduce() E998" class="section-title" href="#reduce() E998">reduce({object}, {func} [, {initial}])</a>
{func} is called for every item in {object}, which can be a
[List| or a |Blob](#List| or a |Blob).  {func} is called with two arguments: the
result so far and current item.  After processing all items
the result is returned.

{initial} is the initial result.  When omitted, the first item
in {object} is used and {func} is first called for the second
item.  If {initial} is not given and {object} is empty no
result can be computed, an E998 error is given.

Examples:
```
echo reduce([1, 3, 5], { acc, val -> acc + val })
echo reduce(['x', 'y'], { acc, val -> acc .. val }, 'a')
### <a id="echo reduce(0z1122, { acc, val -> 2  acc + val })" class="section-title" href="#echo reduce(0z1122, { acc, val -> 2  acc + val })">Note:</a>

```

Can also be used as a [method](#method):
```
echo mylist->reduce({ acc, val -> acc + val }, 0)

### <a id="reg_executing()" class="section-title" href="#reg_executing()">reg_executing()</a>
Returns the single letter name of the register being executed.
Returns an empty string when no register is being executed.
See [@](#@).

### <a id="reg_recorded()" class="section-title" href="#reg_recorded()">reg_recorded()</a>
Returns the single letter name of the last recorded register.
Returns an empty string when nothing was recorded yet.
See [q| and |Q](#q| and |Q).

### <a id="reg_recording()" class="section-title" href="#reg_recording()">reg_recording()</a>
Returns the single letter name of the register being recorded.
Returns an empty string when not recording.  See [q](#q).

reltime()
reltime({start})
### <a id="reltime()" class="section-title" href="#reltime()">reltime({start}, {end})</a>
Return an item that represents a time value.  The item is a
list with items that depend on the system.
The item can be passed to [reltimestr()](#reltimestr()) to convert it to a
string or [reltimefloat()](#reltimefloat()) to convert to a Float.

Without an argument it returns the current "relative time", an
implementation-defined value meaningful only when used as an
argument to [reltime()|, |reltimestr()| and |reltimefloat()](#reltime()|, |reltimestr()| and |reltimefloat()).

With one argument it returns the time passed since the time
specified in the argument.
With two arguments it returns the time passed between {start}
and {end}.

The {start} and {end} arguments must be values returned by
reltime().  Returns zero on error.

Can also be used as a [method](#method):
```
GetStart()->reltime()

```

Note: [localtime()](#localtime()) returns the current (non-relative) time.

### <a id="reltimefloat()" class="section-title" href="#reltimefloat()">reltimefloat({time})</a>
Return a Float that represents the time value of {time}.
Unit of time is seconds.
Example:
let start = reltime()
call MyFunction()
let seconds = reltimefloat(reltime(start))
See the note of reltimestr() about overhead.
Also see [profiling](#profiling).
If there is an error an empty string is returned

Can also be used as a [method](#method):
```
reltime(start)->reltimefloat()

### <a id="reltimestr()" class="section-title" href="#reltimestr()">reltimestr({time})</a>
Return a String that represents the time value of {time}.
This is the number of seconds, a dot and the number of
microseconds.  Example:
```
let start = reltime()
call MyFunction()
echo reltimestr(reltime(start))

```
		Note that overhead for the commands will be added to the time.
Leading spaces are used to make the string align nicely.  You
can use split() to remove it.
```
echo split(reltimestr(reltime(start)))[0]

```
		Also see [profiling](#profiling).
If there is an error an empty string is returned

Can also be used as a [method](#method):
```
reltime(start)->reltimestr()

```

remove({list}, {idx})
### <a id="remove()" class="section-title" href="#remove()">remove({list}, {idx}, {end})</a>
Without {end}: Remove the item at {idx} from [List](#List) {list} and
return the item.
With {end}: Remove items from {idx} to {end} (inclusive) and
return a [List](#List) with these items.  When {idx} points to the same
item as {end} a list with one item is returned.  When {end}
points to an item before {idx} this is an error.
See [list-index](#list-index) for possible values of {idx} and {end}.
Returns zero on error.
Example:
```
:echo "last item: " .. remove(mylist, -1)
:call remove(mylist, 0, 9)

```

Use [delete()](#delete()) to remove a file.

Can also be used as a [method](#method):
```
mylist->remove(idx)

remove({blob}, {idx})
remove({blob}, {idx}, {end})
Without {end}: Remove the byte at {idx} from [Blob](#Blob) {blob} and
return the byte.
With {end}: Remove bytes from {idx} to {end} (inclusive) and
return a [Blob](#Blob) with these bytes.  When {idx} points to the same
byte as {end} a [Blob](#Blob) with one byte is returned.  When {end}
points to a byte before {idx} this is an error.
Returns zero on error.
Example:
```
:echo "last byte: " .. remove(myblob, -1)
:call remove(mylist, 0, 9)

remove({dict}, {key})
Remove the entry from {dict} with key {key} and return it.
Example:
```
:echo "removed " .. remove(dict, "one")

```
		If there is no {key} in {dict} this is an error.
Returns zero on error.

### <a id="rename()" class="section-title" href="#rename()">rename({from}, {to})</a>
Rename the file by the name {from} to the name {to}.  This
should also work to move files across file systems.  The
result is a Number, which is 0 if the file was renamed
successfully, and non-zero when the renaming failed.
NOTE: If {to} exists it is overwritten without warning.
This function is not available in the [sandbox](#sandbox).

Can also be used as a [method](#method):
```
GetOldName()->rename(newname)

### <a id="repeat()" class="section-title" href="#repeat()">repeat({expr}, {count})</a>
Repeat {expr} {count} times and return the concatenated
result.  Example:
```
:let separator = repeat('-', 80)

```
		When {count} is zero or negative the result is empty.
When {expr} is a [List](#List) the result is {expr} concatenated
{count} times.  Example:
```
:let longlist = repeat(['a', 'b'], 3)

```
		Results in ['a', 'b', 'a', 'b', 'a', 'b'].

Can also be used as a [method](#method):
```
mylist->repeat(count)

### <a id="resolve() E655" class="section-title" href="#resolve() E655">resolve({filename})</a>
On MS-Windows, when {filename} is a shortcut (a .lnk file),
returns the path the shortcut points to in a simplified form.
On Unix, repeat resolving symbolic links in all path
components of {filename} and return the simplified result.
To cope with link cycles, resolving of symbolic links is
stopped after 100 iterations.
On other systems, return the simplified {filename}.
The simplification step is done as by [simplify()](#simplify()).
resolve() keeps a leading path component specifying the
current directory (provided the result is still a relative
path name) and also keeps a trailing path separator.

Can also be used as a [method](#method):
```
GetName()->resolve()

```

### <a id="reverse()" class="section-title" href="#reverse()">Note:</a>
reverse({object})
Reverse the order of items in {object} in-place.
{object} can be a [List| or a |Blob](#List| or a |Blob).
Returns {object}.
Returns zero if {object} is not a List or a Blob.
If you want an object to remain unmodified make a copy first:
```
:let revlist = reverse(copy(mylist))

```
		Can also be used as a [method](#method):
```
mylist->reverse()

### <a id="round()" class="section-title" href="#round()">round({expr})</a>
Round off {expr} to the nearest integral value and return it
as a [Float](#Float).  If {expr} lies halfway between two integral
values, then use the larger one (away from zero).
{expr} must evaluate to a [Float| or a |Number](#Float| or a |Number).
Returns 0.0 if {expr} is not a [Float| or a |Number](#Float| or a |Number).
Examples:
```
echo round(0.456)

```
			0.0
```
echo round(4.5)

```
			5.0
```
echo round(-4.5)

```
			-5.0

Can also be used as a [method](#method):
```
Compute()->round()

### <a id="rpcnotify()" class="section-title" href="#rpcnotify()">rpcnotify({channel}, {event} [, {args}...])</a>
Sends {event} to {channel} via [RPC](#RPC) and returns immediately.
If {channel} is 0, the event is broadcast to all channels.
Example:
```
:au VimLeave call rpcnotify(0, "leaving")

### <a id="rpcrequest()" class="section-title" href="#rpcrequest()">rpcrequest({channel}, {method} [, {args}...])</a>
Sends a request to {channel} to invoke {method} via
[RPC](#RPC) and blocks until a response is received.
Example:
```
:let result = rpcrequest(rpc_chan, "func", 1, 2, 3)

### <a id="rpcstart()" class="section-title" href="#rpcstart()">rpcstart({prog} [, {argv}])</a>
Deprecated. Replace
```
:let id = rpcstart('prog', ['arg1', 'arg2'])

```
		with
```
:let id = jobstart(['prog', 'arg1', 'arg2'], {'rpc': v:true})

### <a id="rubyeval()" class="section-title" href="#rubyeval()">rubyeval({expr})</a>
Evaluate Ruby expression {expr} and return its result
converted to Vim data structures.
Numbers, floats and strings are returned as they are (strings
are copied though).
Arrays are represented as Vim [List](#List) type.
Hashes are represented as Vim [Dictionary](#Dictionary) type.
Other objects are represented as strings resulted from their
"Object#to_s" method.

Can also be used as a [method](#method):
```
GetRubyExpr()->rubyeval()

### <a id="screenattr()" class="section-title" href="#screenattr()">screenattr({row}, {col})</a>
Like [screenchar()](#screenchar()), but return the attribute.  This is a rather
arbitrary number that can only be used to compare to the
attribute at other positions.
Returns -1 when row or col is out of range.

Can also be used as a [method](#method):
```
GetRow()->screenattr(col)

### <a id="screenchar()" class="section-title" href="#screenchar()">screenchar({row}, {col})</a>
The result is a Number, which is the character at position
[row, col] on the screen.  This works for every possible
screen position, also status lines, window separators and the
command line.  The top left position is row one, column one
The character excludes composing characters.  For double-byte
encodings it may only be the first byte.
This is mainly to be used for testing.
Returns -1 when row or col is out of range.

Can also be used as a [method](#method):
```
GetRow()->screenchar(col)

### <a id="screenchars()" class="section-title" href="#screenchars()">screenchars({row}, {col})</a>
The result is a List of Numbers.  The first number is the same
as what [screenchar()](#screenchar()) returns.  Further numbers are
composing characters on top of the base character.
This is mainly to be used for testing.
Returns an empty List when row or col is out of range.

Can also be used as a [method](#method):
```
GetRow()->screenchars(col)

### <a id="screencol()" class="section-title" href="#screencol()">screencol()</a>
The result is a Number, which is the current screen column of
the cursor. The leftmost column has number 1.
This function is mainly used for testing.

Note: Always returns the current screen column, thus if used
in a command (e.g. ":echo screencol()") it will return the
column inside the command line, which is 1 when the command is
executed. To get the cursor position in the file use one of
the following mappings:
```
nnoremap <expr> GG ":echom " .. screencol() .. "\n"
nnoremap <silent> GG :echom screencol()<CR>
noremap GG <Cmd>echom screencol()<Cr>

```

### <a id="screenpos()" class="section-title" href="#screenpos()">screenpos({winid}, {lnum}, {col})</a>
The result is a Dict with the screen position of the text
character in window {winid} at buffer line {lnum} and column
{col}.  {col} is a one-based byte index.
The Dict has these members:
row	screen row
col	first screen column
endcol	last screen column
curscol	cursor screen column
If the specified position is not visible, all values are zero.
The "endcol" value differs from "col" when the character
occupies more than one screen cell.  E.g. for a Tab "col" can
be 1 and "endcol" can be 8.
The "curscol" value is where the cursor would be placed.  For
a Tab it would be the same as "endcol", while for a double
width character it would be the same as "col".
The [conceal](#conceal) feature is ignored here, the column numbers are
as if 'conceallevel' is zero.  You can set the cursor to the
right position and use [screencol()](#screencol()) to get the value with
[conceal](#conceal) taken into account.
Returns an empty Dict if {winid} is invalid.

Can also be used as a [method](#method):
```
GetWinid()->screenpos(lnum, col)

### <a id="screenrow()" class="section-title" href="#screenrow()">screenrow()</a>
The result is a Number, which is the current screen row of the
cursor.  The top line has number one.
This function is mainly used for testing.
Alternatively you can use [winline()](#winline()).

Note: Same restrictions as with [screencol()](#screencol()).

### <a id="screenstring()" class="section-title" href="#screenstring()">screenstring({row}, {col})</a>
The result is a String that contains the base character and
any composing characters at position [row, col] on the screen.
This is like [screenchars()](#screenchars()) but returning a String with the
characters.
This is mainly to be used for testing.
Returns an empty String when row or col is out of range.

Can also be used as a [method](#method):
```
GetRow()->screenstring(col)

```

### <a id="search()" class="section-title" href="#search()">Note:</a>
search({pattern} [, {flags} [, {stopline} [, {timeout} [, {skip}]]]])
Search for regexp pattern {pattern}.  The search starts at the
cursor position (you can use [cursor()](#cursor()) to set it).

When a match has been found its line number is returned.
If there is no match a 0 is returned and the cursor doesn't
move.  No error message is given.

{flags} is a String, which can contain these character flags:
'b'	search Backward instead of forward
'c'	accept a match at the Cursor position
'e'	move to the End of the match
'n'	do Not move the cursor
'p'	return number of matching sub-Pattern (see below)
's'	Set the ' mark at the previous location of the cursor
'w'	Wrap around the end of the file
'W'	don't Wrap around the end of the file
'z'	start searching at the cursor column instead of Zero
If neither 'w' or 'W' is given, the 'wrapscan' option applies.

If the 's' flag is supplied, the ' mark is set, only if the
cursor is moved. The 's' flag cannot be combined with the 'n'
flag.

'ignorecase', 'smartcase' and 'magic' are used.

When the 'z' flag is not given, forward searching always
starts in column zero and then matches before the cursor are
skipped.  When the 'c' flag is present in 'cpo' the next
search starts after the match.  Without the 'c' flag the next
search starts one column after the start of the match.  This
matters for overlapping matches.  See [cpo-c](#cpo-c).  You can also
insert "\ze" to change where the match ends, see  [/\ze](#/\ze).

When searching backwards and the 'z' flag is given then the
search starts in column zero, thus no match in the current
line will be found (unless wrapping around the end of the
file).

When the {stopline} argument is given then the search stops
after searching this line.  This is useful to restrict the
search to a range of lines.  Examples:
```
let match = search('(', 'b', line("w0"))
let end = search('END', '', line("w$"))

```
		When {stopline} is used and it is not zero this also implies
that the search does not wrap around the end of the file.
A zero value is equal to not giving the argument.

When the {timeout} argument is given the search stops when
more than this many milliseconds have passed.  Thus when
{timeout} is 500 the search stops after half a second.
The value must not be negative.  A zero value is like not
giving the argument.

If the {skip} expression is given it is evaluated with the
cursor positioned on the start of a match.  If it evaluates to
non-zero this match is skipped.  This can be used, for
example, to skip a match in a comment or a string.
{skip} can be a string, which is evaluated as an expression, a
function reference or a lambda.
When {skip} is omitted or empty, every match is accepted.
When evaluating {skip} causes an error the search is aborted
and -1 returned.
### <a id="search()-sub-match" class="section-title" href="#search()-sub-match">Note:</a>
With the 'p' flag the returned value is one more than the
first sub-match in \(\).  One if none of them matched but the
whole pattern did match.
To get the column number too use [searchpos()](#searchpos()).

The cursor will be positioned at the match, unless the 'n'
flag is used.

Example (goes over all files in the argument list):
```
:let n = 1
:while n <= argc()	    " loop over all files in arglist
:  exe "argument " .. n
:  " start at the last char in the file and wrap for the
:  " first search to find match at start of file
:  normal G$
:  let flags = "w"
:  while search("foo", flags) > 0
:	 s/foo/bar/g
:	 let flags = "W"
:  endwhile
:  update		    " write the file if modified
:  let n = n + 1
:endwhile

```

Example for using some flags:
```
:echo search('\<if\[\(else\)\](#\(else\)\)\(endif\)', 'ncpe')

```
		This will search for the keywords "if", "else", and "endif"
under or after the cursor.  Because of the 'p' flag, it
returns 1, 2, or 3 depending on which keyword is found, or 0
if the search fails.  With the cursor on the first word of the
line:
if (foo == 0) [ let foo = foo + 1 ](# let foo = foo + 1 ) endif ~
the function returns 1.  Without the 'c' flag, the function
finds the "endif" and returns 3.  The same thing happens
without the 'e' flag if the cursor is on the "f" of "if".
The 'n' flag tells the function not to move the cursor.

Can also be used as a [method](#method):
```
GetPattern()->search()

### <a id="searchcount()" class="section-title" href="#searchcount()">searchcount([{options}])</a>
Get or update the last search count, like what is displayed
without the "S" flag in 'shortmess'.  This works even if
'shortmess' does contain the "S" flag.

This returns a Dictionary. The dictionary is empty if the
previous pattern was not set and "pattern" was not specified.

key		type		meaning ~
current	[Number](#Number)	current position of match;
0 if the cursor position is
before the first match
exact_match	[Boolean](#Boolean)	1 if "current" is matched on
"pos", otherwise 0
total		[Number](#Number)	total count of matches found
incomplete	[Number](#Number)	0: search was fully completed
1: recomputing was timed out
2: max count exceeded

For {options} see further down.

To get the last search count when [n| or |N](#n| or |N) was pressed, call
this function with `recompute: 0` . This sometimes returns
wrong information because [n| and |N](#n| and |N)'s maximum count is 99.
If it exceeded 99 the result must be max count + 1 (100). If
you want to get correct information, specify `recompute: 1`:
```

" result == maxcount + 1 (100) when many matches
let result = searchcount(#{recompute: 0})

" Below returns correct result (recompute defaults
" to 1)
let result = searchcount()

```

The function is useful to add the count to 'statusline':
```
function! LastSearchCount() abort
let result = searchcount(#{recompute: 0})
if empty(result)
return ''
endif
if result.incomplete ==# 1     " timed out
return printf(' /%s [?/??]', @/)
elseif result.incomplete ==# 2 " max count exceeded
if result.total > result.maxcount &&
\  result.current > result.maxcount
return printf(' /%s [>%d/>%d]', @/,
\             result.current, result.total)
elseif result.total > result.maxcount
return printf(' /%s [%d/>%d]', @/,
\             result.current, result.total)
endif
endif
return printf(' /%s [%d/%d]', @/,
\             result.current, result.total)
endfunction
let &statusline ..= '%{LastSearchCount()}'

" Or if you want to show the count only when
" 'hlsearch' was on
" let &statusline ..=
" \   '%{v:hlsearch ? LastSearchCount() : ""}'

```

You can also update the search count, which can be useful in a
[CursorMoved| or |CursorMovedI](#CursorMoved| or |CursorMovedI) autocommand:
```

### <a id="autocmd CursorMoved,CursorMovedI " class="section-title" href="#autocmd CursorMoved,CursorMovedI ">Note:</a>
\ let s:searchcount_timer = timer_start(
\   200, function('s:update_searchcount'))
function! s:update_searchcount(timer) abort
if a:timer ==# s:searchcount_timer
call searchcount(#{
\ recompute: 1, maxcount: 0, timeout: 100})
redrawstatus
endif
endfunction

```

This can also be used to count matched texts with specified
pattern in the current buffer using "pattern":
```

" Count '\<foo\>' in this buffer
" (Note that it also updates search count)
let result = searchcount(#{pattern: '\<foo\>'})

" To restore old search count by old pattern,
" search again
call searchcount()

```

{options} must be a Dictionary. It can contain:
key		type		meaning ~
recompute	[Boolean|	if |TRUE](#Boolean|	if |TRUE), recompute the count
like [n| or |N](#n| or |N) was executed.
otherwise returns the last
computed result (when [n](#n) or
[N](#N) was used when "S" is not
in 'shortmess', or this
function was called).
(default: [TRUE](#TRUE))
pattern	[String](#String)	recompute if this was given
and different with [@/](#@/).
this works as same as the
below command is executed
before calling this function
```
let @/ = pattern

```
						(default: [@/](#@/))
timeout	[Number](#Number)	0 or negative number is no
timeout. timeout milliseconds
for recomputing the result
(default: 0)
maxcount	[Number](#Number)	0 or negative number is no
limit. max count of matched
text while recomputing the
result.  if search exceeded
total count, "total" value
becomes `maxcount + 1`
(default: 0)
pos		[List](#List)		`[lnum, col, off]` value
when recomputing the result.
this changes "current" result
value. see [cursor()|, ](#cursor()|, )getpos()
(default: cursor's position)

Can also be used as a [method](#method):
```
GetSearchOpts()->searchcount()

```

### <a id="searchdecl()" class="section-title" href="#searchdecl()">searchdecl({name} [, {global} [, {thisblock}]])</a>
Search for the declaration of {name}.

With a non-zero {global} argument it works like [gD](#gD), find
first match in the file.  Otherwise it works like [gd](#gd), find
first match in the function.

With a non-zero {thisblock} argument matches in a {} block
that ends before the cursor position are ignored.  Avoids
finding variable declarations only valid in another scope.

Moves the cursor to the found match.
Returns zero for success, non-zero for failure.
Example:
```
if searchdecl('myvar') == 0
echo getline('.')
endif

```

Can also be used as a [method](#method):
```
GetName()->searchdecl()

```

### <a id="searchpair()" class="section-title" href="#searchpair()">Note:</a>
searchpair({start}, {middle}, {end} [, {flags} [, {skip}
[, {stopline} [, {timeout}]]]])
Search for the match of a nested start-end pair.  This can be
used to find the "endif" that matches an "if", while other
if/endif pairs in between are ignored.
The search starts at the cursor.  The default is to search
forward, include 'b' in {flags} to search backward.
If a match is found, the cursor is positioned at it and the
line number is returned.  If no match is found 0 or -1 is
returned and the cursor doesn't move.  No error message is
given.

{start}, {middle} and {end} are patterns, see [pattern](#pattern).  They
must not contain \( \) pairs.  Use of \%( \) is allowed.  When
{middle} is not empty, it is found when searching from either
direction, but only when not in a nested start-end pair.  A
typical use is:
```
searchpair('\<if\>', '\<else\>', '\<endif\>')

```
		By leaving {middle} empty the "else" is skipped.

{flags} 'b', 'c', 'n', 's', 'w' and 'W' are used like with
[search()](#search()).  Additionally:
'r'	Repeat until no more matches found; will find the
outer pair.  Implies the 'W' flag.
'm'	Return number of matches instead of line number with
the match; will be > 1 when 'r' is used.
Note: it's nearly always a good idea to use the 'W' flag, to
avoid wrapping around the end of the file.

When a match for {start}, {middle} or {end} is found, the
{skip} expression is evaluated with the cursor positioned on
the start of the match.  It should return non-zero if this
match is to be skipped.  E.g., because it is inside a comment
or a string.
When {skip} is omitted or empty, every match is accepted.
When evaluating {skip} causes an error the search is aborted
and -1 returned.
{skip} can be a string, a lambda, a funcref or a partial.
Anything else makes the function fail.

For {stopline} and {timeout} see [search()](#search()).

The value of 'ignorecase' is used.  'magic' is ignored, the
patterns are used like it's on.

The search starts exactly at the cursor.  A match with
{start}, {middle} or {end} at the next character, in the
direction of searching, is the first one found.  Example:
```
if 1
if 2
endif 2
endif 1

```
		When starting at the "if 2", with the cursor on the "i", and
searching forwards, the "endif 2" is found.  When starting on
the character just before the "if 2", the "endif 1" will be
found.  That's because the "if 2" will be found first, and
then this is considered to be a nested if/endif from "if 2" to
"endif 2".
When searching backwards and {end} is more than one character,
it may be useful to put "\zs" at the end of the pattern, so
that when the cursor is inside a match with the end it finds
the matching start.

Example, to find the "endif" command in a Vim script:
```

:echo searchpair('\<if\>', '\<el\%[seif]\>', '\<en\%[dif]\>', 'W',
### <a id="\ 'getline(".") =~ "^\\s\""')" class="section-title" href="#\ 'getline(".") =~ "^\\s\""')">Note:</a>


```
		The cursor must be at or after the "if" for which a match is
to be found.  Note that single-quote strings are used to avoid
having to double the backslashes.  The skip expression only
catches comments at the start of a line, not after a command.
Also, a word "en" or "if" halfway through a line is considered
a match.
Another example, to search for the matching "{" of a "}":
```

:echo searchpair('{', '', '}', 'bW')


```
		This works when the cursor is at or before the "}" for which a
match is to be found.  To reject matches that syntax
highlighting recognized as strings:
```

:echo searchpair('{', '', '}', 'bW',
\ 'synIDattr(synID(line("."), col("."), 0), "name") =~? "string"')

```

### <a id="searchpairpos()" class="section-title" href="#searchpairpos()">Note:</a>
searchpairpos({start}, {middle}, {end} [, {flags} [, {skip}
[, {stopline} [, {timeout}]]]])
Same as [searchpair()|, but returns a |List](#searchpair()|, but returns a |List) with the line and
column position of the match. The first element of the [List](#List)
is the line number and the second element is the byte index of
the column position of the match.  If no match is found,
returns [0, 0].
```

:let [lnum,col] = searchpairpos('{', '', '}', 'n')

```

See [match-parens](#match-parens) for a bigger and more useful example.

### <a id="searchpos()" class="section-title" href="#searchpos()">Note:</a>
searchpos({pattern} [, {flags} [, {stopline} [, {timeout} [, {skip}]]]])
Same as [search()|, but returns a |List](#search()|, but returns a |List) with the line and
column position of the match. The first element of the [List](#List)
is the line number and the second element is the byte index of
the column position of the match. If no match is found,
returns [0, 0].
Example:
```
:let [lnum, col] = searchpos('mypattern', 'n')


```
		When the 'p' flag is given then there is an extra item with
the sub-pattern match number [search()-sub-match](#search()-sub-match).  Example:
```
:let [lnum, col, submatch] = searchpos('\(\l\)\|\(\u\)', 'np')

```
		In this example "submatch" is 2 when a lowercase letter is
found [/\l|, 3 when an uppercase letter is found |/\u](#/\l|, 3 when an uppercase letter is found |/\u).

Can also be used as a [method](#method):
```
GetPattern()->searchpos()

### <a id="serverlist()" class="section-title" href="#serverlist()">serverlist()</a>
Returns a list of server addresses, or empty if all servers
were stopped. [serverstart()| |serverstop()](#serverstart()| |serverstop())
Example:
```
:echo serverlist()

### <a id="serverstart()" class="section-title" href="#serverstart()">serverstart([{address}])</a>
Opens a socket or named pipe at {address} and listens for
[RPC| messages. Clients can send |API](#RPC| messages. Clients can send |API) commands to the
returned address to control Nvim.

Returns the address string (which may differ from the
{address} argument, see below).

- If {address} has a colon (":") it is a TCP/IPv4/IPv6 address
where the last ":" separates host and port (empty or zero
assigns a random port).
- Else {address} is the path to a named pipe (except on Windows).
- If {address} has no slashes ("/") it is treated as the
"name" part of a generated path in this format:
```
stdpath("run").."/{name}.{pid}.{counter}"

```
		  - If {address} is omitted the name is "nvim".
```
:echo serverstart()
=> /tmp/nvim.bram/oknANW/nvim.15430.5


```
		Example bash command to list all Nvim servers:
```
### <a id="ls ${XDG_RUNTIME_DIR:-${TMPDIR}nvim.${USER}}//nvim..0" class="section-title" href="#ls ${XDG_RUNTIME_DIR:-${TMPDIR}nvim.${USER}}//nvim..0">Note:</a>


```
		Example named pipe:
```
if has('win32')
echo serverstart('\\.\pipe\nvim-pipe-1234')
else
echo serverstart('nvim.sock')
endif

```

Example TCP/IP address:
```
echo serverstart('::1:12345')

### <a id="serverstop()" class="section-title" href="#serverstop()">serverstop({address})</a>
Closes the pipe or socket at {address}.
Returns TRUE if {address} is valid, else FALSE.
If [v:servername](#v:servername) is stopped it is set to the next available
address in [serverlist()](#serverlist()).

### <a id="setbufline()" class="section-title" href="#setbufline()">setbufline({buf}, {lnum}, {text})</a>
Set line {lnum} to {text} in buffer {buf}.  This works like
[setline()](#setline()) for the specified buffer.

This function works only for loaded buffers. First call
[bufload()](#bufload()) if needed.

To insert lines use [appendbufline()](#appendbufline()).

{text} can be a string to set one line, or a list of strings
to set multiple lines.  If the list extends below the last
line then those lines are added.

For the use of {buf}, see [bufname()](#bufname()) above.

{lnum} is used like with [setline()](#setline()).
Use "$" to refer to the last line in buffer {buf}.
When {lnum} is just below the last line the {text} will be
added below the last line.
On success 0 is returned, on failure 1 is returned.

If {buf} is not a valid buffer or {lnum} is not valid, an
error message is given.

Can also be used as a [method](#method), the base is passed as the
third argument:
```
GetText()->setbufline(buf, lnum)

### <a id="setbufvar()" class="section-title" href="#setbufvar()">setbufvar({buf}, {varname}, {val})</a>
Set option or local variable {varname} in buffer {buf} to
{val}.
This also works for a global or local window option, but it
doesn't work for a global or local window variable.
For a local window option the global value is unchanged.
For the use of {buf}, see [bufname()](#bufname()) above.
The {varname} argument is a string.
Note that the variable name without "b:" must be used.
Examples:
```
:call setbufvar(1, "&mod", 1)
:call setbufvar("todo", "myvar", "foobar")

```
		This function is not available in the [sandbox](#sandbox).

Can also be used as a [method](#method), the base is passed as the
third argument:
```
GetValue()->setbufvar(buf, varname)


### <a id="setcellwidths()" class="section-title" href="#setcellwidths()">setcellwidths({list})</a>
Specify overrides for cell widths of character ranges.  This
tells Vim how wide characters are, counted in screen cells.
This overrides 'ambiwidth'.  Example:
```
setcellwidths([[0xad, 0xad, 1],
\ [0x2194, 0x2199, 2]])

### <a id="E1109 E1110 E1111 E1112 E1113 E1114" class="section-title" href="#E1109 E1110 E1111 E1112 E1113 E1114"><</a>
The {list} argument is a list of lists with each three
numbers. These three numbers are [low, high, width].  "low"
and "high" can be the same, in which case this refers to one
character. Otherwise it is the range of characters from "low"
to "high" (inclusive).  "width" is either 1 or 2, indicating
the character width in screen cells.
An error is given if the argument is invalid, also when a
range overlaps with another.
Only characters with value 0x100 and higher can be used.

If the new value causes 'fillchars' or 'listchars' to become
invalid it is rejected and an error is given.

To clear the overrides pass an empty list:
```
setcellwidths([]);

```
		You can use the script $VIMRUNTIME/tools/emoji_list.vim to see
the effect for known emoji characters.

### <a id="setcharpos()" class="section-title" href="#setcharpos()">setcharpos({expr}, {list})</a>
Same as [setpos()](#setpos()) but uses the specified column number as the
character index instead of the byte index in the line.

Example:
With the text "여보세요" in line 8:
```
call setcharpos('.', [0, 8, 4, 0])

```
		positions the cursor on the fourth character '요'.
```
call setpos('.', [0, 8, 4, 0])

```
		positions the cursor on the second character '보'.

Can also be used as a [method](#method):
```
GetPosition()->setcharpos('.')

### <a id="setcharsearch()" class="section-title" href="#setcharsearch()">setcharsearch({dict})</a>
Set the current character search information to {dict},
which contains one or more of the following entries:

char	character which will be used for a subsequent
[,| or |;](#,| or |;) command; an empty string clears the
character search
forward	direction of character search; 1 for forward,
0 for backward
until	type of character search; 1 for a [t| or |T](#t| or |T)
character search, 0 for an [f| or |F](#f| or |F)
character search

This can be useful to save/restore a user's character search
from a script:
```
:let prevsearch = getcharsearch()
:" Perform a command which clobbers user's search
:call setcharsearch(prevsearch)

```
		Also see [getcharsearch()](#getcharsearch()).

Can also be used as a [method](#method):
```
SavedSearch()->setcharsearch()

### <a id="setcmdline()" class="section-title" href="#setcmdline()">setcmdline({str} [, {pos}])</a>
Set the command line to {str} and set the cursor position to
{pos}.
If {pos} is omitted, the cursor is positioned after the text.
Returns 0 when successful, 1 when not editing the command
line.

Can also be used as a [method](#method):
```
GetText()->setcmdline()

### <a id="setcmdpos()" class="section-title" href="#setcmdpos()">setcmdpos({pos})</a>
Set the cursor position in the command line to byte position
{pos}.  The first position is 1.
Use [getcmdpos()](#getcmdpos()) to obtain the current position.
Only works while editing the command line, thus you must use
[c_CTRL-\_e|, |c_CTRL-R_=| or |c_CTRL-R_CTRL-R](#c_CTRL-\_e|, |c_CTRL-R_=| or |c_CTRL-R_CTRL-R) with '='.  For
[c_CTRL-\_e| and |c_CTRL-R_CTRL-R](#c_CTRL-\_e| and |c_CTRL-R_CTRL-R) with '=' the position is
set after the command line is set to the expression.  For
[c_CTRL-R_=](#c_CTRL-R_=) it is set after evaluating the expression but
before inserting the resulting text.
When the number is too big the cursor is put at the end of the
line.  A number smaller than one has undefined results.
Returns 0 when successful, 1 when not editing the command
line.

Can also be used as a [method](#method):
```
GetPos()->setcmdpos()

### <a id="setcursorcharpos()" class="section-title" href="#setcursorcharpos()">setcursorcharpos({lnum}, {col} [, {off}])</a>
setcursorcharpos({list})
Same as [cursor()](#cursor()) but uses the specified column number as the
character index instead of the byte index in the line.

Example:
With the text "여보세요" in line 4:
```
call setcursorcharpos(4, 3)

```
		positions the cursor on the third character '세'.
```
call cursor(4, 3)

```
		positions the cursor on the first character '여'.

Can also be used as a [method](#method):
```
GetCursorPos()->setcursorcharpos()

### <a id="setenv()" class="section-title" href="#setenv()">setenv({name}, {val})</a>
Set environment variable {name} to {val}.  Example:
```
call setenv('HOME', '/home/myhome')


```
		When {val} is [v:null](#v:null) the environment variable is deleted.
See also [expr-env](#expr-env).

Can also be used as a [method](#method), the base is passed as the
second argument:
```
GetPath()->setenv('PATH')

### <a id="setfperm() chmod" class="section-title" href="#setfperm() chmod">setfperm({fname}, {mode})</a>
Set the file permissions for {fname} to {mode}.
{mode} must be a string with 9 characters.  It is of the form
"rwxrwxrwx", where each group of "rwx" flags represent, in
turn, the permissions of the owner of the file, the group the
file belongs to, and other users.  A '-' character means the
permission is off, any other character means on.  Multi-byte
characters are not supported.

For example "rw-r-----" means read-write for the user,
readable by the group, not accessible by others.  "xx-x-----"
would do the same thing.

Returns non-zero for success, zero for failure.

Can also be used as a [method](#method):
```
GetFilename()->setfperm(mode)

```

To read permissions see [getfperm()](#getfperm()).

### <a id="setline()" class="section-title" href="#setline()">setline({lnum}, {text})</a>
Set line {lnum} of the current buffer to {text}.  To insert
lines use [append()](#append()). To set lines in another buffer use
[setbufline()](#setbufline()).

{lnum} is used like with [getline()](#getline()).
When {lnum} is just below the last line the {text} will be
added below the last line.

If this succeeds, FALSE is returned.  If this fails (most likely
because {lnum} is invalid) TRUE is returned.

Example:
```
:call setline(5, strftime("%c"))


```
		When {text} is a [List](#List) then line {lnum} and following lines
will be set to the items in the list.  Example:
```
:call setline(5, ['aaa', 'bbb', 'ccc'])

```
		This is equivalent to:
```
:for [n, l] in [[5, 'aaa'], [6, 'bbb'], [7, 'ccc']]
:  call setline(n, l)
:endfor


```
		Note: The '[ and '] marks are not set.

Can also be used as a [method](#method), the base is passed as the
second argument:
```
GetText()->setline(lnum)

### <a id="setloclist()" class="section-title" href="#setloclist()">setloclist({nr}, {list} [, {action} [, {what}]])</a>
Create or replace or add to the location list for window {nr}.
{nr} can be the window number or the [window-ID](#window-ID).
When {nr} is zero the current window is used.

For a location list window, the displayed location list is
modified.  For an invalid window number {nr}, -1 is returned.
Otherwise, same as [setqflist()](#setqflist()).
Also see [location-list](#location-list).

For {action} see [setqflist-action](#setqflist-action).

If the optional {what} dictionary argument is supplied, then
only the items listed in {what} are set. Refer to [setqflist()](#setqflist())
for the list of supported keys in {what}.

Can also be used as a [method](#method), the base is passed as the
second argument:
```
GetLoclist()->setloclist(winnr)

### <a id="setmatches()" class="section-title" href="#setmatches()">setmatches({list} [, {win}])</a>
Restores a list of matches saved by |getmatches() for the
current window|.  Returns 0 if successful, otherwise -1.  All
current matches are cleared before the list is restored.  See
example for [getmatches()](#getmatches()).
If {win} is specified, use the window with this number or
window ID instead of the current window.

Can also be used as a [method](#method):
```
GetMatches()->setmatches()

```

### <a id="setpos()" class="section-title" href="#setpos()">Note:</a>
setpos({expr}, {list})
Set the position for String {expr}.  Possible values:
.	the cursor
'x	mark x

{list} must be a [List](#List) with four or five numbers:
[bufnum, lnum, col, off]
[bufnum, lnum, col, off, curswant]

"bufnum" is the buffer number.	Zero can be used for the
current buffer.  When setting an uppercase mark "bufnum" is
used for the mark position.  For other marks it specifies the
buffer to set the mark in.  You can use the [bufnr()](#bufnr()) function
to turn a file name into a buffer number.
For setting the cursor and the ' mark "bufnum" is ignored,
since these are associated with a window, not a buffer.
Does not change the jumplist.

"lnum" and "col" are the position in the buffer.  The first
column is 1.  Use a zero "lnum" to delete a mark.  If "col" is
smaller than 1 then 1 is used. To use the character count
instead of the byte count, use [setcharpos()](#setcharpos()).

The "off" number is only used when 'virtualedit' is set. Then
it is the offset in screen columns from the start of the
character.  E.g., a position within a <Tab> or after the last
character.

The "curswant" number is only used when setting the cursor
position.  It sets the preferred column for when moving the
cursor vertically.  When the "curswant" number is missing the
preferred column is not set.  When it is present and setting a
mark position it is not used.

Note that for '< and '> changing the line number may result in
the marks to be effectively be swapped, so that '< is always
before '>.

Returns 0 when the position could be set, -1 otherwise.
An error message is given if {expr} is invalid.

Also see [setcharpos()|, |getpos()| and |getcurpos()](#setcharpos()|, |getpos()| and |getcurpos()).

This does not restore the preferred column for moving
vertically; if you set the cursor position with this, [j](#j) and
[k| motions will jump to previous columns!  Use |cursor()](#k| motions will jump to previous columns!  Use |cursor()) to
also set the preferred column.  Also see the "curswant" key in
[winrestview()](#winrestview()).

Can also be used as a [method](#method):
```
GetPosition()->setpos('.')

### <a id="setqflist()" class="section-title" href="#setqflist()">setqflist({list} [, {action} [, {what}]])</a>
Create or replace or add to the quickfix list.

If the optional {what} dictionary argument is supplied, then
only the items listed in {what} are set. The first {list}
argument is ignored.  See below for the supported items in
{what}.
### <a id="setqflist-what" class="section-title" href="#setqflist-what">Note:</a>
When {what} is not present, the items in {list} are used.  Each
item must be a dictionary.  Non-dictionary items in {list} are
ignored.  Each dictionary item can contain the following
entries:

bufnr	buffer number; must be the number of a valid
buffer
filename	name of a file; only used when "bufnr" is not
present or it is invalid.
module	name of a module; if given it will be used in
quickfix error window instead of the filename.
lnum	line number in the file
end_lnum	end of lines, if the item spans multiple lines
pattern	search pattern used to locate the error
col		column number
vcol	when non-zero: "col" is visual column
when zero: "col" is byte index
end_col	end column, if the item spans multiple columns
nr		error number
text	description of the error
type	single-character error type, 'E', 'W', etc.
valid	recognized error message

The "col", "vcol", "nr", "type" and "text" entries are
optional.  Either "lnum" or "pattern" entry can be used to
locate a matching error line.
If the "filename" and "bufnr" entries are not present or
neither the "lnum" or "pattern" entries are present, then the
item will not be handled as an error line.
If both "pattern" and "lnum" are present then "pattern" will
be used.
If the "valid" entry is not supplied, then the valid flag is
set when "bufnr" is a valid buffer or "filename" exists.
If you supply an empty {list}, the quickfix list will be
cleared.
Note that the list is not exactly the same as what
[getqflist()](#getqflist()) returns.

{action} values:		*setqflist-action* *E927*
'a'	The items from {list} are added to the existing
quickfix list. If there is no existing list, then a
new list is created.

'r'	The items from the current quickfix list are replaced
with the items from {list}.  This can also be used to
clear the list:
```
:call setqflist([], 'r')

```

'f'	All the quickfix lists in the quickfix stack are
freed.

If {action} is not present or is set to ' ', then a new list
is created. The new quickfix list is added after the current
quickfix list in the stack and all the following lists are
freed. To add a new quickfix list at the end of the stack,
set "nr" in {what} to "$".

The following items can be specified in dictionary {what}:
context	quickfix list context. See [quickfix-context](#quickfix-context)
efm		errorformat to use when parsing text from
"lines". If this is not present, then the
'errorformat' option value is used.
See [quickfix-parse](#quickfix-parse)
id		quickfix list identifier [quickfix-ID](#quickfix-ID)
idx		index of the current entry in the quickfix
list specified by "id" or "nr". If set to '$',
then the last entry in the list is set as the
current entry.  See [quickfix-index](#quickfix-index)
items	list of quickfix entries. Same as the {list}
argument.
lines	use 'errorformat' to parse a list of lines and
add the resulting entries to the quickfix list
{nr} or {id}.  Only a [List](#List) value is supported.
See [quickfix-parse](#quickfix-parse)
nr		list number in the quickfix stack; zero
means the current quickfix list and "$" means
the last quickfix list.
quickfixtextfunc
function to get the text to display in the
quickfix window.  The value can be the name of
a function or a funcref or a lambda.  Refer to
[quickfix-window-function](#quickfix-window-function) for an explanation
of how to write the function and an example.
title	quickfix list title text. See [quickfix-title](#quickfix-title)
Unsupported keys in {what} are ignored.
If the "nr" item is not present, then the current quickfix list
is modified. When creating a new quickfix list, "nr" can be
set to a value one greater than the quickfix stack size.
When modifying a quickfix list, to guarantee that the correct
list is modified, "id" should be used instead of "nr" to
specify the list.

Examples (See also [setqflist-examples](#setqflist-examples)):
```
:call setqflist([], 'r', {'title': 'My search'})
:call setqflist([], 'r', {'nr': 2, 'title': 'Errors'})
:call setqflist([], 'a', {'id':qfid, 'lines':["F1:10:L10"]})

```

Returns zero for success, -1 for failure.

This function can be used to create a quickfix list
independent of the 'errorformat' setting.  Use a command like
`:cc 1` to jump to the first position.

Can also be used as a [method](#method), the base is passed as the
second argument:
```
GetErrorlist()->setqflist()

```

### <a id="setreg()" class="section-title" href="#setreg()">Note:</a>
setreg({regname}, {value} [, {options}])
Set the register {regname} to {value}.
The {regname} argument is a string.

{value} may be any value returned by [getreg()](#getreg()) or
[getreginfo()|, including a |List| or |Dict](#getreginfo()|, including a |List| or |Dict).
If {options} contains "a" or {regname} is upper case,
then the value is appended.

{options} can also contain a register type specification:
"c" or "v"	      [charwise](#charwise) mode
"l" or "V"	      [linewise](#linewise) mode
"b" or "<CTRL-V>" [blockwise-visual](#blockwise-visual) mode
If a number immediately follows "b" or "<CTRL-V>" then this is
used as the width of the selection - if it is not specified
then the width of the block is set to the number of characters
in the longest line (counting a <Tab> as 1 character).
If {options} contains "u" or '"', then the unnamed register is
set to point to register {regname}.

If {options} contains no register settings, then the default
is to use character mode unless {value} ends in a <NL> for
string {value} and linewise mode for list {value}. Blockwise
mode is never selected automatically.
Returns zero for success, non-zero for failure.

### <a id="E883" class="section-title" href="#E883">Note:</a>
Note: you may not use [List](#List) containing more than one item to
set search and expression registers. Lists containing no
items act like empty strings.

Examples:
```
### <a id=":call setreg(v:register, @)" class="section-title" href="#:call setreg(v:register, @)">Note:</a>
### <a id=":call setreg('', @%, 'ac')" class="section-title" href="#:call setreg('', @%, 'ac')">Note:</a>
:call setreg('a', "1\n2\n3", 'b5')
:call setreg('"', { 'points_to': 'a'})


```
		This example shows using the functions to save and restore a
register:
```
:let var_a = getreginfo()
:call setreg('a', var_a)

```
		or:
```
:let var_a = getreg('a', 1, 1)
:let var_amode = getregtype('a')
....
:call setreg('a', var_a, var_amode)

```
		Note: you may not reliably restore register value
without using the third argument to [getreg()](#getreg()) as without it
newlines are represented as newlines AND Nul bytes are
represented as newlines as well, see [NL-used-for-Nul](#NL-used-for-Nul).

You can also change the type of a register by appending
nothing:
```
:call setreg('a', '', 'al')


```
		Can also be used as a [method](#method), the base is passed as the
second argument:
```
GetText()->setreg('a')

### <a id="settabvar()" class="section-title" href="#settabvar()">settabvar({tabnr}, {varname}, {val})</a>
Set tab-local variable {varname} to {val} in tab page {tabnr}.
[t:var](#t:var)
The {varname} argument is a string.
Note that the variable name without "t:" must be used.
Tabs are numbered starting with one.
This function is not available in the [sandbox](#sandbox).

Can also be used as a [method](#method), the base is passed as the
third argument:
```
GetValue()->settabvar(tab, name)

settabwinvar({tabnr}, {winnr}, {varname}, {val})	*settabwinvar()*
Set option or local variable {varname} in window {winnr} to
{val}.
Tabs are numbered starting with one.  For the current tabpage
use [setwinvar()](#setwinvar()).
{winnr} can be the window number or the [window-ID](#window-ID).
When {winnr} is zero the current window is used.
This also works for a global or local buffer option, but it
doesn't work for a global or local buffer variable.
For a local buffer option the global value is unchanged.
Note that the variable name without "w:" must be used.
Examples:
```
:call settabwinvar(1, 1, "&list", 0)
:call settabwinvar(3, 2, "myvar", "foobar")

```
		This function is not available in the [sandbox](#sandbox).

Can also be used as a [method](#method), the base is passed as the
fourth argument:
```
GetValue()->settabwinvar(tab, winnr, name)

### <a id="settagstack()" class="section-title" href="#settagstack()">settagstack({nr}, {dict} [, {action}])</a>
Modify the tag stack of the window {nr} using {dict}.
{nr} can be the window number or the [window-ID](#window-ID).

For a list of supported items in {dict}, refer to
[gettagstack()](#gettagstack()). "curidx" takes effect before changing the tag
stack.
### <a id="E962" class="section-title" href="#E962">Note:</a>
How the tag stack is modified depends on the {action}
argument:
- If {action} is not present or is set to 'r', then the tag
stack is replaced.
- If {action} is set to 'a', then new entries from {dict} are
pushed (added) onto the tag stack.
- If {action} is set to 't', then all the entries from the
current entry in the tag stack or "curidx" in {dict} are
removed and then new entries are pushed to the stack.

The current index is set to one after the length of the tag
stack after the modification.

Returns zero for success, -1 for failure.

Examples (for more examples see [tagstack-examples](#tagstack-examples)):
Empty the tag stack of window 3:
```
call settagstack(3, {'items' : []})


```
		    Save and restore the tag stack:
```
let stack = gettagstack(1003)
" do something else
call settagstack(1003, stack)
unlet stack

```

Can also be used as a [method](#method), the base is passed as the
second argument:
```
GetStack()->settagstack(winnr)

### <a id="setwinvar()" class="section-title" href="#setwinvar()">setwinvar({nr}, {varname}, {val})</a>
Like [settabwinvar()](#settabwinvar()) for the current tab page.
Examples:
```
:call setwinvar(1, "&list", 0)
:call setwinvar(2, "myvar", "foobar")


```
		Can also be used as a [method](#method), the base is passed as the
third argument:
```
GetValue()->setwinvar(winnr, name)

### <a id="sha256()" class="section-title" href="#sha256()">sha256({string})</a>
Returns a String with 64 hex characters, which is the SHA256
checksum of {string}.

Can also be used as a [method](#method):
```
GetText()->sha256()

### <a id="shellescape()" class="section-title" href="#shellescape()">shellescape({string} [, {special}])</a>
Escape {string} for use as a shell command argument.

On Windows when 'shellslash' is not set, encloses {string} in
double-quotes and doubles all double-quotes within {string}.
Otherwise encloses {string} in single-quotes and replaces all
"'" with "'\''".

If {special} is a [non-zero-arg](#non-zero-arg):
- Special items such as "!", "%", "#" and "<cword>" will be
preceded by a backslash. The backslash will be removed again
by the [:!](#:!) command.
- The <NL> character is escaped.

If 'shell' contains "csh" in the tail:
- The "!" character will be escaped. This is because csh and
tcsh use "!" for history replacement even in single-quotes.
- The <NL> character is escaped (twice if {special} is
a [non-zero-arg](#non-zero-arg)).

If 'shell' contains "fish" in the tail, the "\" character will
be escaped because in fish it is used as an escape character
inside single quotes.

Example of use with a [:!](#:!) command:
```
:exe '!dir ' .. shellescape(expand('<cfile>'), 1)

```
		This results in a directory listing for the file under the
cursor.  Example of use with [system()](#system()):
```
:call system("chmod +w -- " .. shellescape(expand("%")))

```
		See also [::S](#::S).

Can also be used as a [method](#method):
```
GetCommand()->shellescape()

### <a id="shiftwidth()" class="section-title" href="#shiftwidth()">shiftwidth([{col}])</a>
Returns the effective value of 'shiftwidth'. This is the
'shiftwidth' value unless it is zero, in which case it is the
'tabstop' value.  To be backwards compatible in indent
plugins, use this:
```
### <a id="if exists('shiftwidth')" class="section-title" href="#if exists('shiftwidth')">Note:</a>
func s:sw()
return shiftwidth()
endfunc
else
func s:sw()
return &sw
endfunc
endif

```
		And then use s:sw() instead of &sw.

When there is one argument {col} this is used as column number
for which to return the 'shiftwidth' value. This matters for the
'vartabstop' feature. If no {col} argument is given, column 1
will be assumed.

Can also be used as a [method](#method):
```
GetColumn()->shiftwidth()

sign_ functions are documented here: [sign-functions-details](#sign-functions-details)

### <a id="simplify()" class="section-title" href="#simplify()">simplify({filename})</a>
Simplify the file name as much as possible without changing
the meaning.  Shortcuts (on MS-Windows) or symbolic links (on
Unix) are not resolved.  If the first path component in
{filename} designates the current directory, this will be
valid for the result as well.  A trailing path separator is
not removed either. On Unix "//path" is unchanged, but
"///path" is simplified to "/path" (this follows the Posix
standard).
Example:
```
simplify("./dir/.././/file/") == "./file/"

```
		Note: The combination "dir/.." is only removed if "dir" is
a searchable directory or does not exist.  On Unix, it is also
removed when "dir" is a symbolic link within the same
directory.  In order to resolve all the involved symbolic
links before simplifying the path name, use [resolve()](#resolve()).

Can also be used as a [method](#method):
```
GetName()->simplify()

### <a id="sin()" class="section-title" href="#sin()">sin({expr})</a>
Return the sine of {expr}, measured in radians, as a [Float](#Float).
{expr} must evaluate to a [Float| or a |Number](#Float| or a |Number).
Returns 0.0 if {expr} is not a [Float| or a |Number](#Float| or a |Number).
Examples:
```
:echo sin(100)

```
			-0.506366
```
:echo sin(-4.01)

```
			0.763301

Can also be used as a [method](#method):
```
Compute()->sin()

### <a id="sinh()" class="section-title" href="#sinh()">sinh({expr})</a>
Return the hyperbolic sine of {expr} as a [Float](#Float) in the range
[-inf, inf].
{expr} must evaluate to a [Float| or a |Number](#Float| or a |Number).
Returns 0.0 if {expr} is not a [Float| or a |Number](#Float| or a |Number).
Examples:
```
:echo sinh(0.5)

```
			0.521095
```
:echo sinh(-0.9)

```
			-1.026517

Can also be used as a [method](#method):
```
Compute()->sinh()

### <a id="sockconnect()" class="section-title" href="#sockconnect()">sockconnect({mode}, {address} [, {opts}])</a>
Connect a socket to an address. If {mode} is "pipe" then
{address} should be the path of a named pipe. If {mode} is
"tcp" then {address} should be of the form "host:port" where
the host should be an ip adderess or host name, and port the
port number.

Returns a [channel| ID. Close the socket with |chanclose()](#channel| ID. Close the socket with |chanclose()).
Use [chansend()](#chansend()) to send data over a bytes socket, and
[rpcrequest()| and |rpcnotify()](#rpcrequest()| and |rpcnotify()) to communicate with a RPC
socket.

{opts} is an optional dictionary with these keys:
[on_data](#on_data) : callback invoked when data was read from socket
data_buffered : read socket data in [channel-buffered](#channel-buffered) mode.
rpc     : If set, [msgpack-rpc](#msgpack-rpc) will be used to communicate
over the socket.
Returns:
- The channel ID on success (greater than zero)
- 0 on invalid arguments or connection failure.

### <a id="sort() E702" class="section-title" href="#sort() E702">sort({list} [, {func} [, {dict}]])</a>
Sort the items in {list} in-place.  Returns {list}.

If you want a list to remain unmodified make a copy first:
```
:let sortedlist = sort(copy(mylist))


```
		When {func} is omitted, is empty or zero, then sort() uses the
string representation of each item to sort on.  Numbers sort
after Strings, [Lists](#Lists) after Numbers.  For sorting text in the
current buffer use [:sort](#:sort).

When {func} is given and it is '1' or 'i' then case is
ignored.

When {func} is given and it is 'l' then the current collation
locale is used for ordering. Implementation details: strcoll()
is used to compare strings. See [:language](#:language) check or set the
collation locale. [v:collate](#v:collate) can also be used to check the
current locale. Sorting using the locale typically ignores
case. Example:
```
" ö is sorted similarly to o with English locale.
:language collate en_US.UTF8
:echo sort(['n', 'o', 'O', 'ö', 'p', 'z'], 'l')

```
			['n', 'o', 'O', 'ö', 'p', 'z'] ~
```
" ö is sorted after z with Swedish locale.
:language collate sv_SE.UTF8
:echo sort(['n', 'o', 'O', 'ö', 'p', 'z'], 'l')

```
			['n', 'o', 'O', 'p', 'z', 'ö'] ~
This does not work properly on Mac.

When {func} is given and it is 'n' then all items will be
sorted numerical (Implementation detail: this uses the
strtod() function to parse numbers, Strings, Lists, Dicts and
Funcrefs will be considered as being 0).

When {func} is given and it is 'N' then all items will be
sorted numerical. This is like 'n' but a string containing
digits will be used as the number they represent.

When {func} is given and it is 'f' then all items will be
sorted numerical. All values must be a Number or a Float.

When {func} is a [Funcref](#Funcref) or a function name, this function
is called to compare items.  The function is invoked with two
items as argument and must return zero if they are equal, 1 or
bigger if the first one sorts after the second one, -1 or
smaller if the first one sorts before the second one.

{dict} is for functions with the "dict" attribute.  It will be
used to set the local variable "self". [Dictionary-function](#Dictionary-function)

The sort is stable, items which compare equal (as number or as
string) will keep their relative position. E.g., when sorting
on numbers, text strings will sort next to each other, in the
same order as they were originally.

Can also be used as a [method](#method):
```
mylist->sort()


```
		Also see [uniq()](#uniq()).

Example:
```
func MyCompare(i1, i2)
return a:i1 == a:i2 ? 0 : a:i1 > a:i2 ? 1 : -1
endfunc
eval mylist->sort("MyCompare")

```
		A shorter compare version for this specific simple case, which
ignores overflow:
```
func MyCompare(i1, i2)
return a:i1 - a:i2
endfunc

```
		For a simple expression you can use a lambda:
```
eval mylist->sort({i1, i2 -> i1 - i2})

```

### <a id="soundfold()" class="section-title" href="#soundfold()">Note:</a>
soundfold({word})
Return the sound-folded equivalent of {word}.  Uses the first
language in 'spelllang' for the current window that supports
soundfolding.  'spell' must be set.  When no sound folding is
possible the {word} is returned unmodified.
This can be used for making spelling suggestions.  Note that
the method can be quite slow.

Can also be used as a [method](#method):
```
GetWord()->soundfold()

```

### <a id="spellbadword()" class="section-title" href="#spellbadword()">Note:</a>
spellbadword([{sentence}])
Without argument: The result is the badly spelled word under
or after the cursor.  The cursor is moved to the start of the
bad word.  When no bad word is found in the cursor line the
result is an empty string and the cursor doesn't move.

With argument: The result is the first word in {sentence} that
is badly spelled.  If there are no spelling mistakes the
result is an empty string.

The return value is a list with two items:
- The badly spelled word or an empty string.
- The type of the spelling error:
"bad"		spelling mistake
"rare"		rare word
"local"		word only valid in another region
"caps"		word should start with Capital
Example:
```
echo spellbadword("the quik brown fox")

```
			['quik', 'bad'] ~

The spelling information for the current window and the value
of 'spelllang' are used.

Can also be used as a [method](#method):
```
GetText()->spellbadword()

```

### <a id="spellsuggest()" class="section-title" href="#spellsuggest()">Note:</a>
spellsuggest({word} [, {max} [, {capital}]])
Return a [List](#List) with spelling suggestions to replace {word}.
When {max} is given up to this number of suggestions are
returned.  Otherwise up to 25 suggestions are returned.

When the {capital} argument is given and it's non-zero only
suggestions with a leading capital will be given.  Use this
after a match with 'spellcapcheck'.

{word} can be a badly spelled word followed by other text.
This allows for joining two words that were split.  The
suggestions also include the following text, thus you can
replace a line.

{word} may also be a good word.  Similar words will then be
returned.  {word} itself is not included in the suggestions,
although it may appear capitalized.

The spelling information for the current window is used.  The
values of 'spelllang' and 'spellsuggest' are used.

Can also be used as a [method](#method):
```
GetWord()->spellsuggest()

### <a id="split()" class="section-title" href="#split()">split({string} [, {pattern} [, {keepempty}]])</a>
Make a [List](#List) out of {string}.  When {pattern} is omitted or
empty each white-separated sequence of characters becomes an
item.
Otherwise the string is split where {pattern} matches,
removing the matched characters. 'ignorecase' is not used
here, add \c to ignore case. [/\c](#/\c)
When the first or last item is empty it is omitted, unless the
{keepempty} argument is given and it's non-zero.
Other empty items are kept when {pattern} matches at least one
character or when {keepempty} is non-zero.
Example:
```
:let words = split(getline('.'), '\W\+')

```
		To split a string in individual characters:
```
:for c in split(mystring, '\zs')

```
		If you want to keep the separator you can also use '\zs' at
the end of the pattern:
```
:echo split('abc:def:ghi', ':\zs')

```
			['abc:', 'def:', 'ghi'] ~
Splitting a table where the first element can be empty:
```
:let items = split(line, ':', 1)

```
		The opposite function is [join()](#join()).

Can also be used as a [method](#method):
```
GetString()->split()

### <a id="sqrt()" class="section-title" href="#sqrt()">sqrt({expr})</a>
Return the non-negative square root of Float {expr} as a
[Float](#Float).
{expr} must evaluate to a [Float| or a |Number](#Float| or a |Number).  When {expr}
is negative the result is NaN (Not a Number).  Returns 0.0 if
{expr} is not a [Float| or a |Number](#Float| or a |Number).
Examples:
```
:echo sqrt(100)

```
			10.0
```
:echo sqrt(-4.01)

```
			str2float("nan")
NaN may be different, it depends on system libraries.

Can also be used as a [method](#method):
```
Compute()->sqrt()

### <a id="srand()" class="section-title" href="#srand()">srand([{expr}])</a>
Initialize seed used by [rand()](#rand()):
- If {expr} is not given, seed values are initialized by
reading from /dev/urandom, if possible, or using time(NULL)
a.k.a. epoch time otherwise; this only has second accuracy.
- If {expr} is given it must be a Number.  It is used to
initialize the seed values.  This is useful for testing or
when a predictable sequence is intended.

Examples:
```
:let seed = srand()
:let seed = srand(userinput)
:echo rand(seed)

```

Can also be used as a [method](#method):
```
userinput->srand()

### <a id="stdioopen()" class="section-title" href="#stdioopen()">stdioopen({opts})</a>
With [--headless| this opens stdin and stdout as a |channel](#--headless| this opens stdin and stdout as a |channel).
May be called only once. See [channel-stdio](#channel-stdio). stderr is not
handled by this function, see [v:stderr](#v:stderr).

Close the stdio handles with [chanclose()|. Use |chansend()](#chanclose()|. Use |chansend())
to send data to stdout, and [rpcrequest()| and |rpcnotify()](#rpcrequest()| and |rpcnotify())
to communicate over RPC.

{opts} is a dictionary with these keys:
[on_stdin](#on_stdin) : callback invoked when stdin is written to.
on_print : callback invoked when Nvim needs to print a
message, with the message (whose type is string)
as sole argument.
stdin_buffered : read stdin in [channel-buffered](#channel-buffered) mode.
rpc      : If set, [msgpack-rpc](#msgpack-rpc) will be used to communicate
over stdio
Returns:
- [channel-id](#channel-id) on success (value is always 1)
- 0 on invalid arguments


### <a id="stdpath() E6100" class="section-title" href="#stdpath() E6100">stdpath({what})</a>
Returns [standard-path](#standard-path) locations of various default files and
directories.

{what}       Type    Description ~
cache        String  Cache directory: arbitrary temporary
storage for plugins, etc.
config       String  User configuration directory. [init.vim](#init.vim)
is stored here.
config_dirs  List    Other configuration directories.
data         String  User data directory.
data_dirs    List    Other data directories.
log          String  Logs directory (for use by plugins too).
run          String  Run directory: temporary, local storage
for sockets, named pipes, etc.
state        String  Session state directory: storage for file
drafts, swap, undo, [shada](#shada).

Example:
```
:echo stdpath("config")


### <a id="str2float()" class="section-title" href="#str2float()">str2float({string} [, {quoted}])</a>
Convert String {string} to a Float.  This mostly works the
same as when using a floating point number in an expression,
see [floating-point-format](#floating-point-format).  But it's a bit more permissive.
E.g., "1e40" is accepted, while in an expression you need to
write "1.0e40".  The hexadecimal form "0x123" is also
accepted, but not others, like binary or octal.
When {quoted} is present and non-zero then embedded single
quotes before the dot are ignored, thus "1'000.0" is a
thousand.
Text after the number is silently ignored.
The decimal point is always '.', no matter what the locale is
set to.  A comma ends the number: "12,345.67" is converted to
12.0.  You can strip out thousands separators with
[substitute()](#substitute()):
```
let f = str2float(substitute(text, ',', '', 'g'))

```

Returns 0.0 if the conversion fails.

Can also be used as a [method](#method):
```
let f = text->substitute(',', '', 'g')->str2float()

### <a id="str2list()" class="section-title" href="#str2list()">str2list({string} [, {utf8}])</a>
Return a list containing the number values which represent
each character in String {string}.  Examples:
```
str2list(" ")		returns [32]
str2list("ABC")		returns [65, 66, 67]

```
		[list2str()](#list2str()) does the opposite.

UTF-8 encoding is always used, {utf8} option has no effect,
and exists only for backwards-compatibility.
With UTF-8 composing characters are handled properly:
```
str2list("á")		returns [97, 769]


```
		Can also be used as a [method](#method):
```
GetString()->str2list()

### <a id="str2nr()" class="section-title" href="#str2nr()">str2nr({string} [, {base}])</a>
Convert string {string} to a number.
{base} is the conversion base, it can be 2, 8, 10 or 16.
When {quoted} is present and non-zero then embedded single
quotes are ignored, thus "1'000'000" is a million.

When {base} is omitted base 10 is used.  This also means that
a leading zero doesn't cause octal conversion to be used, as
with the default String to Number conversion.  Example:
```
let nr = str2nr('0123')

```

When {base} is 16 a leading "0x" or "0X" is ignored.  With a
different base the result will be zero. Similarly, when
{base} is 8 a leading "0", "0o" or "0O" is ignored, and when
{base} is 2 a leading "0b" or "0B" is ignored.
Text after the number is silently ignored.

Returns 0 if {string} is empty or on error.

Can also be used as a [method](#method):
```
GetText()->str2nr()

### <a id="strcharpart()" class="section-title" href="#strcharpart()">strcharpart({src}, {start} [, {len}])</a>
Like [strpart()](#strpart()) but using character index and length instead
of byte index and length.  Composing characters are counted
separately.
When a character index is used where a character does not
exist it is assumed to be one character.  For example:
```
strcharpart('abc', -1, 2)

```
		results in 'a'.

Returns an empty string on error.

Can also be used as a [method](#method):
```
GetText()->strcharpart(5)

### <a id="strchars()" class="section-title" href="#strchars()">strchars({string} [, {skipcc}])</a>
The result is a Number, which is the number of characters
in String {string}.
When {skipcc} is omitted or zero, composing characters are
counted separately.
When {skipcc} set to 1, Composing characters are ignored.

Returns zero on error.

Also see [strlen()|, |strdisplaywidth()| and |strwidth()](#strlen()|, |strdisplaywidth()| and |strwidth()).

{skipcc} is only available after 7.4.755.  For backward
compatibility, you can define a wrapper function:
```
if has("patch-7.4.755")
function s:strchars(str, skipcc)
return strchars(a:str, a:skipcc)
endfunction
else
function s:strchars(str, skipcc)
if a:skipcc
return strlen(substitute(a:str, ".", "x", "g"))
else
return strchars(a:str)
endif
endfunction
endif

```

Can also be used as a [method](#method):
```
GetText()->strchars()

### <a id="strdisplaywidth()" class="section-title" href="#strdisplaywidth()">strdisplaywidth({string} [, {col}])</a>
The result is a Number, which is the number of display cells
String {string} occupies on the screen when it starts at {col}
(first column is zero).  When {col} is omitted zero is used.
Otherwise it is the screen column where to start.  This
matters for Tab characters.
The option settings of the current window are used.  This
matters for anything that's displayed differently, such as
'tabstop' and 'display'.
When {string} contains characters with East Asian Width Class
Ambiguous, this function's return value depends on 'ambiwidth'.
Returns zero on error.
Also see [strlen()|, |strwidth()| and |strchars()](#strlen()|, |strwidth()| and |strchars()).

Can also be used as a [method](#method):
```
GetText()->strdisplaywidth()

### <a id="strftime()" class="section-title" href="#strftime()">strftime({format} [, {time}])</a>
The result is a String, which is a formatted date and time, as
specified by the {format} string.  The given {time} is used,
or the current time if no time is given.  The accepted
{format} depends on your system, thus this is not portable!
See the manual page of the C function strftime() for the
format.  The maximum length of the result is 80 characters.
See also [localtime()|, |getftime()| and |strptime()](#localtime()|, |getftime()| and |strptime()).
The language can be changed with the [:language](#:language) command.
Examples:
```
:echo strftime("%c")		   Sun Apr 27 11:49:23 1997
:echo strftime("%Y %b %d %X")	   1997 Apr 27 11:53:25
:echo strftime("%y%m%d %T")	   970427 11:53:55
:echo strftime("%H:%M")	   11:55
:echo strftime("%c", getftime("file.c"))
Show mod time of file.c.


```
		Can also be used as a [method](#method):
```
GetFormat()->strftime()

### <a id="strgetchar()" class="section-title" href="#strgetchar()">strgetchar({str}, {index})</a>
Get a Number corresponding to the character at {index} in
{str}.  This uses a zero-based character index, not a byte
index.  Composing characters are considered separate
characters here.  Use [nr2char()](#nr2char()) to convert the Number to a
String.
Returns -1 if {index} is invalid.
Also see [strcharpart()| and |strchars()](#strcharpart()| and |strchars()).

Can also be used as a [method](#method):
```
GetText()->strgetchar(5)

### <a id="stridx()" class="section-title" href="#stridx()">stridx({haystack}, {needle} [, {start}])</a>
The result is a Number, which gives the byte index in
{haystack} of the first occurrence of the String {needle}.
If {start} is specified, the search starts at index {start}.
This can be used to find a second match:
```
:let colon1 = stridx(line, ":")
:let colon2 = stridx(line, ":", colon1 + 1)

```
		The search is done case-sensitive.
For pattern searches use [match()](#match()).
-1 is returned if the {needle} does not occur in {haystack}.
See also [strridx()](#strridx()).
Examples:
```
:echo stridx("An Example", "Example")	     3
:echo stridx("Starting point", "Start")    0
:echo stridx("Starting point", "start")   -1
### <a id="strstr() strchr()" class="section-title" href="#strstr() strchr()"><</a>
stridx() works similar to the C function strstr().  When used
with a single character it works similar to strchr().

Can also be used as a [method](#method):
```
GetHaystack()->stridx(needle)

### <a id="string()" class="section-title" href="#string()">Note:</a>
string({expr})	Return {expr} converted to a String.  If {expr} is a Number,
Float, String, Blob or a composition of them, then the result
can be parsed back with [eval()](#eval()).
{expr} type	result ~
String		'string'
Number		123
Float		123.123456 or 1.123456e8 or
`str2float('inf')`
Funcref		`function('name')`
Blob		0z00112233.44556677.8899
List		[item, item]
Dictionary	{key: value, key: value}
Note that in String values the ' character is doubled.
Also see [strtrans()](#strtrans()).
Note 2: Output format is mostly compatible with YAML, except
for infinite and NaN floating-point values representations
which use [str2float()](#str2float()).  Strings are also dumped literally,
only single quote is escaped, which does not allow using YAML
for parsing back binary strings.  [eval()](#eval()) should always work for
strings and floats though and this is the only official
method, use [msgpackdump()| or |json_encode()](#msgpackdump()| or |json_encode()) if you need to
share data with other application.

Can also be used as a [method](#method):
```
mylist->string()

### <a id="strlen()" class="section-title" href="#strlen()">strlen({string})</a>
The result is a Number, which is the length of the String
{string} in bytes.
If the argument is a Number it is first converted to a String.
For other types an error is given and zero is returned.
If you want to count the number of multibyte characters use
[strchars()](#strchars()).
Also see [len()|, |strdisplaywidth()| and |strwidth()](#len()|, |strdisplaywidth()| and |strwidth()).

Can also be used as a [method](#method):
```
GetString()->strlen()

### <a id="strpart()" class="section-title" href="#strpart()">strpart({src}, {start} [, {len} [, {chars}]])</a>
The result is a String, which is part of {src}, starting from
byte {start}, with the byte length {len}.
When {chars} is present and TRUE then {len} is the number of
characters positions (composing characters are not counted
separately, thus "1" means one base character and any
following composing characters).
To count {start} as characters instead of bytes use
[strcharpart()](#strcharpart()).

When bytes are selected which do not exist, this doesn't
result in an error, the bytes are simply omitted.
If {len} is missing, the copy continues from {start} till the
end of the {src}.
```
strpart("abcdefg", 3, 2)    == "de"
strpart("abcdefg", -2, 4)   == "ab"
strpart("abcdefg", 5, 4)    == "fg"
strpart("abcdefg", 3)	    == "defg"


```
		Note: To get the first character, {start} must be 0.  For
example, to get the character under the cursor:
```
strpart(getline("."), col(".") - 1, 1, v:true)

```

Returns an empty string on error.

Can also be used as a [method](#method):
```
GetText()->strpart(5)

### <a id="strptime()" class="section-title" href="#strptime()">strptime({format}, {timestring})</a>
The result is a Number, which is a unix timestamp representing
the date and time in {timestring}, which is expected to match
the format specified in {format}.

The accepted {format} depends on your system, thus this is not
portable!  See the manual page of the C function strptime()
for the format.  Especially avoid "%c".  The value of $TZ also
matters.

If the {timestring} cannot be parsed with {format} zero is
returned.  If you do not know the format of {timestring} you
can try different {format} values until you get a non-zero
result.

See also [strftime()](#strftime()).
Examples:
```
:echo strptime("%Y %b %d %X", "1997 Apr 27 11:49:23")

```
		  862156163
```
:echo strftime("%c", strptime("%y%m%d %T", "970427 11:53:55"))

```
		  Sun Apr 27 11:53:55 1997
```
:echo strftime("%c", strptime("%Y%m%d%H%M%S", "19970427115355") + 3600)

```
		  Sun Apr 27 12:53:55 1997

Can also be used as a [method](#method):
```
GetFormat()->strptime(timestring)

```

### <a id="strridx()" class="section-title" href="#strridx()">strridx({haystack}, {needle} [, {start}])</a>
The result is a Number, which gives the byte index in
{haystack} of the last occurrence of the String {needle}.
When {start} is specified, matches beyond this index are
ignored.  This can be used to find a match before a previous
match:
```
:let lastcomma = strridx(line, ",")
:let comma2 = strridx(line, ",", lastcomma - 1)

```
		The search is done case-sensitive.
For pattern searches use [match()](#match()).
-1 is returned if the {needle} does not occur in {haystack}.
If the {needle} is empty the length of {haystack} is returned.
See also [stridx()](#stridx()).  Examples:
```
:echo strridx("an angry armadillo", "an")	     3
### <a id="strrchr()" class="section-title" href="#strrchr()"><</a>
When used with a single character it works similar to the C
function strrchr().

Can also be used as a [method](#method):
```
GetHaystack()->strridx(needle)

### <a id="strtrans()" class="section-title" href="#strtrans()">strtrans({string})</a>
The result is a String, which is {string} with all unprintable
characters translated into printable characters ['isprint'](#'isprint').
Like they are shown in a window.  Example:
```
echo strtrans(@a)

```
		This displays a newline in register a as "^@" instead of
starting a new line.

Returns an empty string on error.

Can also be used as a [method](#method):
```
GetString()->strtrans()

### <a id="strwidth()" class="section-title" href="#strwidth()">strwidth({string})</a>
The result is a Number, which is the number of display cells
String {string} occupies.  A Tab character is counted as one
cell, alternatively use [strdisplaywidth()](#strdisplaywidth()).
When {string} contains characters with East Asian Width Class
Ambiguous, this function's return value depends on 'ambiwidth'.
Returns zero on error.
Also see [strlen()|, |strdisplaywidth()| and |strchars()](#strlen()|, |strdisplaywidth()| and |strchars()).

Can also be used as a [method](#method):
```
GetString()->strwidth()

### <a id="submatch() E935" class="section-title" href="#submatch() E935">submatch({nr} [, {list}])</a>
Only for an expression in a [:substitute](#:substitute) command or
substitute() function.
Returns the {nr}'th submatch of the matched text.  When {nr}
is 0 the whole matched text is returned.
Note that a NL in the string can stand for a line break of a
multi-line match or a NUL character in the text.
Also see [sub-replace-expression](#sub-replace-expression).

If {list} is present and non-zero then submatch() returns
a list of strings, similar to [getline()](#getline()) with two arguments.
NL characters in the text represent NUL characters in the
text.
Only returns more than one item for [:substitute](#:substitute), inside
[substitute()](#substitute()) this list will always contain one or zero
items, since there are no real line breaks.

When substitute() is used recursively only the submatches in
the current (deepest) call can be obtained.

Returns an empty string or list on error.

Examples:
```
:s/\d\+/\=submatch(0) + 1/
:echo substitute(text, '\d\+', '\=submatch(0) + 1', '')

```
		This finds the first number in the line and adds one to it.
A line break is included as a newline character.

Can also be used as a [method](#method):
```
GetNr()->submatch()

### <a id="substitute()" class="section-title" href="#substitute()">substitute({string}, {pat}, {sub}, {flags})</a>
The result is a String, which is a copy of {string}, in which
the first match of {pat} is replaced with {sub}.
When {flags} is "g", all matches of {pat} in {string} are
replaced.  Otherwise {flags} should be "".

This works like the ":substitute" command (without any flags).
But the matching with {pat} is always done like the 'magic'
option is set and 'cpoptions' is empty (to make scripts
portable).  'ignorecase' is still relevant, use [/\c| or |/\C](#/\c| or |/\C)
if you want to ignore or match case and ignore 'ignorecase'.
'smartcase' is not used.  See [string-match](#string-match) for how {pat} is
used.

A "~" in {sub} is not replaced with the previous {sub}.
Note that some codes in {sub} have a special meaning
[sub-replace-special](#sub-replace-special).  For example, to replace something with
"\n" (two characters), use "\\\\n" or '\\n'.

When {pat} does not match in {string}, {string} is returned
unmodified.

Example:
```
### <a id=":let &path = substitute(&path, ",\\=[^,]$", "", "")" class="section-title" href="#:let &path = substitute(&path, ",\\=[^,]$", "", "")">Note:</a>

```
		This removes the last component of the 'path' option.
```
### <a id=":echo substitute("testing", ".", "\\U\\0", "")" class="section-title" href="#:echo substitute("testing", ".", "\\U\\0", "")">Note:</a>

```
		results in "TESTING".

When {sub} starts with "\=", the remainder is interpreted as
an expression. See [sub-replace-expression](#sub-replace-expression).  Example:
```
:echo substitute(s, '%\(\x\x\)',
\ '\=nr2char("0x" .. submatch(1))', 'g')


```
		When {sub} is a Funcref that function is called, with one
optional argument.  Example:
```
:echo substitute(s, '%\(\x\x\)', SubNr, 'g')

```
		The optional argument is a list which contains the whole
matched string and up to nine submatches, like what
[submatch()](#submatch()) returns.  Example:
```
:echo substitute(s, '%\(\x\x\)', {m -> '0x' .. m[1]}, 'g')


```
		Returns an empty string on error.

Can also be used as a [method](#method):
```
GetString()->substitute(pat, sub, flags)

### <a id="swapinfo()" class="section-title" href="#swapinfo()">swapinfo({fname})</a>
The result is a dictionary, which holds information about the
swapfile {fname}. The available fields are:
version Vim version
user	user name
host	host name
fname	original file name
pid	PID of the Vim process that created the swap
file
mtime	last modification time in seconds
inode	Optional: INODE number of the file
dirty	1 if file was modified, 0 if not
In case of failure an "error" item is added with the reason:
Cannot open file: file not found or in accessible
Cannot read file: cannot read first block
Not a swap file: does not contain correct block ID
Magic number mismatch: Info in first block is invalid

Can also be used as a [method](#method):
```
GetFilename()->swapinfo()

### <a id="swapname()" class="section-title" href="#swapname()">swapname({buf})</a>
The result is the swap file path of the buffer {buf}.
For the use of {buf}, see [bufname()](#bufname()) above.
If buffer {buf} is the current buffer, the result is equal to
[:swapname](#:swapname) (unless there is no swap file).
If buffer {buf} has no swap file, returns an empty string.

Can also be used as a [method](#method):
```
GetBufname()->swapname()

### <a id="synID()" class="section-title" href="#synID()">synID({lnum}, {col}, {trans})</a>
The result is a Number, which is the syntax ID at the position
{lnum} and {col} in the current window.
The syntax ID can be used with [synIDattr()](#synIDattr()) and
[synIDtrans()](#synIDtrans()) to obtain syntax information about text.

{col} is 1 for the leftmost column, {lnum} is 1 for the first
line.  'synmaxcol' applies, in a longer line zero is returned.
Note that when the position is after the last character,
that's where the cursor can be in Insert mode, synID() returns
zero.  {lnum} is used like with [getline()](#getline()).

When {trans} is [TRUE](#TRUE), transparent items are reduced to the
item that they reveal.  This is useful when wanting to know
the effective color.  When {trans} is [FALSE](#FALSE), the transparent
item is returned.  This is useful when wanting to know which
syntax item is effective (e.g. inside parens).
Warning: This function can be very slow.  Best speed is
obtained by going through the file in forward direction.

Returns zero on error.

Example (echoes the name of the syntax item under the cursor):
```
:echo synIDattr(synID(line("."), col("."), 1), "name")

```


### <a id="synIDattr()" class="section-title" href="#synIDattr()">synIDattr({synID}, {what} [, {mode}])</a>
The result is a String, which is the {what} attribute of
syntax ID {synID}.  This can be used to obtain information
about a syntax item.
{mode} can be "gui" or "cterm", to get the attributes
for that mode.  When {mode} is omitted, or an invalid value is
used, the attributes for the currently active highlighting are
used (GUI or cterm).
Use synIDtrans() to follow linked highlight groups.
{what}		result
"name"		the name of the syntax item
"fg"		foreground color (GUI: color name used to set
the color, cterm: color number as a string,
term: empty string)
"bg"		background color (as with "fg")
"font"		font name (only available in the GUI)
[highlight-font](#highlight-font)
"sp"		special color (as with "fg") [guisp](#guisp)
"fg#"		like "fg", but for the GUI and the GUI is
running the name in "#RRGGBB" form
"bg#"		like "fg#" for "bg"
"sp#"		like "fg#" for "sp"
"bold"		"1" if bold
"italic"	"1" if italic
"reverse"	"1" if reverse
"inverse"	"1" if inverse (= reverse)
"standout"	"1" if standout
"underline"	"1" if underlined
"undercurl"	"1" if undercurled
"underdouble"	"1" if double underlined
"underdotted"	"1" if dotted underlined
"underdashed"	"1" if dashed underlined
"strikethrough"	"1" if struckthrough
"nocombine"	"1" if nocombine

Returns an empty string on error.

Example (echoes the color of the syntax item under the
cursor):
```
:echo synIDattr(synIDtrans(synID(line("."), col("."), 1)), "fg")

```

Can also be used as a [method](#method):
```
:echo synID(line("."), col("."), 1)->synIDtrans()->synIDattr("fg")

### <a id="synIDtrans()" class="section-title" href="#synIDtrans()">synIDtrans({synID})</a>
The result is a Number, which is the translated syntax ID of
{synID}.  This is the syntax group ID of what is being used to
highlight the character.  Highlight links given with
":highlight link" are followed.

Returns zero on error.

Can also be used as a [method](#method):
```
:echo synID(line("."), col("."), 1)->synIDtrans()->synIDattr("fg")

### <a id="synconcealed()" class="section-title" href="#synconcealed()">synconcealed({lnum}, {col})</a>
The result is a [List](#List) with currently three items:
1. The first item in the list is 0 if the character at the
position {lnum} and {col} is not part of a concealable
region, 1 if it is.  {lnum} is used like with [getline()](#getline()).
2. The second item in the list is a string. If the first item
is 1, the second item contains the text which will be
displayed in place of the concealed text, depending on the
current setting of 'conceallevel' and 'listchars'.
3. The third and final item in the list is a number
representing the specific syntax region matched in the
line. When the character is not concealed the value is
zero. This allows detection of the beginning of a new
concealable region if there are two consecutive regions
with the same replacement character.  For an example, if
the text is "123456" and both "23" and "45" are concealed
and replaced by the character "X", then:
call			returns ~
synconcealed(lnum, 1)   [0, '', 0]
synconcealed(lnum, 2)   [1, 'X', 1]
synconcealed(lnum, 3)   [1, 'X', 1]
synconcealed(lnum, 4)   [1, 'X', 2]
synconcealed(lnum, 5)   [1, 'X', 2]
synconcealed(lnum, 6)   [0, '', 0]


### <a id="synstack()" class="section-title" href="#synstack()">synstack({lnum}, {col})</a>
Return a [List](#List), which is the stack of syntax items at the
position {lnum} and {col} in the current window.  {lnum} is
used like with [getline()](#getline()).  Each item in the List is an ID
like what [synID()](#synID()) returns.
The first item in the List is the outer region, following are
items contained in that one.  The last one is what [synID()](#synID())
returns, unless not the whole item is highlighted or it is a
transparent item.
This function is useful for debugging a syntax file.
Example that shows the syntax stack under the cursor:
```
for id in synstack(line("."), col("."))
echo synIDattr(id, "name")
endfor

```
		When the position specified with {lnum} and {col} is invalid
an empty list is returned.  The position just after the last
character in a line and the first column in an empty line are
valid positions.

### <a id="system() E677" class="section-title" href="#system() E677">system({cmd} [, {input}])</a>
Gets the output of {cmd} as a [string| (|systemlist()](#string| (|systemlist()) returns
a [List|) and sets |v:shell_error](#List|) and sets |v:shell_error) to the error code.
{cmd} is treated as in [jobstart()](#jobstart()):
If {cmd} is a List it runs directly (no 'shell').
If {cmd} is a String it runs in the 'shell', like this:
```
:call jobstart(split(&shell) + split(&shellcmdflag) + ['{cmd}'])


```
		Not to be used for interactive commands.

Result is a String, filtered to avoid platform-specific quirks:
- <CR><NL> is replaced with <NL>
- NUL characters are replaced with SOH (0x01)

Example:
```
:echo system(['ls', expand('%:h')])


```
		If {input} is a string it is written to a pipe and passed as
stdin to the command.  The string is written as-is, line
separators are not changed.
If {input} is a [List](#List) it is written to the pipe as
[writefile()](#writefile()) does with {binary} set to "b" (i.e. with
a newline between each list item, and newlines inside list
items converted to NULs).
When {input} is given and is a valid buffer id, the content of
the buffer is written to the file line by line, each line
terminated by NL (and NUL where the text has NL).
### <a id="E5677" class="section-title" href="#E5677">Note:</a>
Note: system() cannot write to or read from backgrounded ("&")
shell commands, e.g.:
```
:echo system("cat - &", "foo")

```
		which is equivalent to:
```
$ echo foo | bash -c 'cat - &'

```
		The pipes are disconnected (unless overridden by shell
redirection syntax) before input can reach it. Use
[jobstart()](#jobstart()) instead.

Note: Use [shellescape()| or |::S| with |expand()](#shellescape()| or |::S| with |expand()) or
[fnamemodify()](#fnamemodify()) to escape special characters in a command
argument. 'shellquote' and 'shellxquote' must be properly
configured. Example:
```
:echo system('ls '..shellescape(expand('%:h')))
:echo system('ls '..expand('%:h:S'))


```
		Unlike ":!cmd" there is no automatic check for changed files.
Use [:checktime](#:checktime) to force a check.

Can also be used as a [method](#method):
```
:echo GetCmd()->system()

### <a id="systemlist()" class="section-title" href="#systemlist()">systemlist({cmd} [, {input} [, {keepempty}]])</a>
Same as [system()|, but returns a |List](#system()|, but returns a |List) with lines (parts of
output separated by NL) with NULs transformed into NLs. Output
is the same as [readfile()](#readfile()) will output with {binary} argument
set to "b", except that a final newline is not preserved,
unless {keepempty} is non-zero.
Note that on MS-Windows you may get trailing CR characters.

To see the difference between "echo hello" and "echo -n hello"
use [system()| and |split()](#system()| and |split()):
```
echo split(system('echo hello'), '\n', 1)

```

Returns an empty string on error.

Can also be used as a [method](#method):
```
:echo GetCmd()->systemlist()

### <a id="tabpagebuflist()" class="section-title" href="#tabpagebuflist()">tabpagebuflist([{arg}])</a>
The result is a [List](#List), where each item is the number of the
buffer associated with each window in the current tab page.
{arg} specifies the number of the tab page to be used. When
omitted the current tab page is used.
When {arg} is invalid the number zero is returned.
To get a list of all buffers in all tabs use this:
```
let buflist = []
for i in range(tabpagenr('$'))
call extend(buflist, tabpagebuflist(i + 1))
endfor

```
		Note that a buffer may appear in more than one window.

Can also be used as a [method](#method):
```
GetTabpage()->tabpagebuflist()

### <a id="tabpagenr()" class="section-title" href="#tabpagenr()">tabpagenr([{arg}])</a>
The result is a Number, which is the number of the current
tab page.  The first tab page has number 1.

The optional argument {arg} supports the following values:
$	the number of the last tab page (the tab page
count).
#	the number of the last accessed tab page
(where [g<Tab>](#g<Tab>) goes to).  If there is no
previous tab page, 0 is returned.
The number can be used with the [:tab](#:tab) command.

Returns zero on error.

### <a id="tabpagewinnr()" class="section-title" href="#tabpagewinnr()">tabpagewinnr({tabarg} [, {arg}])</a>
Like [winnr()](#winnr()) but for tab page {tabarg}.
{tabarg} specifies the number of tab page to be used.
{arg} is used like with [winnr()](#winnr()):
- When omitted the current window number is returned.  This is
the window which will be used when going to this tab page.
- When "$" the number of windows is returned.
- When "#" the previous window nr is returned.
Useful examples:
```
tabpagewinnr(1)	    " current window of tab page 1
tabpagewinnr(4, '$')    " number of windows in tab page 4

```
		When {tabarg} is invalid zero is returned.

Can also be used as a [method](#method):
```
GetTabpage()->tabpagewinnr()

```

### <a id="tagfiles()" class="section-title" href="#tagfiles()">Note:</a>
tagfiles()	Returns a [List](#List) with the file names used to search for tags
for the current buffer.  This is the 'tags' option expanded.


### <a id="taglist()" class="section-title" href="#taglist()">taglist({expr} [, {filename}])</a>
Returns a [List](#List) of tags matching the regular expression {expr}.

If {filename} is passed it is used to prioritize the results
in the same way that [:tselect| does. See |tag-priority](#:tselect| does. See |tag-priority).
{filename} should be the full path of the file.

Each list item is a dictionary with at least the following
entries:
name		Name of the tag.
filename	Name of the file where the tag is
defined.  It is either relative to the
current directory or a full path.
cmd		Ex command used to locate the tag in
the file.
kind		Type of the tag.  The value for this
entry depends on the language specific
kind values.  Only available when
using a tags file generated by
Universal/Exuberant ctags or hdrtag.
static		A file specific tag.  Refer to
[static-tag](#static-tag) for more information.
More entries may be present, depending on the content of the
tags file: access, implementation, inherits and signature.
Refer to the ctags documentation for information about these
fields.  For C code the fields "struct", "class" and "enum"
may appear, they give the name of the entity the tag is
contained in.

The ex-command "cmd" can be either an ex search pattern, a
line number or a line number followed by a byte number.

If there are no matching tags, then an empty list is returned.

To get an exact tag match, the anchors '^' and '$' should be
used in {expr}.  This also make the function work faster.
Refer to [tag-regexp](#tag-regexp) for more information about the tag
search regular expression pattern.

Refer to ['tags'](#'tags') for information about how the tags file is
located by Vim. Refer to [tags-file-format](#tags-file-format) for the format of
the tags file generated by the different ctags tools.

Can also be used as a [method](#method):
```
GetTagpattern()->taglist()

### <a id="tempname() temp-file-name" class="section-title" href="#tempname() temp-file-name">tempname()</a>
The result is a String, which is the name of a file that
doesn't exist.  It can be used for a temporary file.  Example:
```
:let tmpfile = tempname()
:exe "redir > " .. tmpfile

```
		For Unix, the file will be in a private directory [tempfile](#tempfile).
For MS-Windows forward slashes are used when the 'shellslash'
option is set or when 'shellcmdflag' starts with '-'.

### <a id="termopen()" class="section-title" href="#termopen()">termopen({cmd} [, {opts}])</a>
Spawns {cmd} in a new pseudo-terminal session connected
to the current (unmodified) buffer. Parameters and behavior
are the same as [jobstart()](#jobstart()) except "pty", "width", "height",
and "TERM" are ignored: "height" and "width" are taken from
the current window.
Returns the same values as [jobstart()](#jobstart()).

Terminal environment is initialized as in [|jobstart-env](#|jobstart-env),
except $TERM is set to "xterm-256color". Full behavior is
described in [terminal](#terminal).

### <a id="tan()" class="section-title" href="#tan()">tan({expr})</a>
Return the tangent of {expr}, measured in radians, as a [Float](#Float)
in the range [-inf, inf].
{expr} must evaluate to a [Float| or a |Number](#Float| or a |Number).
Returns 0.0 if {expr} is not a [Float| or a |Number](#Float| or a |Number).
Examples:
```
:echo tan(10)

```
			0.648361
```
:echo tan(-4.01)

```
			-1.181502

Can also be used as a [method](#method):
```
Compute()->tan()

### <a id="tanh()" class="section-title" href="#tanh()">tanh({expr})</a>
Return the hyperbolic tangent of {expr} as a [Float](#Float) in the
range [-1, 1].
{expr} must evaluate to a [Float| or a |Number](#Float| or a |Number).
Returns 0.0 if {expr} is not a [Float| or a |Number](#Float| or a |Number).
Examples:
```
:echo tanh(0.5)

```
			0.462117
```
:echo tanh(-1)

```
			-0.761594

Can also be used as a [method](#method):
```
Compute()->tanh()

```

### <a id="timer_info()" class="section-title" href="#timer_info()">Note:</a>
timer_info([{id}])
Return a list with information about timers.
When {id} is given only information about this timer is
returned.  When timer {id} does not exist an empty list is
returned.
When {id} is omitted information about all timers is returned.

For each timer the information is stored in a [Dictionary](#Dictionary) with
these items:
"id"	    the timer ID
"time"	    time the timer was started with
"repeat"	    number of times the timer will still fire;
-1 means forever
"callback"	    the callback

Can also be used as a [method](#method):
```
GetTimer()->timer_info()

```

### <a id="timer_pause()" class="section-title" href="#timer_pause()">timer_pause({timer}, {paused})</a>
Pause or unpause a timer.  A paused timer does not invoke its
callback when its time expires.  Unpausing a timer may cause
the callback to be invoked almost immediately if enough time
has passed.

Pausing a timer is useful to avoid the callback to be called
for a short time.

If {paused} evaluates to a non-zero Number or a non-empty
String, then the timer is paused, otherwise it is unpaused.
See [non-zero-arg](#non-zero-arg).

Can also be used as a [method](#method):
```
GetTimer()->timer_pause(1)

```

### <a id="timer_start() timer timers" class="section-title" href="#timer_start() timer timers">Note:</a>
timer_start({time}, {callback} [, {options}])
Create a timer and return the timer ID.

{time} is the waiting time in milliseconds. This is the
minimum time before invoking the callback.  When the system is
busy or Vim is not waiting for input the time will be longer.

{callback} is the function to call.  It can be the name of a
function or a [Funcref](#Funcref).  It is called with one argument, which
is the timer ID.  The callback is only invoked when Vim is
waiting for input.

{options} is a dictionary.  Supported entries:
"repeat"	Number of times to repeat the callback.
-1 means forever.  Default is 1.
If the timer causes an error three times in a
row the repeat is cancelled.

Returns -1 on error.

Example:
```
func MyHandler(timer)
echo 'Handler called'
endfunc
let timer = timer_start(500, 'MyHandler',
\ {'repeat': 3})

```
		This invokes MyHandler() three times at 500 msec intervals.

Can also be used as a [method](#method):
```
GetMsec()->timer_start(callback)


```
		Not available in the [sandbox](#sandbox).

### <a id="timer_stop()" class="section-title" href="#timer_stop()">timer_stop({timer})</a>
Stop a timer.  The timer callback will no longer be invoked.
{timer} is an ID returned by timer_start(), thus it must be a
Number.  If {timer} does not exist there is no error.

Can also be used as a [method](#method):
```
GetTimer()->timer_stop()

```

### <a id="timer_stopall()" class="section-title" href="#timer_stopall()">timer_stopall()</a>
Stop all timers.  The timer callbacks will no longer be
invoked.  Useful if some timers is misbehaving.  If there are
no timers there is no error.

### <a id="tolower()" class="section-title" href="#tolower()">tolower({expr})</a>
The result is a copy of the String given, with all uppercase
characters turned into lowercase (just like applying [gu](#gu) to
the string).  Returns an empty string on error.

Can also be used as a [method](#method):
```
GetText()->tolower()

### <a id="toupper()" class="section-title" href="#toupper()">toupper({expr})</a>
The result is a copy of the String given, with all lowercase
characters turned into uppercase (just like applying [gU](#gU) to
the string).  Returns an empty string on error.

Can also be used as a [method](#method):
```
GetText()->toupper()

### <a id="tr()" class="section-title" href="#tr()">tr({src}, {fromstr}, {tostr})</a>
The result is a copy of the {src} string with all characters
which appear in {fromstr} replaced by the character in that
position in the {tostr} string.  Thus the first character in
{fromstr} is translated into the first character in {tostr}
and so on.  Exactly like the unix "tr" command.
This code also deals with multibyte characters properly.

Returns an empty string on error.

Examples:
```
echo tr("hello there", "ht", "HT")

```
		returns "Hello THere"
```
echo tr("<blob>", "<>", "{}")

```
		returns "{blob}"

Can also be used as a [method](#method):
```
GetText()->tr(from, to)

### <a id="trim()" class="section-title" href="#trim()">trim({text} [, {mask} [, {dir}]])</a>
Return {text} as a String where any character in {mask} is
removed from the beginning and/or end of {text}.
If {mask} is not given, {mask} is all characters up to 0x20,
which includes Tab, space, NL and CR, plus the non-breaking
space character 0xa0.
The optional {dir} argument specifies where to remove the
characters:
0	remove from the beginning and end of {text}
1	remove only at the beginning of {text}
2	remove only at the end of {text}
When omitted both ends are trimmed.
This function deals with multibyte characters properly.
Returns an empty string on error.

Examples:
```
echo trim("   some text ")

```
		returns "some text"
```
echo trim("  \r\t\t\r RESERVE \t\n\x0B\xA0") .. "_TAIL"

```
		returns "RESERVE_TAIL"
```
echo trim("rm<Xrm<>X>rrm", "rm<>")

```
		returns "Xrm<>X" (characters in the middle are not removed)
```
echo trim("  vim  ", " ", 2)

```
		returns "  vim"

Can also be used as a [method](#method):
```
GetText()->trim()

### <a id="trunc()" class="section-title" href="#trunc()">trunc({expr})</a>
Return the largest integral value with magnitude less than or
equal to {expr} as a [Float](#Float) (truncate towards zero).
{expr} must evaluate to a [Float| or a |Number](#Float| or a |Number).
Returns 0.0 if {expr} is not a [Float| or a |Number](#Float| or a |Number).
Examples:
```
echo trunc(1.456)

```
			1.0
```
echo trunc(-5.456)

```
			-5.0
```
echo trunc(4.0)

```
			4.0

Can also be used as a [method](#method):
```
Compute()->trunc()

### <a id="type()" class="section-title" href="#type()">type({expr})</a>
The result is a Number representing the type of {expr}.
Instead of using the number directly, it is better to use the
v:t_ variable that has the value:
Number:     0 ([v:t_number](#v:t_number))
String:     1 ([v:t_string](#v:t_string))
Funcref:    2 ([v:t_func](#v:t_func))
List:       3 ([v:t_list](#v:t_list))
Dictionary: 4 ([v:t_dict](#v:t_dict))
Float:      5 ([v:t_float](#v:t_float))
Boolean:    6 ([v:true| and |v:false](#v:true| and |v:false))
Null:       7 ([v:null](#v:null))
Blob:      10 ([v:t_blob](#v:t_blob))
For backward compatibility, this method can be used:
```
:if type(myvar) == type(0)
:if type(myvar) == type("")
:if type(myvar) == type(function("tr"))
:if type(myvar) == type([])
:if type(myvar) == type({})
:if type(myvar) == type(0.0)
:if type(myvar) == type(v:true)

```
		In place of checking for [v:null](#v:null) type it is better to check
for [v:null](#v:null) directly as it is the only value of this type:
```
:if myvar is v:null

```
               To check if the v:t_ variables exist use this:
```
:if exists('v:t_number')


```
		Can also be used as a [method](#method):
```
mylist->type()

### <a id="undofile()" class="section-title" href="#undofile()">undofile({name})</a>
Return the name of the undo file that would be used for a file
with name {name} when writing.  This uses the 'undodir'
option, finding directories that exist.  It does not check if
the undo file exists.
{name} is always expanded to the full path, since that is what
is used internally.
If {name} is empty undofile() returns an empty string, since a
buffer without a file name will not write an undo file.
Useful in combination with [:wundo| and |:rundo](#:wundo| and |:rundo).

Can also be used as a [method](#method):
```
GetFilename()->undofile()

### <a id="undotree()" class="section-title" href="#undotree()">undotree()</a>
Return the current state of the undo tree in a dictionary with
the following items:
"seq_last"	The highest undo sequence number used.
"seq_cur"	The sequence number of the current position in
the undo tree.  This differs from "seq_last"
when some changes were undone.
"time_cur"	Time last used for [:earlier](#:earlier) and related
commands.  Use [strftime()](#strftime()) to convert to
something readable.
"save_last"	Number of the last file write.  Zero when no
write yet.
"save_cur"	Number of the current position in the undo
tree.
"synced"	Non-zero when the last undo block was synced.
This happens when waiting from input from the
user.  See [undo-blocks](#undo-blocks).
"entries"	A list of dictionaries with information about
undo blocks.

The first item in the "entries" list is the oldest undo item.
Each List item is a [Dictionary](#Dictionary) with these items:
"seq"		Undo sequence number.  Same as what appears in
[:undolist](#:undolist).
"time"	Timestamp when the change happened.  Use
[strftime()](#strftime()) to convert to something readable.
"newhead"	Only appears in the item that is the last one
that was added.  This marks the last change
and where further changes will be added.
"curhead"	Only appears in the item that is the last one
that was undone.  This marks the current
position in the undo tree, the block that will
be used by a redo command.  When nothing was
undone after the last change this item will
not appear anywhere.
"save"	Only appears on the last block before a file
write.  The number is the write count.  The
first write has number 1, the last one the
"save_last" mentioned above.
"alt"		Alternate entry.  This is again a List of undo
blocks.  Each item may again have an "alt"
item.

### <a id="uniq() E882" class="section-title" href="#uniq() E882">uniq({list} [, {func} [, {dict}]])</a>
Remove second and succeeding copies of repeated adjacent
{list} items in-place.  Returns {list}.  If you want a list
to remain unmodified make a copy first:
```
:let newlist = uniq(copy(mylist))

```
		The default compare function uses the string representation of
each item.  For the use of {func} and {dict} see [sort()](#sort()).

Returns zero if {list} is not a [List](#List).

Can also be used as a [method](#method):
```
mylist->uniq()

### <a id="values()" class="section-title" href="#values()">values({dict})</a>
Return a [List| with all the values of {dict}.  The |List](#List| with all the values of {dict}.  The |List) is
in arbitrary order.  Also see [items()| and |keys()](#items()| and |keys()).
Returns zero if {dict} is not a [Dict](#Dict).

Can also be used as a [method](#method):
```
mydict->values()

### <a id="virtcol()" class="section-title" href="#virtcol()">virtcol({expr})</a>
The result is a Number, which is the screen column of the file
position given with {expr}.  That is, the last screen position
occupied by the character at that position, when the screen
would be of unlimited width.  When there is a <Tab> at the
position, the returned Number will be the column at the end of
the <Tab>.  For example, for a <Tab> in column 1, with 'ts'
set to 8, it returns 8. [conceal](#conceal) is ignored.
For the byte position use [col()](#col()).
For the use of {expr} see [col()](#col()).
When 'virtualedit' is used {expr} can be [lnum, col, off], where
"off" is the offset in screen columns from the start of the
character.  E.g., a position within a <Tab> or after the last
character.  When "off" is omitted zero is used.
When Virtual editing is active in the current mode, a position
beyond the end of the line can be returned. ['virtualedit'](#'virtualedit')
The accepted positions are:
.	    the cursor position
$	    the end of the cursor line (the result is the
number of displayed characters in the cursor line
plus one)
'x	    position of mark x (if the mark is not set, 0 is
returned)
v       In Visual mode: the start of the Visual area (the
cursor is the end).  When not in Visual mode
returns the cursor position.  Differs from ['<](#'<) in
that it's updated right away.
Note that only marks in the current file can be used.
Examples:
```
virtcol(".")	   with text "foo^Lbar", with cursor on the "^L", returns 5
virtcol("$")	   with text "foo^Lbar", returns 9
virtcol("'t")    with text "	  there", with 't at 'h', returns 6

```
		The first column is 1.  0 is returned for an error.
A more advanced example that echoes the maximum length of
all lines:
```
echo max(map(range(1, line('$')), "virtcol([v:val, '$'])"))


```
		Can also be used as a [method](#method):
```
GetPos()->virtcol()

### <a id="virtcol2col()" class="section-title" href="#virtcol2col()">virtcol2col({winid}, {lnum}, {col})</a>
The result is a Number, which is the byte index of the
character in window {winid} at buffer line {lnum} and virtual
column {col}.

If {col} is greater than the last virtual column in line
{lnum}, then the byte index of the character at the last
virtual column is returned.

The {winid} argument can be the window number or the
[window-ID](#window-ID). If this is zero, then the current window is used.

Returns -1 if the window {winid} doesn't exist or the buffer
line {lnum} or virtual column {col} is invalid.

See also [screenpos()|, |virtcol()| and |col()](#screenpos()|, |virtcol()| and |col()).

Can also be used as a [method](#method):
```
GetWinid()->virtcol2col(lnum, col)

### <a id="visualmode()" class="section-title" href="#visualmode()">visualmode([{expr}])</a>
The result is a String, which describes the last Visual mode
used in the current buffer.  Initially it returns an empty
string, but once Visual mode has been used, it returns "v",
"V", or "<CTRL-V>" (a single CTRL-V character) for
character-wise, line-wise, or block-wise Visual mode
respectively.
Example:
```
:exe "normal " .. visualmode()

```
		This enters the same Visual mode as before.  It is also useful
in scripts if you wish to act differently depending on the
Visual mode that was used.
If Visual mode is active, use [mode()](#mode()) to get the Visual mode
(e.g., in a [:vmap](#:vmap)).
If {expr} is supplied and it evaluates to a non-zero Number or
a non-empty String, then the Visual mode will be cleared and
the old value is returned.  See [non-zero-arg](#non-zero-arg).

### <a id="wait()" class="section-title" href="#wait()">wait({timeout}, {condition} [, {interval}])</a>
Waits until {condition} evaluates to [TRUE](#TRUE), where {condition}
is a [Funcref| or |string](#Funcref| or |string) containing an expression.

{timeout} is the maximum waiting time in milliseconds, -1
means forever.

Condition is evaluated on user events, internal events, and
every {interval} milliseconds (default: 200).

Returns a status integer:
0 if the condition was satisfied before timeout
-1 if the timeout was exceeded
-2 if the function was interrupted (by [CTRL-C](#CTRL-C))
-3 if an error occurred

### <a id="wildmenumode()" class="section-title" href="#wildmenumode()">wildmenumode()</a>
Returns [TRUE| when the wildmenu is active and |FALSE](#TRUE| when the wildmenu is active and |FALSE)
otherwise.  See 'wildmenu' and 'wildmode'.
This can be used in mappings to handle the 'wildcharm' option
gracefully. (Makes only sense with [mapmode-c](#mapmode-c) mappings).

For example to make <c-j> work like <down> in wildmode, use:
```
:cnoremap <expr> <C-j> wildmenumode() ? "\<Down>\<Tab>" : "\<c-j>"

```

(Note, this needs the 'wildcharm' option set appropriately).

### <a id="win_execute()" class="section-title" href="#win_execute()">win_execute({id}, {command} [, {silent}])</a>
Like `execute()` but in the context of window {id}.
The window will temporarily be made the current window,
without triggering autocommands or changing directory.  When
executing {command} autocommands will be triggered, this may
have unexpected side effects.  Use [:noautocmd](#:noautocmd) if needed.
Example:
```
call win_execute(winid, 'syntax enable')

```

Can also be used as a [method](#method), the base is passed as the
second argument:
```
GetCommand()->win_execute(winid)

### <a id="win_findbuf()" class="section-title" href="#win_findbuf()">win_findbuf({bufnr})</a>
Returns a [List| with |window-ID](#List| with |window-ID)s for windows that contain
buffer {bufnr}.  When there is none the list is empty.

Can also be used as a [method](#method):
```
GetBufnr()->win_findbuf()

### <a id="win_getid()" class="section-title" href="#win_getid()">win_getid([{win} [, {tab}]])</a>
Get the [window-ID](#window-ID) for the specified window.
When {win} is missing use the current window.
With {win} this is the window number.  The top window has
number 1.
Without {tab} use the current tab, otherwise the tab with
number {tab}.  The first tab has number one.
Return zero if the window cannot be found.

Can also be used as a [method](#method):
```
GetWinnr()->win_getid()

### <a id="win_gettype()" class="section-title" href="#win_gettype()">win_gettype([{nr}])</a>
Return the type of the window:
"autocmd"	autocommand window. Temporary window
used to execute autocommands.
"command"	command-line window [cmdwin](#cmdwin)
(empty)		normal window
"loclist"	[location-list-window](#location-list-window)
"popup"		floating window [api-floatwin](#api-floatwin)
"preview"	preview window [preview-window](#preview-window)
"quickfix"	[quickfix-window](#quickfix-window)
"unknown"	window {nr} not found

When {nr} is omitted return the type of the current window.
When {nr} is given return the type of this window by number or
[window-ID](#window-ID).

Also see the 'buftype' option.

Can also be used as a [method](#method):
```
GetWinid()->win_gettype()

```

### <a id="win_gotoid()" class="section-title" href="#win_gotoid()">win_gotoid({expr})</a>
Go to window with ID {expr}.  This may also change the current
tabpage.
Return TRUE if successful, FALSE if the window cannot be found.

Can also be used as a [method](#method):
```
GetWinid()->win_gotoid()

### <a id="win_id2tabwin()" class="section-title" href="#win_id2tabwin()">win_id2tabwin({expr})</a>
Return a list with the tab number and window number of window
with ID {expr}: [tabnr, winnr].
Return [0, 0] if the window cannot be found.

Can also be used as a [method](#method):
```
GetWinid()->win_id2tabwin()

### <a id="win_id2win()" class="section-title" href="#win_id2win()">win_id2win({expr})</a>
Return the window number of window with ID {expr}.
Return 0 if the window cannot be found in the current tabpage.

Can also be used as a [method](#method):
```
GetWinid()->win_id2win()

### <a id="win_move_separator()" class="section-title" href="#win_move_separator()">win_move_separator({nr}, {offset})</a>
Move window {nr}'s vertical separator (i.e., the right border)
by {offset} columns, as if being dragged by the mouse. {nr}
can be a window number or [window-ID](#window-ID). A positive {offset}
moves right and a negative {offset} moves left. Moving a
window's vertical separator will change the width of the
window and the width of other windows adjacent to the vertical
separator. The magnitude of movement may be smaller than
specified (e.g., as a consequence of maintaining
'winminwidth'). Returns TRUE if the window can be found and
FALSE otherwise.
This will fail for the rightmost window and a full-width
window, since it has no separator on the right.

Can also be used as a [method](#method):
```
GetWinnr()->win_move_separator(offset)

### <a id="win_move_statusline()" class="section-title" href="#win_move_statusline()">win_move_statusline({nr}, {offset})</a>
Move window {nr}'s status line (i.e., the bottom border) by
{offset} rows, as if being dragged by the mouse. {nr} can be a
window number or [window-ID](#window-ID). A positive {offset} moves down
and a negative {offset} moves up. Moving a window's status
line will change the height of the window and the height of
other windows adjacent to the status line. The magnitude of
movement may be smaller than specified (e.g., as a consequence
of maintaining 'winminheight'). Returns TRUE if the window can
be found and FALSE otherwise.

Can also be used as a [method](#method):
```
GetWinnr()->win_move_statusline(offset)

### <a id="win_screenpos()" class="section-title" href="#win_screenpos()">win_screenpos({nr})</a>
Return the screen position of window {nr} as a list with two
numbers: [row, col].  The first window always has position
[1, 1], unless there is a tabline, then it is [2, 1].
{nr} can be the window number or the [window-ID](#window-ID).  Use zero
for the current window.
Returns [0, 0] if the window cannot be found in the current
tabpage.

Can also be used as a [method](#method):
```
GetWinid()->win_screenpos()

```

### <a id="win_splitmove()" class="section-title" href="#win_splitmove()">win_splitmove({nr}, {target} [, {options}])</a>
Move the window {nr} to a new split of the window {target}.
This is similar to moving to {target}, creating a new window
using [:split](#:split) but having the same contents as window {nr}, and
then closing {nr}.

Both {nr} and {target} can be window numbers or [window-ID](#window-ID)s.
Both must be in the current tab page.

Returns zero for success, non-zero for failure.

{options} is a [Dictionary](#Dictionary) with the following optional entries:
"vertical"	When TRUE, the split is created vertically,
like with [:vsplit](#:vsplit).
"rightbelow"	When TRUE, the split is made below or to the
right (if vertical).  When FALSE, it is done
above or to the left (if vertical).  When not
present, the values of 'splitbelow' and
'splitright' are used.

Can also be used as a [method](#method):
```
GetWinid()->win_splitmove(target)

```

### <a id="winbufnr()" class="section-title" href="#winbufnr()">Note:</a>
winbufnr({nr})	The result is a Number, which is the number of the buffer
associated with window {nr}.  {nr} can be the window number or
the [window-ID](#window-ID).
When {nr} is zero, the number of the buffer in the current
window is returned.
When window {nr} doesn't exist, -1 is returned.
Example:
```
:echo "The file in the current window is " .. bufname(winbufnr(0))

```

Can also be used as a [method](#method):
```
FindWindow()->winbufnr()->bufname()

```

### <a id="wincol()" class="section-title" href="#wincol()">Note:</a>
wincol()	The result is a Number, which is the virtual column of the
cursor in the window.  This is counting screen cells from the
left side of the window.  The leftmost column is one.

### <a id="windowsversion()" class="section-title" href="#windowsversion()">Note:</a>
windowsversion()
The result is a String.  For MS-Windows it indicates the OS
version.  E.g, Windows 10 is "10.0", Windows 8 is "6.2",
Windows XP is "5.1".  For non-MS-Windows systems the result is
an empty string.

### <a id="winheight()" class="section-title" href="#winheight()">winheight({nr})</a>
The result is a Number, which is the height of window {nr}.
{nr} can be the window number or the [window-ID](#window-ID).
When {nr} is zero, the height of the current window is
returned.  When window {nr} doesn't exist, -1 is returned.
An existing window always has a height of zero or more.
This excludes any window toolbar line.
Examples:
```
:echo "The current window has " .. winheight(0) .. " lines."


```
		Can also be used as a [method](#method):
```
GetWinid()->winheight()

```

### <a id="winlayout()" class="section-title" href="#winlayout()">winlayout([{tabnr}])</a>
The result is a nested List containing the layout of windows
in a tabpage.

Without {tabnr} use the current tabpage, otherwise the tabpage
with number {tabnr}. If the tabpage {tabnr} is not found,
returns an empty list.

For a leaf window, it returns:
["leaf", {winid}]
For horizontally split windows, which form a column, it
returns:
["col", [{nested list of windows}]]
For vertically split windows, which form a row, it returns:
["row", [{nested list of windows}]]

Example:
```
" Only one window in the tab page
:echo winlayout()
['leaf', 1000]
" Two horizontally split windows
:echo winlayout()
['col', [['leaf', 1000], ['leaf', 1001]]]
" The second tab page, with three horizontally split
" windows, with two vertically split windows in the
" middle window
:echo winlayout(2)
['col', [['leaf', 1002], ['row', [['leaf', 1003],
['leaf', 1001]]], ['leaf', 1000]]]

```

Can also be used as a [method](#method):
```
GetTabnr()->winlayout()

```

### <a id="winline()" class="section-title" href="#winline()">Note:</a>
winline()	The result is a Number, which is the screen line of the cursor
in the window.  This is counting screen lines from the top of
the window.  The first line is one.
If the cursor was moved the view on the file will be updated
first, this may cause a scroll.

### <a id="winnr()" class="section-title" href="#winnr()">Note:</a>
winnr([{arg}])	The result is a Number, which is the number of the current
window.  The top window has number 1.
Returns zero for a popup window.

The optional argument {arg} supports the following values:
$	the number of the last window (the window
count).
#	the number of the last accessed window (where
[CTRL-W_p](#CTRL-W_p) goes to).  If there is no previous
window or it is in another tab page 0 is
returned.
{N}j	the number of the Nth window below the
current window (where [CTRL-W_j](#CTRL-W_j) goes to).
{N}k	the number of the Nth window above the current
window (where [CTRL-W_k](#CTRL-W_k) goes to).
{N}h	the number of the Nth window left of the
current window (where [CTRL-W_h](#CTRL-W_h) goes to).
{N}l	the number of the Nth window right of the
current window (where [CTRL-W_l](#CTRL-W_l) goes to).
The number can be used with [CTRL-W_w](#CTRL-W_w) and ":wincmd w"
[:wincmd](#:wincmd).
When {arg} is invalid an error is given and zero is returned.
Also see [tabpagewinnr()| and |win_getid()](#tabpagewinnr()| and |win_getid()).
Examples:
```
let window_count = winnr('$')
let prev_window = winnr('#')
let wnum = winnr('3k')


```
		Can also be used as a [method](#method):
```
GetWinval()->winnr()

```

### <a id="winrestcmd()" class="section-title" href="#winrestcmd()">Note:</a>
winrestcmd()	Returns a sequence of [:resize](#:resize) commands that should restore
the current window sizes.  Only works properly when no windows
are opened or closed and the current window and tab page is
unchanged.
Example:
```
:let cmd = winrestcmd()
:call MessWithWindowSizes()
:exe cmd

```

### <a id="winrestview()" class="section-title" href="#winrestview()">Note:</a>
winrestview({dict})
Uses the [Dictionary| returned by |winsaveview()](#Dictionary| returned by |winsaveview()) to restore
the view of the current window.
Note: The {dict} does not have to contain all values, that are
returned by [winsaveview()](#winsaveview()). If values are missing, those
settings won't be restored. So you can use:
```
:call winrestview({'curswant': 4})

```

This will only set the curswant value (the column the cursor
wants to move on vertical movements) of the cursor to column 5
(yes, that is 5), while all other settings will remain the
same. This is useful, if you set the cursor position manually.

If you have changed the values the result is unpredictable.
If the window size changed the result won't be the same.

Can also be used as a [method](#method):
```
GetView()->winrestview()

```

### <a id="winsaveview()" class="section-title" href="#winsaveview()">Note:</a>
winsaveview()	Returns a [Dictionary](#Dictionary) that contains information to restore
the view of the current window.  Use [winrestview()](#winrestview()) to
restore the view.
This is useful if you have a mapping that jumps around in the
buffer and you want to go back to the original view.
This does not save fold information.  Use the 'foldenable'
option to temporarily switch off folding, so that folds are
not opened when moving around. This may have side effects.
The return value includes:
lnum		cursor line number
col		cursor column (Note: the first column
zero, as opposed to what getpos()
returns)
coladd		cursor column offset for 'virtualedit'
curswant	column for vertical movement
topline		first line in the window
topfill		filler lines, only in diff mode
leftcol		first column displayed; only used when
'wrap' is off
skipcol		columns skipped
Note that no option values are saved.


### <a id="winwidth()" class="section-title" href="#winwidth()">winwidth({nr})</a>
The result is a Number, which is the width of window {nr}.
{nr} can be the window number or the [window-ID](#window-ID).
When {nr} is zero, the width of the current window is
returned.  When window {nr} doesn't exist, -1 is returned.
An existing window always has a width of zero or more.
Examples:
```
:echo "The current window has " .. winwidth(0) .. " columns."
:if winwidth(0) <= 50
:  50 wincmd |
:endif

```
		For getting the terminal or screen size, see the 'columns'
option.

Can also be used as a [method](#method):
```
GetWinid()->winwidth()

### <a id="wordcount()" class="section-title" href="#wordcount()">wordcount()</a>
The result is a dictionary of byte/chars/word statistics for
the current buffer.  This is the same info as provided by
[g_CTRL-G](#g_CTRL-G)
The return value includes:
bytes		Number of bytes in the buffer
chars		Number of chars in the buffer
words		Number of words in the buffer
cursor_bytes    Number of bytes before cursor position
(not in Visual mode)
cursor_chars    Number of chars before cursor position
(not in Visual mode)
cursor_words    Number of words before cursor position
(not in Visual mode)
visual_bytes    Number of bytes visually selected
(only in Visual mode)
visual_chars    Number of chars visually selected
(only in Visual mode)
visual_words    Number of words visually selected
(only in Visual mode)


### <a id="writefile()" class="section-title" href="#writefile()">Note:</a>
writefile({object}, {fname} [, {flags}])
When {object} is a [List](#List) write it to file {fname}.  Each list
item is separated with a NL.  Each list item must be a String
or Number.
When {flags} contains "b" then binary mode is used: There will
not be a NL after the last list item.  An empty item at the
end does cause the last line in the file to end in a NL.

When {object} is a [Blob](#Blob) write the bytes to file {fname}
unmodified.

When {flags} contains "a" then append mode is used, lines are
appended to the file:
```
:call writefile(["foo"], "event.log", "a")
:call writefile(["bar"], "event.log", "a")

```

When {flags} contains "S" fsync() call is not used, with "s"
it is used, 'fsync' option applies by default. No fsync()
means that writefile() will finish faster, but writes may be
left in OS buffers and not yet written to disk. Such changes
will disappear if system crashes before OS does writing.

All NL characters are replaced with a NUL character.
Inserting CR characters needs to be done before passing {list}
to writefile().
An existing file is overwritten, if possible.
When the write fails -1 is returned, otherwise 0.  There is an
error message if the file can't be created or when writing
fails.
Also see [readfile()](#readfile()).
To copy a file byte for byte:
```
:let fl = readfile("foo", "b")
:call writefile(fl, "foocopy", "b")


```
		Can also be used as a [method](#method):
```
GetText()->writefile("thefile")

### <a id="xor()" class="section-title" href="#xor()">xor({expr}, {expr})</a>
Bitwise XOR on the two arguments.  The arguments are converted
to a number.  A List, Dict or Float argument causes an error.
Also see `and()` and `or()`.
Example:
```
:let bits = xor(bits, 0x80)

```

Can also be used as a [method](#method):
```
:let bits = bits->xor(0x80)

```



## <a id="string-match" class="section-title" href="#string-match">3. Matching a Pattern in a String</a> 

This is common between several functions. A regexp pattern as explained at
[pattern](#pattern) is normally used to find a match in the buffer lines.  When a
pattern is used to find a match in a String, almost everything works in the
same way.  The difference is that a String is handled like it is one line.
When it contains a "\n" character, this is not seen as a line break for the
pattern.  It can be matched with a "\n" in the pattern, or with ".".  Example:
```
:let a = "aaaa\nxxxx"
:echo matchstr(a, "..\n..")
aa
xx
:echo matchstr(a, "a.x")
a
x

Don't forget that "^" will only match at the first character of the String and
"$" at the last character of the string.  They don't match after or before a
"\n".

vim:tw=78:ts=8:noet:ft=help:norl:


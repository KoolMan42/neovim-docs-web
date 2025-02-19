---
title: Tree Sitter
description: Some page
layout: "@layouts/MainLayout.astro"
---


## <a id="" class="section-title" href="#">*Testing.Txt*	Nvim</a> 

VIM REFERENCE MANUAL	  by Bram Moolenaar


### <a id="testing-support" class="section-title" href="#testing-support">Testing Vim and Vim script</a>

Expression evaluation is explained in [eval.txt](#eval.txt).  This file goes into details
about writing tests in Vim script.  This can be used for testing Vim itself
and for testing plugins.

1. Testing Vim				[testing](#testing)
2. Test functions			[test-functions-details](#test-functions-details)
3. Assert functions			[assert-functions-details](#assert-functions-details)


## <a id="testing" class="section-title" href="#testing">1. Testing Vim</a> 

Vim can be tested after building it, usually with "make test".
The tests are located in the directory "src/testdir".

There are several types of tests added over time:
test33.in		oldest, don't add any of these
test_something.in	old style tests
test_something.vim	new style tests

### <a id="new-style-testing" class="section-title" href="#new-style-testing">Note:</a>
New tests should be added as new style tests.  These use functions such as
[assert_equal()](#assert_equal()) to keep the test commands and the expected result in one
place.
### <a id="old-style-testing" class="section-title" href="#old-style-testing">Note:</a>
In some cases an old style test needs to be used.

Find more information in the file src/testdir/README.txt.


## <a id="test-functions-details" class="section-title" href="#test-functions-details">2. Test Functions</a> 

### <a id="test_garbagecollect_now()" class="section-title" href="#test_garbagecollect_now()">test_garbagecollect_now()</a>
Like garbagecollect(), but executed right away.  This must
only be called directly to avoid any structure to exist
internally, and [v:testing](#v:testing) must have been set before calling
any function.


## <a id="assert-functions-details" class="section-title" href="#assert-functions-details">3. Assert Functions</a> 

### <a id="assert_beeps()" class="section-title" href="#assert_beeps()">assert_beeps({cmd})</a>
Run {cmd} and add an error message to [v:errors](#v:errors) if it does
NOT produce a beep or visual bell.
Also see [assert_fails()|, |assert_nobeep()](#assert_fails()|, |assert_nobeep()) and
[assert-return](#assert-return).

Can also be used as a [method](#method):
```
GetCmd()->assert_beeps()

```

### <a id="assert_equal()" class="section-title" href="#assert_equal()">Note:</a>
assert_equal({expected}, {actual} [, {msg}])
When {expected} and {actual} are not equal an error message is
added to [v:errors](#v:errors) and 1 is returned.  Otherwise zero is
returned [assert-return](#assert-return).
There is no automatic conversion, the String "4" is different
from the Number 4.  And the number 4 is different from the
Float 4.0.  The value of 'ignorecase' is not used here, case
always matters.
When {msg} is omitted an error in the form "Expected
{expected} but got {actual}" is produced.
Example:
```
assert_equal('foo', 'bar')

```
		Will result in a string to be added to [v:errors](#v:errors):
test.vim line 12: Expected 'foo' but got 'bar' ~

Can also be used as a [method](#method):
```
mylist->assert_equal([1, 2, 3])

### <a id="assert_equalfile()" class="section-title" href="#assert_equalfile()"><</a>
assert_equalfile({fname-one}, {fname-two})
When the files {fname-one} and {fname-two} do not contain
exactly the same text an error message is added to [v:errors](#v:errors).
Also see [assert-return](#assert-return).
When {fname-one} or {fname-two} does not exist the error will
mention that.

Can also be used as a [method](#method):
```
GetLog()->assert_equalfile('expected.log')

### <a id="assert_exception()" class="section-title" href="#assert_exception()">assert_exception({error} [, {msg}])</a>
When v:exception does not contain the string {error} an error
message is added to [v:errors|.  Also see |assert-return](#v:errors|.  Also see |assert-return).
This can be used to assert that a command throws an exception.
Using the error number, followed by a colon, avoids problems
with translations:
```
try
commandthatfails
call assert_false(1, 'command should have failed')
catch
call assert_exception('E492:')
endtry

### <a id="assert_fails()" class="section-title" href="#assert_fails()">assert_fails({cmd} [, {error} [, {msg}]])</a>
Run {cmd} and add an error message to [v:errors](#v:errors) if it does
NOT produce an error.  Also see [assert-return](#assert-return).
When {error} is given it must match in [v:errmsg](#v:errmsg).
Note that beeping is not considered an error, and some failing
commands only beep.  Use [assert_beeps()](#assert_beeps()) for those.

Can also be used as a [method](#method):
```
GetCmd()->assert_fails('E99:')

### <a id="assert_false()" class="section-title" href="#assert_false()">assert_false({actual} [, {msg}])</a>
When {actual} is not false an error message is added to
[v:errors|, like with |assert_equal()](#v:errors|, like with |assert_equal()).
Also see [assert-return](#assert-return).
A value is false when it is zero. When {actual} is not a
number the assert fails.
When {msg} is omitted an error in the form
"Expected False but got {actual}" is produced.

Can also be used as a [method](#method):
```
GetResult()->assert_false()

### <a id="assert_inrange()" class="section-title" href="#assert_inrange()">assert_inrange({lower}, {upper}, {actual} [, {msg}])</a>
This asserts number and [Float](#Float) values.  When {actual}  is lower
than {lower} or higher than {upper} an error message is added
to [v:errors|.  Also see |assert-return](#v:errors|.  Also see |assert-return).
When {msg} is omitted an error in the form
"Expected range {lower} - {upper}, but got {actual}" is
produced.

### <a id="assert_match()" class="section-title" href="#assert_match()">Note:</a>
assert_match({pattern}, {actual} [, {msg}])
When {pattern} does not match {actual} an error message is
added to [v:errors|.  Also see |assert-return](#v:errors|.  Also see |assert-return).

{pattern} is used as with [expr-=~](#expr-=~): The matching is always done
like 'magic' was set and 'cpoptions' is empty, no matter what
the actual value of 'magic' or 'cpoptions' is.

{actual} is used as a string, automatic conversion applies.
Use "^" and "$" to match with the start and end of the text.
Use both to match the whole text.

When {msg} is omitted an error in the form
"Pattern {pattern} does not match {actual}" is produced.
Example:
```
assert_match('^f.*o$', 'foobar')

```
		Will result in a string to be added to [v:errors](#v:errors):
test.vim line 12: Pattern '^f.*o$' does not match 'foobar' ~

Can also be used as a [method](#method):
```
### <a id="getFile()->assert_match('foo.')" class="section-title" href="#getFile()->assert_match('foo.')">Note:</a>

```

### <a id="assert_nobeep()" class="section-title" href="#assert_nobeep()">assert_nobeep({cmd})</a>
Run {cmd} and add an error message to [v:errors](#v:errors) if it
produces a beep or visual bell.
Also see [assert_beeps()](#assert_beeps()).

Can also be used as a [method](#method):
```
GetCmd()->assert_nobeep()

```

### <a id="assert_notequal()" class="section-title" href="#assert_notequal()">Note:</a>
assert_notequal({expected}, {actual} [, {msg}])
The opposite of `assert_equal()`: add an error message to
[v:errors](#v:errors) when {expected} and {actual} are equal.
Also see [assert-return](#assert-return).

Can also be used as a [method](#method):
```
mylist->assert_notequal([1, 2, 3])

### <a id="assert_notmatch()" class="section-title" href="#assert_notmatch()"><</a>
assert_notmatch({pattern}, {actual} [, {msg}])
The opposite of `assert_match()`: add an error message to
[v:errors](#v:errors) when {pattern} matches {actual}.
Also see [assert-return](#assert-return).

Can also be used as a [method](#method):
```
### <a id="getFile()->assert_notmatch('bar.')" class="section-title" href="#getFile()->assert_notmatch('bar.')">Note:</a>


### <a id="assert_report()" class="section-title" href="#assert_report()">assert_report({msg})</a>
Report a test failure directly, using String {msg}.
Always returns one.

Can also be used as a [method](#method):
```
GetMessage()->assert_report()


### <a id="assert_true()" class="section-title" href="#assert_true()">assert_true({actual} [, {msg}])</a>
When {actual} is not true an error message is added to
[v:errors|, like with |assert_equal()](#v:errors|, like with |assert_equal()).
Also see [assert-return](#assert-return).
A value is [TRUE| when it is a non-zero number or |v:true](#TRUE| when it is a non-zero number or |v:true).
When {actual} is not a number or [v:true](#v:true) the assert fails.
When {msg} is omitted an error in the form "Expected True but
got {actual}" is produced.

Can also be used as a [method](#method):
```
GetResult()->assert_true()

```


vim:tw=78:ts=8:noet:ft=help:norl:


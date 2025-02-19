---
title: Tree Sitter
description: Some page
layout: "@layouts/MainLayout.astro"
---


## <a id="Nvim" class="section-title" href="#Nvim"> Pi Spec Txt</a> 

by Gustavo Niemeyer ~

This is a filetype plugin to work with rpm spec files.

Currently, this Vim plugin allows you to easily update the %changelog
section in RPM spec files.  It will even create a section for you if it
doesn't exist yet.  If you've already inserted an entry today, it will
give you the opportunity to just add a new item in today's entry.  If you
don't provide a format string ([spec_chglog_format](#spec_chglog_format)), it'll ask you an
email address and build a format string by itself.

1. How to use it	[spec-how-to-use-it](#spec-how-to-use-it)
2. Customizing		[spec-customizing](#spec-customizing)


## <a id="spec-how-to-use-it" class="section-title" href="#spec-how-to-use-it">1. How to Use It</a> 

The spec_chglog plugin provides a map like the following:

:map <buffer> <LocalLeader>c <Plug>SpecChangelog

It means that you may run the plugin inside a spec file by pressing
your maplocalleader key (default is '\') plus 'c'.  If you do not have
[spec_chglog_format](#spec_chglog_format) set, the plugin will ask you for an email address
to use in this edit session.

Every time you run the plugin, it will check to see if the last entry in the
changelog has been written today and by you.  If the entry matches, it will
just insert a new changelog item, otherwise it will create a new changelog
entry.  If you are running with [spec_chglog_release_info](#spec_chglog_release_info) enabled, it will
also check if the name, version and release matches.  The plugin is smart
enough to ask you if it should update the package release, if you have not
done so.

### <a id="spec-setting-a-map" class="section-title" href="#spec-setting-a-map">Setting a map</a>
-------------

As you should know, you can easily set a map to access any Vim command (or
anything, for that matter).  If you don't like the default map of

```
LocalLeader>c, you may just set up your own key.  The following line
shows you how you could do this in your vimrc file, mapping the plugin to
the <F5> key:

au FileType spec map <buffer> <F5> <Plug>SpecChangelog

Note: the plugin will respect your desire to change the default mapping
and won't set it.

This command will add a map only in the spec file buffers.


## <a id="spec-customizing" class="section-title" href="#spec-customizing">2. Customizing</a> 

### <a id="spec_chglog_format" class="section-title" href="#spec_chglog_format">The format string</a>
-----------------

You can easily customize how your spec file entry will look like.  To do
this just set the variable "spec_chglog_format" in your vimrc file like
this:
```

let spec_chglog_format = "%a %b %d %Y My Name <my@email.com>"

Note that "%a %b %d %Y" is the most used time format.  If you don't provide
a format string, when you run the SpecChangelog command for the first
time, it will ask you an email address and build the [spec_chglog_format](#spec_chglog_format)
variable for you.  This way, you will only need to provide your email
address once.

To discover which format options you can use, take a look at the strftime()
function man page.

### <a id="spec_chglog_prepend" class="section-title" href="#spec_chglog_prepend">Where to insert new items</a>
-------------------------

The plugin will usually insert new %changelog entry items (note that it's
not the entry itself) after the existing ones.  If you set the
spec_chglog_prepend variable
```

let spec_chglog_prepend = 1

it will insert new items before the existing ones.

### <a id="spec_chglog_release_info" class="section-title" href="#spec_chglog_release_info">Inserting release info</a>
----------------------

If you want, the plugin may automatically insert release information
on each changelog entry.  One advantage of turning this feature on is
that it may control if the release has been updated after the last
change in the package or not.  If you have not updated the package
version or release, it will ask you if it should update the package
release for you.  To turn this feature on, just insert the following
code in your vimrc:
```

let spec_chglog_release_info = 1

Then, the first item in your changelog entry will be something like:
```

+ name-1.0-1cl

If you don't like the release updating feature and don't want to answer
"No" each time it detects an old release, you may disable it with
```

let spec_chglog_never_increase_release = 1


Good luck!!

vim:tw=78:ts=8:noet:ft=help:norl:


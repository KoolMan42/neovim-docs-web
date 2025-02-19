---
title: Tree Sitter
description: Some page
layout: "@layouts/MainLayout.astro"
---


## <a id="Nvim" class="section-title" href="#Nvim"> Mlang Txt</a> 

VIM REFERENCE MANUAL    by Bram Moolenaar


### <a id="multilang multi-lang" class="section-title" href="#multilang multi-lang">Multi-language features</a>

This is about using messages and menus in various languages.  For editing
multibyte text see [multibyte](#multibyte).

The basics are explained in the user manual: [usr_45.txt](#usr_45.txt).

Type [gO](#gO) to see the table of contents.


## <a id="multilang-messages" class="section-title" href="#multilang-messages">1. Messages</a> 

Vim picks up the locale from the environment.  In most cases this means Vim
will use the language that you prefer, unless it's not available.

To see a list of supported locale names on your system, look in one of these
directories (for Unix):
/usr/lib/locale ~
/usr/share/locale ~
Unfortunately, upper/lowercase differences matter.  Also watch out for the
use of "-" and "_".

### <a id=":lan :lang :language E197" class="section-title" href="#:lan :lang :language E197">Note:</a>
:lan[guage]
:lan[guage] mes[sages]
:lan[guage] cty[pe]
:lan[guage] tim[e]
:lan[guage] col[late]
Print the current language (aka locale).
With the "messages" argument the language used for
messages is printed.  Technical: LC_MESSAGES.
With the "ctype" argument the language used for
character encoding is printed.  Technical: LC_CTYPE.
With the "time" argument the language used for
strftime() is printed.  Technical: LC_TIME.
With the "collate" argument the language used for
collation order is printed.  Technical: LC_COLLATE.
Without argument all parts of the locale are printed
(this is system dependent).
The current language can also be obtained with the
[v:lang|, |v:ctype|, |v:collate| and |v:lc_time](#v:lang|, |v:ctype|, |v:collate| and |v:lc_time)
variables.

:lan[guage] {name}
:lan[guage] mes[sages] {name}
:lan[guage] cty[pe] {name}
:lan[guage] tim[e] {name}
:lan[guage] col[late] {name}
Set the current language (aka locale) to {name}.
The locale {name} must be a valid locale on your
system.  Some systems accept aliases like "en" or
"en_US", but some only accept the full specification
like "en_US.ISO_8859-1".  On Unix systems you can use
this command to see what locales are supported:
```
:!locale -a

```
			With the "messages" argument the language used for
messages is set.  This can be different when you want,
for example, English messages while editing Japanese
text.  This sets $LC_MESSAGES.
With the "ctype" argument the language used for
character encoding is set.  This affects the libraries
that Vim was linked with.  It's unusual to set this to
a different value from 'encoding' or "C".  This sets
$LC_CTYPE.
With the "time" argument the language used for time
and date messages is set.  This affects strftime().
This sets $LC_TIME.
With the "collate" argument the language used for the
collation order is set.  This affects sorting of
characters. This sets $LC_COLLATE.
Without an argument all are set, and additionally
$LANG is set.
The LC_NUMERIC value will always be set to "C" so
that floating point numbers use '.' as the decimal
point.  This will make a difference for items that
depend on the language (some messages, time and date
format).
Not fully supported on all systems.
If this fails there will be an error message.  If it
succeeds there is no message.  Example:
```
:language
Current language: C
:language de_DE.ISO_8859-1
:language mes
Current messages language: de_DE.ISO_8859-1
:lang mes en

```


Message files (vim.mo) have to be placed in "$VIMRUNTIME/lang/xx/LC_MESSAGES",
where "xx" is the abbreviation of the language (mostly two letters). If you
write your own translations you need to generate the .po file and convert it
to a .mo file.

To overrule the automatic choice of the language, set the $LANG variable to
the language of your choice.  use "en" to disable translations.
```

:let $LANG = 'ja'

(text for Windows by Muraoka Taro)


## <a id="multilang-menus" class="section-title" href="#multilang-menus">2. Menus</a> 

See [45.2](#45.2) for the basics, esp. using 'langmenu'.

Note that if changes have been made to the menus after the translation was
done, some of the menus may be shown in English.  Please try contacting the
maintainer of the translation and ask him to update it.  You can find the
name and e-mail address of the translator in
"$VIMRUNTIME/lang/menu_<lang>.vim".

To set the font to use for the menus, use the [:highlight](#:highlight) command.  Example:
```

:highlight Menu font=k12,r12


ALIAS LOCALE NAMES

Unfortunately, the locale names are different on various systems, even though
they are for the same language and encoding.  If you do not get the menu
translations you expected, check the output of this command:
```

echo v:lang

Now check the "$VIMRUNTIME/lang" directory for menu translation files that use
a similar language.  A difference in a "-" being a "_" already causes a file
not to be found!  Another common difference to watch out for is "iso8859-1"
versus "iso_8859-1".  Fortunately Vim makes all names lowercase, thus you
don't have to worry about case differences.  Spaces are changed to
underscores, to avoid having to escape them.

If you find a menu translation file for your language with a different name,
create a file in your own runtime directory to load that one.  The name of
that file could be:
```

~/.config/nvim/lang/menu_<v:lang>.vim

Check the 'runtimepath' option for directories which are searched.  In that
file put a command to load the menu file with the other name:
```

runtime lang/menu_<other_lang>.vim


TRANSLATING MENUS

If you want to do your own translations, you can use the [:menutrans](#:menutrans) command,
explained below.  It is recommended to put the translations for one language
in a Vim script.  For a language that has no translation yet, please consider
becoming the maintainer and make your translations available to all Vim users.
Send an e-mail to the Vim maintainer <maintainer@vim.org>.

### <a id=":menut :menutrans :menutranslate" class="section-title" href="#:menut :menutrans :menutranslate">Note:</a>
:menut[ranslate] clear
Clear all menu translations.

:menut[ranslate] {english} {mylang}
Translate menu name {english} to {mylang}.  All
special characters like "&" and "<Tab>" need to be
included.  Spaces and dots need to be escaped with a
backslash, just like in other [:menu](#:menu) commands.
Case in {english} is ignored.

See the $VIMRUNTIME/lang directory for examples.

To try out your translations you first have to remove all menus.  This is how
you can do it without restarting Vim:
```
:source $VIMRUNTIME/delmenu.vim
:source <your-new-menu-file>
:source $VIMRUNTIME/menu.vim

Each part of a menu path is translated separately.  The result is that when
"Help" is translated to "Hilfe" and "Overview" to "Überblick" then
"Help.Overview" will be translated to "Hilfe.Überblick".


## <a id="multilang-scripts" class="section-title" href="#multilang-scripts">3. Scripts</a> 

In Vim scripts you can use the [v:lang](#v:lang) variable to get the current language
(locale).  The default value is "C" or comes from the $LANG environment
variable.

The following example shows how this variable is used in a simple way, to make
a message adapt to language preferences of the user,
```

:if v:lang =~ "de_DE"
:  echo "Guten Morgen"
:else
:  echo "Good morning"
:endif

```


vim:tw=78:sw=4:ts=8:noet:ft=help:norl:


---
title: Tree Sitter
description: Some page
layout: "@layouts/MainLayout.astro"
---


## <a id="Nvim" class="section-title" href="#Nvim"> Print Txt</a> 

VIM REFERENCE MANUAL    by Bram Moolenaar


### <a id="printing" class="section-title" href="#printing">Printing</a>

Type [gO](#gO) to see the table of contents.


## <a id="print-intro" class="section-title" href="#print-intro">1. Introduction</a> 

On MS-Windows Vim can print your text on any installed printer.  On other
systems a PostScript file is produced.  This can be directly sent to a
PostScript printer.  For other printers a program like ghostscript needs to be
used.

Note: If you have problems printing with [:hardcopy](#:hardcopy), an alternative is to use
[:TOhtml](#:TOhtml) and print the resulting html file from a browser.

### <a id=":ha :hardcopy E237 E238 E324" class="section-title" href="#:ha :hardcopy E237 E238 E324">Note:</a>
:[range]ha[rdcopy][!] [arguments]
Send [range] lines (default whole file) to the
printer.

On MS-Windows a dialog is displayed to allow selection
of printer, paper size etc.  To skip the dialog, use
the [!].  In this case the printer defined by
'printdevice' is used, or, if 'printdevice' is empty,
the system default printer.

For systems other than MS-Windows, PostScript is
written in a temp file and 'printexpr' is used to
actually print it.  Then [arguments] can be used by
'printexpr' through [v:cmdarg](#v:cmdarg).  Otherwise [arguments]
is ignored.  'printoptions' can be used to specify
paper size, duplex, etc.
Note: If you want PDF, there are tools such as
"ps2pdf" that can convert the PostScript to PDF.

:[range]ha[rdcopy][!] >{filename}
As above, but write the resulting PostScript in file
{filename}.
Things like "%" are expanded [cmdline-special](#cmdline-special)
Careful: An existing file is silently overwritten.
On MS-Windows use the "print to file" feature of the
printer driver.

Progress is displayed during printing as a page number and a percentage.  To
abort printing use the interrupt key (CTRL-C or, on MS-systems, CTRL-Break).

Printer output is controlled by the 'printfont' and 'printoptions' options.
'printheader' specifies the format of a page header.

The printed file is always limited to the selected margins, irrespective of
the current window's 'wrap' or 'linebreak' settings.  The "wrap" item in
'printoptions' can be used to switch wrapping off.
The current highlighting colors are used in the printout, with the following
considerations:
1) The normal background is always rendered as white (i.e. blank paper).
2) White text or the default foreground is rendered as black, so that it shows
up!
3) If 'background' is "dark", then the colours are darkened to compensate for
the fact that otherwise they would be too bright to show up clearly on
white paper.


## <a id="print-options" class="section-title" href="#print-options">2. Print Options</a> 

Here are the details for the options that change the way printing is done.
For generic info about setting options see [options.txt](#options.txt).

### <a id="pdev-option" class="section-title" href="#pdev-option">Note:</a>
'printdevice' 'pdev'	string	(default empty)
global
This defines the name of the printer to be used when the [:hardcopy](#:hardcopy) command
is issued with a bang (!) to skip the printer selection dialog.  On Win32, it
should be the printer name exactly as it appears in the standard printer
dialog.
If the option is empty, then vim will use the system default printer for
":hardcopy!"

### <a id="penc-option E620" class="section-title" href="#penc-option E620">Note:</a>
'printencoding' 'penc'	String	(default empty, except for:
Windows: cp1252,
Macintosh: mac-roman,
HPUX: hp-roman8)
global
Sets the character encoding used when printing.  This option tells Vim which
print character encoding file from the "print" directory in 'runtimepath' to
use.

This option will accept any value from [encoding-names](#encoding-names).  Any recognized names
are converted to Vim standard names - see 'encoding' for more details.  Names
not recognized by Vim will just be converted to lower case and underscores
replaced with '-' signs.

If 'printencoding' is empty or Vim cannot find the file then it will use
'encoding' (if it is set an 8-bit encoding) to find the print character
encoding file.  If Vim is unable to find a character encoding file then it
will use the "latin1" print character encoding file.

When 'encoding' is set to a multibyte encoding, Vim will try to convert
characters to the printing encoding for printing (if 'printencoding' is empty
then the conversion will be to latin1). If no conversion is possible then
printing will fail.  Any characters that cannot be converted will be replaced
with upside down question marks.

Two print character encoding files are provided to support default Mac and
HPUX character encodings and are used by default on these platforms. Code page
1252 print character encoding is used by default on the Windows platform.

### <a id="pexpr-option" class="section-title" href="#pexpr-option">Note:</a>
'printexpr' 'pexpr'	String	(default: see below)
global
Expression that is evaluated to print the PostScript produced with
[:hardcopy](#:hardcopy).
The file name to be printed is in [v:fname_in](#v:fname_in).
The arguments to the ":hardcopy" command are in [v:cmdarg](#v:cmdarg).
The expression must take care of deleting the file after printing it.
When there is an error, the expression must return a non-zero number.
If there is no error, return zero or an empty string.
The default for non MS-Windows systems is to simply use "lpr" to print the
file:
```

system(['lpr']
+ (empty(&printdevice)?[]:['-P', &printdevice])
+ [v:fname_in])
.. delete(v:fname_in)
+ v:shell_error

On MS-Dos and MS-Windows machines the default is to copy the file to the
currently specified printdevice:
```

system(['copy', v:fname_in, empty(&printdevice)?'LPT1':&printdevice])
.. delete(v:fname_in)

If you change this option, using a function is an easy way to avoid having to
escape all the spaces.  Example:
```

:set printexpr=PrintFile(v:fname_in)
:function PrintFile(fname)
:  call system("ghostview " .. a:fname)
:  call delete(a:fname)
:  return v:shell_error
:endfunc

Be aware that some print programs return control before they have read the
file.  If you delete the file too soon it will not be printed.  These programs
usually offer an option to have them remove the file when printing is done.
### <a id="E365" class="section-title" href="#E365">Note:</a>
If evaluating the expression fails or it results in a non-zero number, you get
an error message.  In that case Vim will delete the file.  In the default
value for non-MS-Windows a trick is used: Adding "v:shell_error" will result
in a non-zero number when the system() call fails.

This option cannot be set from a [modeline| or in the |sandbox](#modeline| or in the |sandbox), for security
reasons.

### <a id="pfn-option E613" class="section-title" href="#pfn-option E613">Note:</a>
'printfont' 'pfn'	string	(default "courier")
global
This is the name of the font that will be used for the [:hardcopy](#:hardcopy) command's
output.  It has the same format as the 'guifont' option, except that only one
font may be named, and the special "guifont=*" syntax is not available.

In the Win32 GUI version this specifies a font name with its extra attributes,
as with the 'guifont' option.

For other systems, only ":h11" is recognized, where "11" is the point size of
the font.  When omitted, the point size is 10.

### <a id="pheader-option" class="section-title" href="#pheader-option">Note:</a>
'printheader' 'pheader'  string  (default "%<%f%h%m%=Page %N")
global
This defines the format of the header produced in [:hardcopy](#:hardcopy) output.  The
option is defined in the same way as the 'statusline' option.  The same simple
header is used when this option is empty.

### <a id="pmbcs-option" class="section-title" href="#pmbcs-option">Note:</a>
'printmbcharset' 'pmbcs'  string (default "")
global
Sets the CJK character set to be used when generating CJK output from
[:hardcopy](#:hardcopy).  The following predefined values are currently recognised by Vim:

Value		Description ~
Chinese	GB_2312-80
(Simplified)	GBT_12345-90
MAC		Apple Mac Simplified Chinese
GBT-90_MAC	GB/T 12345-90 Apple Mac Simplified
Chinese
GBK		GBK (GB 13000.1-93)
ISO10646	ISO 10646-1:1993

Chinese	CNS_1993	CNS 11643-1993, Planes 1 & 2
(Traditional)	BIG5
ETEN		Big5 with ETen extensions
ISO10646	ISO 10646-1:1993

Japanese	JIS_C_1978
JIS_X_1983
JIS_X_1990
MSWINDOWS	Win3.1/95J (JIS X 1997 + NEC +
IBM extensions)
KANJITALK6	Apple Mac KanjiTalk V6.x
KANJITALK7	Apple Mac KanjiTalk V7.x

Korean	KS_X_1992
MAC		Apple Macintosh Korean
MSWINDOWS	KS X 1992 with MS extensions
ISO10646	ISO 10646-1:1993

Only certain combinations of the above values and 'printencoding' are
possible.  The following tables show the valid combinations:

euc-cn	 gbk	ucs-2	utf-8 ~
Chinese	GB_2312-80	   x
(Simplified)	GBT_12345-90	   x
MAC		   x
GBT-90_MAC	   x
GBK			   x
ISO10646			  x	  x

euc-tw	 big5	ucs-2	utf-8 ~
Chinese	CNS_1993	   x
(Traditional)	BIG5			   x
ETEN			   x
ISO10646			  x	  x

euc-jp	 sjis	ucs-2	utf-8 ~
Japanese	JIS_C_1978	   x	   x
JIS_X_1983	   x	   x
JIS_X_1990	   x		  x	  x
MSWINDOWS		   x
KANJITALK6		   x
KANJITALK7		   x

euc-kr	 cp949	ucs-2	utf-8 ~
Korean	KS_X_1992	   x
MAC		   x
MSWINDOWS		   x
ISO10646			  x	  x

To set up the correct encoding and character set for printing some
Japanese text you would do the following;
```
:set printencoding=euc-jp
:set printmbcharset=JIS_X_1983

If 'printmbcharset' is not one of the above values then it is assumed to
specify a custom multibyte character set and no check will be made that it is
compatible with the value for 'printencoding'.  Vim will look for a file
defining the character set in the "print" directory in 'runtimepath'.

### <a id="pmbfn-option" class="section-title" href="#pmbfn-option">Note:</a>
'printmbfont' 'pmbfn'	string (default "")
global
This is a comma-separated list of fields for font names to be used when
generating CJK output from [:hardcopy](#:hardcopy).  Each font name has to be preceded
with a letter indicating the style the font is to be used for as follows:

r:{font-name}		font to use for normal characters
b:{font-name}		font to use for bold characters
i:{font-name}		font to use for italic characters
o:{font-name}		font to use for bold-italic characters

A field with the r: prefix must be specified when doing CJK printing.  The
other fontname specifiers are optional.  If a specifier is missing then
another font will be used as follows:

if b: is missing, then use r:
if i: is missing, then use r:
if o: is missing, then use b:

Some CJK fonts do not contain characters for codes in the ASCII code range.
Also, some characters in the CJK ASCII code ranges differ in a few code points
from traditional ASCII characters.  There are two additional fields to control
printing of characters in the ASCII code range.

c:yes			Use Courier font for characters in the ASCII
c:no (default)	code range.

a:yes			Use ASCII character set for codes in the ASCII
a:no (default)	code range.

The following is an example of specifying two multibyte fonts, one for normal
and italic printing and one for bold and bold-italic printing, and using
Courier to print codes in the ASCII code range but using the national
character set:
```
:set printmbfont=r:WadaMin-Regular,b:WadaMin-Bold,c:yes

```

### <a id="popt-option" class="section-title" href="#popt-option">Note:</a>
'printoptions' 'popt'	string (default "")
global
This is a comma-separated list of items that control the format of the output
of [:hardcopy](#:hardcopy):

left:{spec}		left margin (default: 10pc)
right:{spec}		right margin (default: 5pc)
top:{spec}		top margin (default: 5pc)
bottom:{spec}		bottom margin (default: 5pc)
{spec} is a number followed by "in" for inches, "pt"
for points (1 point is 1/72 of an inch), "mm" for
millimeters or "pc" for a percentage of the media
size.
Weird example:
left:2in,top:30pt,right:16mm,bottom:3pc
If the unit is not recognized there is no error and
the default value is used.

header:{nr}		Number of lines to reserve for the header.
Only the first line is actually filled, thus when {nr}
is 2 there is one empty line.  The header is formatted
according to 'printheader'.
header:0		Do not print a header.
header:2  (default)	Use two lines for the header

syntax:n		Do not use syntax highlighting.  This is faster and
thus useful when printing large files.
syntax:y		Do syntax highlighting.
syntax:a  (default)	Use syntax highlighting if the printer appears to be
able to print color or grey.

number:y		Include line numbers in the printed output.
number:n  (default)	No line numbers.

wrap:y    (default)	Wrap long lines.
wrap:n		Truncate long lines.

duplex:off		Print on one side.
duplex:long (default)	Print on both sides (when possible), bind on long
side.
duplex:short		Print on both sides (when possible), bind on short
side.

collate:y  (default)	Collating: 1 2 3, 1 2 3, 1 2 3
collate:n		No collating: 1 1 1, 2 2 2, 3 3 3

jobsplit:n (default)	Do all copies in one print job
jobsplit:y		Do each copy as a separate print job.  Useful when
doing N-up postprocessing.

portrait:y (default)	Orientation is portrait.
portrait:n		Orientation is landscape.
### <a id="a4 letter" class="section-title" href="#a4 letter">Note:</a>
paper:A4   (default)	Paper size: A4
paper:{name}		Paper size from this table:
{name}	    size in cm	     size in inch ~
10x14	    25.4  x 35.57    10    x 14
A3	    29.7  x 42	     11.69 x 16.54
A4	    21	  x 29.7      8.27 x 11.69
A5	    14.8  x 21	      5.83 x  8.27
B4	    25	  x 35.3     10.12 x 14.33
B5	    17.6  x 25	      7.17 x 10.12
executive   18.42 x 26.67     7.25 x 10.5
folio	    21	  x 33	      8.27 x 13
ledger	    43.13 x 27.96    17    x 11
legal	    21.59 x 35.57     8.5  x 14
letter	    21.59 x 27.96     8.5  x 11
quarto	    21.59 x 27.5      8.5  x 10.83
statement   13.97 x 21.59     5.5  x  8.5
tabloid     27.96 x 43.13    11    x 17

formfeed:n (default)	Treat form feed characters (0x0c) as a normal print
character.
formfeed:y		When a form feed character is encountered, continue
printing of the current line at the beginning of the
first line on a new page.

The item indicated with (default) is used when the item is not present.  The
values are not always used, especially when using a dialog to select the
printer and options.
Example:
```
:set printoptions=paper:letter,duplex:off


## <a id="postscript-printing" class="section-title" href="#postscript-printing">3. PostScript Printing</a> <span id="E455"></span>

Provided you have enough disk space there should be no problems generating a
PostScript file.  You need to have the runtime files correctly installed (if
you can find the help files, they probably are).

There are currently a number of limitations with PostScript printing:

- 'printfont' - The font name is ignored (the Courier family is always used -
it should be available on all PostScript printers) but the font size is
used.

- 'printoptions' - The duplex setting is used when generating PostScript
output, but it is up to the printer to take notice of the setting.  If the
printer does not support duplex printing then it should be silently ignored.
Some printers, however, don't print at all.

- 8-bit support - While a number of 8-bit print character encodings are
supported it is possible that some characters will not print.  Whether a
character will print depends on the font in the printer knowing the
character.  Missing characters will be replaced with an upside down question
mark, or a space if that character is also not known by the font.  It may be
possible to get all the characters in an encoding to print by installing a
new version of the Courier font family.

- Multi-byte support - Currently Vim will try to convert multibyte characters
to the 8-bit encoding specified by 'printencoding' (or latin1 if it is
empty).  Any characters that are not successfully converted are shown as
unknown characters.  Printing will fail if Vim cannot convert the multibyte
to the 8-bit encoding.


## <a id="" class="section-title" href="#">4. Custom 8-Bit Print Character Encodings	*Postscript-Print-Encoding*</a> <span id="E618"></span>

To use your own print character encoding when printing 8-bit character data
you need to define your own PostScript font encoding vector.  Details on how
to define a font encoding vector is beyond the scope of this help file, but
you can find details in the PostScript Language Reference Manual, 3rd Edition,
published by Addison-Wesley and available in PDF form at
https://www.adobe.com/.  The following describes what you need to do for Vim to
locate and use your print character encoding.

i.   Decide on a unique name for your encoding vector, one that does not clash
with any of the recognized or standard encoding names that Vim uses (see
[encoding-names](#encoding-names) for a list), and that no one else is likely to use.
ii.  Copy $VIMRUNTIME/print/latin1.ps to the print subdirectory in your
'runtimepath' and rename it with your unique name.
iii. Edit your renamed copy of latin1.ps, replacing all occurrences of latin1
with your unique name (don't forget the line starting %%Title:), and
modify the array of glyph names to define your new encoding vector.  The
array must have exactly 256 entries or you will not be able to print!
iv.  Within Vim, set 'printencoding' to your unique encoding name and then
print your file.  Vim will now use your custom print character encoding.

Vim will report an error with the resource file if you change the order or
content of the first 3 lines, other than the name of the encoding on the line
starting %%Title: or the version number on the line starting %%Version:.

[Technical explanation for those that know PostScript - Vim looks for a file
with the same name as the encoding it will use when printing.  The file
defines a new PostScript Encoding resource called /VIM-name, where name is the
print character encoding Vim will use.]


## <a id="postscript-cjk-printing" class="section-title" href="#postscript-cjk-printing">5. PostScript CJK Printing</a> <span id="E673"></span>

Vim supports printing of Chinese, Japanese, and Korean files.  Setting up Vim
to correctly print CJK files requires setting up a few more options.

Each of these countries has many standard character sets and encodings which
require that both be specified when printing.  In addition, CJK fonts normally
do not have the concept of italic glyphs and use different weight or stroke
style to achieve emphasis when printing.  This in turn requires a different
approach to specifying fonts to use when printing.

The encoding and character set are specified with the 'printencoding' and
'printmbcharset' options.  If 'printencoding' is not specified then 'encoding'
is used as normal.  If 'printencoding' is specified then characters will be
translated to this encoding for printing.  You should ensure that the encoding
is compatible with the character set needed for the file contents or some
characters may not appear when printed.

The fonts to use for CJK printing are specified with 'printmbfont'.  This
option allows you to specify different fonts to use when printing characters
which are syntax highlighted with the font styles normal, italic, bold and
bold-italic.

Please read your printer documentation on how to install new fonts.

CJK fonts can be large containing several thousand glyphs, and it is not
uncommon to find that they only contain a subset of a national standard.  It
is not unusual to find the fonts to not include characters for codes in the
ASCII code range.  If you find half-width Roman characters are not appearing
in your printout then you should configure Vim to use the Courier font the
half-width ASCII characters with 'printmbfont'.  If your font does not include
other characters then you will need to find another font that does.

Another issue with ASCII characters, is that the various national character
sets specify a couple of different glyphs in the ASCII code range.  If you
print ASCII text using the national character set you may see some unexpected
characters.  If you want true ASCII code printing then you need to configure
Vim to output ASCII characters for the ASCII code range with 'printmbfont'.

It is possible to define your own multibyte character set although this
should not be attempted lightly.  A discussion on the process if beyond the
scope of these help files.  You can find details on CMap (character map) files
in the document 'Adobe CMap and CIDFont Files Specification, Version 1.0',
available from https://www.adobe.com as a PDF file.


## <a id="postscript-print-trouble" class="section-title" href="#postscript-print-trouble">6. PostScript Printing Troubleshooting</a> <span id="E621"></span>

Usually the only sign of a problem when printing with PostScript is that your
printout does not appear.  If you are lucky you may get a printed page that
tells you the PostScript operator that generated the error that prevented the
print job completing.

There are a number of possible causes as to why the printing may have failed:

- Wrong version of the prolog resource file.  The prolog resource file
contains some PostScript that Vim needs to be able to print.  Each version
of Vim needs one particular version.  Make sure you have correctly installed
the runtime files, and don't have any old versions of a file called prolog
in the print directory in your 'runtimepath' directory.

- Paper size.  Some PostScript printers will abort printing a file if they do
not support the requested paper size.  By default Vim uses A4 paper.  Find
out what size paper your printer normally uses and set the appropriate paper
size with 'printoptions'.  If you cannot find the name of the paper used,
measure a sheet and compare it with the table of supported paper sizes listed
for 'printoptions', using the paper that is closest in both width AND height.
Note: The dimensions of actual paper may vary slightly from the ones listed.
If there is no paper listed close enough, then you may want to try psresize
from PSUtils, discussed below.

- Two-sided printing (duplex).  Normally a PostScript printer that does not
support two-sided printing will ignore any request to do it.  However, some
printers may abort the job altogether.  Try printing with duplex turned off.
Note: Duplex prints can be achieved manually using PS utils - see below.

- Collated printing.  As with Duplex printing, most PostScript printers that
do not support collating printouts will ignore a request to do so.  Some may
not.  Try printing with collation turned off.

- Syntax highlighting.  Some print management code may prevent the generated
PostScript file from being printed on a black and white printer when syntax
highlighting is turned on, even if solid black is the only color used.  Try
printing with syntax highlighting turned off.

A safe printoptions setting to try is:
```

:set printoptions=paper:A4,duplex:off,collate:n,syntax:n

Replace "A4" with the paper size that best matches your printer paper.


## <a id="postscript-print-util" class="section-title" href="#postscript-print-util">7. PostScript Utilities</a> 

7.1 Ghostscript

Ghostscript is a PostScript and PDF interpreter that can be used to display
and print on non-PostScript printers PostScript and PDF files.  It can also
generate PDF files from PostScript.

Ghostscript will run on a wide variety of platforms. Information on
Ghostscript can be found at:

http://www.ghostscript.com/

Support for a number of non PostScript printers is provided in the
distribution as standard, but if you cannot find support for your printer
check the Ghostscript site for other printers not included by default.


7.2 Ghostscript Previewers.

The interface to Ghostscript is very primitive so a number of graphical front
ends have been created.  These allow easier PostScript file selection,
previewing at different zoom levels, and printing.  Check supplied
documentation for full details.

ALTERNATE DUPLEX PRINTING

It is possible to achieve a poor man's version of duplex printing using the PS
utility psselect.  This utility has options -e and -o for printing just the
even or odd pages of a PS file respectively.

First generate a PS file with the ":hardcopy" command, then generate new
files with all the odd and even numbered pages with:
```

psselect -o test.ps odd.ps
psselect -e test.ps even.ps

Next print odd.ps with your platform's normal print command.  Then take the
print output, turn it over and place it back in the paper feeder.  Now print
even.ps with your platform's print command.  All the even pages should now
appear on the back of the odd pages.

There are a couple of points to bear in mind:

1. Position of the first page.  If the first page is on top of the printout
when printing the odd pages then you need to reverse the order that the odd
pages are printed.  This can be done with the -r option to psselect.  This
will ensure page 2 is printed on the back of page 1.
Note: it is better to reverse the odd numbered pages rather than the even
numbered in case there are an odd number of pages in the original PS file.

2. Paper flipping.  When turning over the paper with the odd pages printed on
them you may have to either flip them horizontally (along the long edge) or
vertically (along the short edge), as well as possibly rotating them 180
degrees.  All this depends on the printer - it will be more obvious for
desktop ink jets than for small office laser printers where the paper path
is hidden from view.


## <a id="printing-formfeed" class="section-title" href="#printing-formfeed">8. Formfeed Characters</a> 

By default Vim does not do any special processing of formfeed control
characters.  Setting the 'printoptions' formfeed item will make Vim recognize
formfeed characters and continue printing the current line at the beginning
of the first line on a new page.  The use of formfeed characters provides
rudimentary print control but there are certain things to be aware of.

Vim will always start printing a line (including a line number if enabled)
containing a formfeed character, even if it is the first character on the
line.  This means if a line starting with a formfeed character is the first
line of a page then Vim will print a blank page.

Since the line number is printed at the start of printing the line containing
the formfeed character, the remainder of the line printed on the new page
will not have a line number printed for it (in the same way as the wrapped
lines of a long line when wrap in 'printoptions' is enabled).

If the formfeed character is the last character on a line, then printing will
continue on the second line of the new page, not the first.  This is due to
Vim processing the end of the line after the formfeed character and moving
down a line to continue printing.

Due to the points made above it is recommended that when formfeed character
processing is enabled, printing of line numbers is disabled, and that form
feed characters are not the last character on a line.  Even then you may need
to adjust the number of lines before a formfeed character to prevent
accidental blank pages.


## <a id="" class="section-title" href="#">Vim Tw 78 Ts 8 Noet Ft Help Norl</a> 




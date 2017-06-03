# text-tools
`text-tools` is a set of programs designed to be used with a text
editor I'm currently working on. The programs themselves are
generic programs that can be used for some stream-based text
editing tasks.

These programs are:
* `add`, `mul` for adding and multiplying the numbers represented by the
  lines of stdin
* `cmt` for commenting out text
* `hello` for printing the hello world program in a given language
* `i`, `ui` for indenting and unindenting text
* `j` for joining lines together
* `lic` for printing out license text
* `sc`, `up`, `lo` for swapping, resp. changing to upper and lower case of text
* `spt` for splitting function calls and declarations over multiple lines
* `u` for acquisition of Unicode characters not present in US-ASCII

Some of the parameters for these programs are set through environment
variables (although there are usually command-line arguments that
allow you to set them as well), such as `SRC_LANG` for the
programming langauge that is used, or `SRC_INDENT` for the indentation
string that is used.

The programs are written in Python 3, and should be cross-platform
(although some programs are implemented as symbolic links, somewhat
crippling Windows support). If you want to be able to use the
programs anywhere, you can of course add the `bin` folder to your
`PATH` environment variable.

## Examples
### lic, cmt, hello
Let's say you have a burning desire to write a "hello world" C program,
but you can't be bothered to type it out. Also you'd like to claim it
as your own intellectual property and add the ISC license to the top.

Just use:

```bash
$ (export SRC_LANG=c; lic isc | cmt -d; echo; hello) > main.c
```

Behold how `main.c` now contains just what you requested.

### u
Let's say you're learning Icelandic, but can't be bothered to change your
keyboard layout to Icelandic, or even US-Intl. `u` is the program for you!
Simply put the following file in your home directory (or any parent
directory of your working directory) and call it `.urc`.

```json
{
	"ae": "æ",
	"th": "þ",
	"dh": "ð",

	"'": "\u0301",
	"\"": "\u0308"
}
```

Lo and behold:

```bash
$ u ae
æ
$ u ae | up
Æ
$ u o \"
ö
```

## License
Copyright (c) 2017, Antonie Blom

Permission to use, copy, modify, and/or distribute this software for any
purpose with or without fee is hereby granted, provided that the above
copyright notice and this permission notice appear in all copies.

THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES
WITH REGARD TO THIS SOFTWARE INCLUDING ALL IMPLIED WARRANTIES OF
MERCHANTABILITY AND FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR
ANY SPECIAL, DIRECT, INDIRECT, OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES
WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN
ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF
OR IN CONNECTION WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.


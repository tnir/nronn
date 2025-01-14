# nRonn

[![Ruby](https://github.com/n-ronn/nronn/actions/workflows/build.yml/badge.svg)](https://github.com/n-ronn/nronn/actions/workflows/build.yml?query=branch%3Amain)

nRonn is a new, currently-maintained fork of the defunct [original Ronn
project](https://github.com/rtomayko/ronn).

Ronn builds manuals. It converts simple, human readable textfiles to roff for
terminal display, and also to HTML for the web.

The source format includes all of Markdown but has a more rigid structure and
syntax extensions for features commonly found in manpages (definition lists,
link notation, etc.). The ronn-format(7) manual page defines the format in
detail.

The `*.ronn` files found in the [`man/`][1] directory show off a wide range of
ronn capabilities:

* [ronn(1)](https://n-ronn.github.io/nronn/ronn.1.html) command -
  [source file](https://github.com/n-ronn/nronn/blob/main/man/ronn.1.ronn),
  [roff output](https://github.com/n-ronn/nronn/blob/main/man/ronn.1)

* [ronn-format(7)](https://n-ronn.github.io/nronn/ronn-format.7.html) -
  [source file](https://github.com/n-ronn/nronn/blob/main/man/ronn-format.7.ronn),
  [roff output](https://github.com/n-ronn/nronn/blob/main/man/ronn-format.7)

[1]: https://github.com/n-ronn/nronn/tree/main/man

As an alternative, you might want to check out [pandoc](http://johnmacfarlane.net/pandoc/) which can also convert markdown into roff manual pages.

## Installation

Install with `gem` anywhere that supports it:

```bash
gem install nronn
```

See [INSTALLING.md](INSTALLING.md) for details on other systems and installation methods.

## Examples

Build roff and HTML output files for one or more input files:

```bash
$ ronn man/ronn.5.ronn
roff: man/ronn.5
html: man/ronn.5.html
```

Generate only a standalone HTML version of one or more files:

```bash
$ ronn --html man/markdown.5.ronn
html: man/markdown.5.html
```

Build roff versions of all ronn files in a directory:

```bash
$ ronn --roff man/*.ronn
```

View a ronn file as if it were a manpage without building intermediate files:

```bash
$ ronn --man man/markdown.5.ronn
```

View roff output with man(1):

```bash
$ man man/ronn.5
```

The [ronn(1)](https://n-ronn.github.io/nronn/ronn.1.html) manual page includes
comprehensive documentation on `ronn` command line options.

## Background

Some think Unix manual pages are a poor and outdated form of documentation. nRonn
disagrees:

* Manpages follow a well defined structure that's immediately familiar. This
  gives developers a starting point when documenting new tools, libraries, and
  formats.

* Manpages get to the point. Because they're written in an inverted style, with
  a SYNOPSIS section followed by additional detail, prose and references to
  other sources of information, manpages provide the best of both cheat sheet
  and reference style documentation.

* Historically, manpages use an extremely — unbelievably — limited set of
  text formatting capabilities. You get a couple of headings, lists, bold,
  underline and no more. This is a feature.

* Although two levels of section hierarchy are technically supported, most
  manpages use only a single level. Unwieldy document hierarchies complicate
  otherwise good documentation. Remember that Feynman covered all of physics
  — heavenly bodies through QED — with only two levels of document hierarchy
  (_The Feynman Lectures on Physics_, 1970).

* The classical terminal manpage display is typographically well thought out.
  Big bold section headings, justified monospace text, nicely indented
  paragraphs, intelligently aligned definition lists, and an informational
  header and footer.

* Manpages have a simple referencing syntax; e.g., sh(1), fork(2), markdown(7).
  HTML versions can use this to generate links between pages.

Unfortunately, figuring out how to create a manpage is a fairly tedious process.
The roff/mandoc/mdoc macro languages are highly extensible, fractured between
multiple dialects, and include a bunch of device-specific stuff irrelevant to
modern publishing tools. Ronn aims to solve that problem.

## Requirements

Ruby 2.3 or newer, and gems as listed in `nronn.gemspec`.

## Project Management

The project home page is at <https://github.com/n-ronn/nronn>. Bug reports,
feature requests, and patch submissions are welcome.

## License and Copying

MIT License.

See [LICENSE.txt](LICENSE.txt) for detail.

## JRuby support

JRuby is not supported yet:

[![JRuby](https://github.com/n-ronn/nronn/actions/workflows/jruby.yml/badge.svg)](https://github.com/n-ronn/nronn/actions/workflows/jruby.yml)

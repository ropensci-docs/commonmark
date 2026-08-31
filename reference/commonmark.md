# Parse and render markdown text

Converts markdown text to several formats using John MacFarlane's
[cmark](https://github.com/commonmark/cmark) reference implementation.
Supported output formats include `html`, `latex`, groff `man`, and
normalized "commonmark" markdown. In addition the markdown parse tree
can be returned in xml format.

## Usage

``` r
markdown_html(
  text,
  hardbreaks = FALSE,
  smart = FALSE,
  normalize = FALSE,
  sourcepos = FALSE,
  footnotes = FALSE,
  extensions = FALSE
)

markdown_xml(
  text,
  hardbreaks = FALSE,
  smart = FALSE,
  normalize = FALSE,
  sourcepos = FALSE,
  footnotes = FALSE,
  extensions = FALSE
)

markdown_man(
  text,
  hardbreaks = FALSE,
  smart = FALSE,
  normalize = FALSE,
  footnotes = FALSE,
  width = 0,
  extensions = FALSE
)

markdown_commonmark(
  text,
  hardbreaks = FALSE,
  smart = FALSE,
  normalize = FALSE,
  footnotes = FALSE,
  width = 0,
  extensions = FALSE
)

markdown_text(
  text,
  hardbreaks = FALSE,
  smart = FALSE,
  normalize = FALSE,
  footnotes = FALSE,
  width = 0,
  extensions = FALSE
)

markdown_latex(
  text,
  hardbreaks = FALSE,
  smart = FALSE,
  normalize = FALSE,
  footnotes = FALSE,
  width = 0,
  extensions = FALSE
)
```

## Arguments

- text:

  Markdown text

- hardbreaks:

  Treat newlines as hard line breaks. If this option is specified, hard
  wrapping is disabled regardless of the value given with `width`.

- smart:

  Use smart punctuation. See details.

- normalize:

  Consolidate adjacent text nodes.

- sourcepos:

  Include source position attribute in output.

- footnotes:

  parse footnotes

- extensions:

  Enables Github extensions. Can be `TRUE` (all) `FALSE` (none) or a
  character vector with a subset of available
  [extensions](https://docs.ropensci.org/commonmark/reference/extensions.md).

- width:

  Specify wrap width (default 0 = nowrap).

## Details

Support for extensions (including tables and autolink) is provided via
the Github [fork](https://github.com/github/cmark-gfm) of cmark. For now
these are opt-in and have to be enabled with the `extensions` parameter.
See also the manual page on
[extensions](https://docs.ropensci.org/commonmark/reference/extensions.md).

When smart punctuation is enabled, straight double and single quotes
will be rendered as curly quotes, depending on their position. Moreover
`--` will be rendered as – (en-dash), `---` will be rendered as —
(em-dash), and `...` will be rendered as ... (ellipses).

## Examples

``` r
md <- readLines("https://raw.githubusercontent.com/yihui/knitr/master/NEWS.md")
html <- markdown_html(md)
xml <- markdown_xml(md)
man <- markdown_man(md)
tex <- markdown_latex(md)
cm <- markdown_commonmark(md)
text <- markdown_text(md)
```

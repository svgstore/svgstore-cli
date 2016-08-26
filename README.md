# svgstore-cli

A command-line tool for combining SVG files into a single sprite sheet using
`<symbol>` tags.

## Installation

```
npm install -g svgstore-cli
```

## Usage

```
svgstore [-o OUTFILE] [-p PREFIX] [--inline] INPUT ...
```

* Multiple input files can be specified
* Input files can be globs (e.g., `**/*.svg`)
* Output to stdout by default
* Can direct output to a file with the `-o outfile` flag
* Can prefix the symbol names using the `-p prefix` flag
* Supports `--inline` to avoid generating XML doctype

---

Licensed under [MIT](https://github.com/svgstore/svgstore-cli/blob/master/LICENSE)

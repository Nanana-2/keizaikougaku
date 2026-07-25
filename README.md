# Economic Engineering I

This repository contains a Japanese lecture-note project for the 2026 course
"Economic Engineering I". The main deliverable is a Japanese LaTeX
textbook covering financial markets, time value, portfolio theory, derivatives,
binomial models, and the Black-Scholes model.

The repository is primarily a source-and-reference repository. The `.tex` files
are authoritative; generated LaTeX files are deliberately ignored by Git.

## Repository layout

```text
.
|-- textbook/
|   |-- main.tex              # LaTeX entry point
|   `-- chapters/ch01.tex ... # Chapter sources
|-- materials/
|   |-- lectures/             # Original course handouts, in Japanese
|   |-- answers/              # Exercise-answer PDFs
|   `-- supplements/          # Supplementary handouts and topic-specific PDFs
|-- .gitignore
`-- README.md
```

The PDFs under `materials/` are reference material and are intentionally kept
under version control. Their original filenames are preserved so that they can
be matched to the course materials and to references in the chapter sources.

## Building the textbook

Build from the `textbook/` directory with LuaLaTeX:

```powershell
cd textbook
lualatex main.tex
lualatex main.tex
```

Running LaTeX twice refreshes cross-references and the table of contents. If
`latexmk` is available, the equivalent command is:

```powershell
cd textbook
latexmk -lualatex main.tex
```

The generated PDF is `textbook/main.pdf`. It is a local build artifact and is
ignored by Git. Auxiliary files such as `.aux`, `.log`, `.out`, and `.toc` are
also ignored.

The document uses Japanese LaTeX packages, including `jlreq` and `luatexja`,
and therefore requires a LuaLaTeX installation with the required Japanese
fonts and packages. The source was authored in Japanese; do not translate or
normalize the chapter text unless explicitly requested.

## Working conventions for AI agents

1. Read `textbook/main.tex` before editing chapter files. It defines the
   document class, packages, theorem environments, colors, and chapter order.
2. Treat `textbook/chapters/chNN.tex` as the source of truth for chapter
   content. Chapter files are included from `main.tex` with `\input`.
3. Keep generated files out of commits. Do not add `.aux`, `.log`, `.out`,
   `.toc`, or generated PDFs from `textbook/` unless the user explicitly asks
   for a build artifact.
4. Keep reference PDFs under `materials/`. Preserve their filenames when
   possible; if a file must be renamed, update all references and explain the
   mapping in the change.
5. Preserve Japanese text and UTF-8 filenames. Be careful when using tools that
   may interpret the files using a non-UTF-8 console encoding.
6. After changing LaTeX, compile the document when the local TeX environment is
   available and inspect the resulting log for errors. A successful source edit
   does not necessarily imply a successful PDF build.

## Scope and provenance

The textbook is a reconstructed and expanded set of course notes based on the
included handouts and answer materials. The files under `materials/` are
reference inputs, not generated outputs. Check the source documents and the
course context before treating any statement as an official syllabus,
assessment, or current financial guidance.

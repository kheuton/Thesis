# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A PhD dissertation in LaTeX for Tufts University (Computer Science). The thesis is a work in progress — the `bpr` chapter is the author's content currently being ported from docx to tex. Other chapter directories (`semi_supervised_pchmm_missing_data`, `irregular_time_series_data_driven_missingness`) contain placeholder content being replaced.

**Important:** This is a thesis — never add, rephrase, or modify thesis prose without an explicit request. Only make the exact change asked for.

## Git workflow

Commit small, focused changes frequently to make rollbacks easy.

## Building

```bash
# Full build with bibliography
latexmk -pdf thesis_main.tex

# Or manually (run pdflatex 2-3 times with bibtex in between)
pdflatex thesis_main.tex && bibtex thesis_main && pdflatex thesis_main.tex && pdflatex thesis_main.tex
```

Build artifacts (`.aux`, `.bbl`, `.log`, `.toc`, etc.) are gitignored. Output is `thesis_main.pdf`.

## Structure

- `thesis_main.tex` — root document; sets title/author/metadata, inputs all chapters
- `mytuftsthesis.cls` — custom Tufts PhD thesis document class (based on `book`)
- `matscript.sty` — shared math/figure/theorem package
- `refs/thesisbib.bib` — single BibTeX bibliography for all citations
- `content/` — thesis content files, organized by chapter under `content/chapters/`

## Macros

Defined in `matscript.sty` (shared): `\norm{}`, `\abs{}`, `\alert{}` (red text for drafts), `\code{}`, theorem environments.

Defined in `thesis_main.tex` (thesis-specific): `\xobs`, `\til{}`, `\tpc`, `\fpc`, `\compactsum{}{}`.

## Draft vs. final mode

Line 1 of `thesis_main.tex` toggles the mode:
- `final` — double spacing (submission)
- `draft` — single spacing (editing)

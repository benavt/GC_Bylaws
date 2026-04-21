# GC Bylaws

This repository contains the Graduate Council bylaws source for the
`2026-04-21` branch revision.

The canonical LaTeX source is [GC_Bylaws.tex](/Users/tiburon/Desktop/StuGov/T_for_GM/GC_Bylaws/GC_Bylaws.tex).
It compiles to `GC_Bylaws.pdf` and uses the shared `union-doc.cls` document
class from the nested `union-docs-latex-class` submodule.

## Repository Layout

- `GC_Bylaws.tex`: the single source file for the bylaws on this branch
- `.github/workflows/compile-latex.yml`: GitHub Actions workflow that compiles
  the document and uploads the PDF artifact
- `union-docs-latex-class/`: git submodule containing the shared LaTeX class,
  fonts, and official Union logos

## Getting Started

After cloning the repo, initialize the submodule:

```bash
git submodule update --init --recursive
```

To build the PDF locally:

```bash
latexmk -lualatex -shell-escape GC_Bylaws.tex
```

Run the build twice if you are using `lualatex` directly so the table of
contents is fully populated.

## Notes

- The document uses LuaLaTeX and requires shell escape enabled.
- The shared class repo provides the fonts and branding assets, so the local
  `Font_Assets` directory is no longer used on this branch.

# GC Bylaws

This repository stores the Graduate Council bylaws source for the revision
associated with the March 21, 2025 amendment process.

The primary LaTeX source is `GC_Bylaws.tex`, which compiles to `GC_Bylaws.pdf`.
The document uses the shared `union-doc.cls` class and branding assets from the
nested `union-docs-latex-class` git submodule.

## Repository Layout

- `GC_Bylaws.tex`: the single source file for the bylaws on this branch
- `GC_24-25_BL_Amd_2_2025-03-21.pdf`: the amendment motion that added the
  Masters'/Co-term representation provisions and expanded non-voting graduate
  organization representation
- `.github/workflows/compile-latex.yml`: CI workflow that builds the PDF and
  uploads the artifact
- `union-docs-latex-class/`: submodule containing the shared class, fonts, and
  official Union logos

## Getting Started

After cloning, initialize the submodule:

```bash
git submodule update --init --recursive
```

To build locally:

```bash
latexmk -lualatex -shell-escape GC_Bylaws.tex
```

Run the document twice if you are invoking `lualatex` directly so the table of
contents is fully populated.

For editing guidance, look at the example document in the submodule at
`union-docs-latex-class/demo/v1/demo.tex`. It shows the expected `union-doc`
class structure and the document commands used to format Union documents.

## Notes

- This repo uses LuaLaTeX.
- Shell escape is required during compilation.
- The old top-level `Font_Assets` directory is no longer used on this branch;
  fonts come from the `union-docs-latex-class` submodule.

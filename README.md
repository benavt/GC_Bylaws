# GC Bylaws

This repository holds the **LaTeX source and compiled PDF of the Bylaws of the
Rensselaer Union Graduate Student Council (GC)**. It is maintained by the
Graduate Student Council and the Student Senate so that the current, approved
version of the document is always available as both an editable source and a
typeset PDF.

## What's in here

| File / folder | Purpose |
| --- | --- |
| `GC_Bylaws.tex` | The primary source — the full text of the Bylaws, marked up in LaTeX. Edit this to propose changes. |
| `GC_Bylaws.pdf` | The compiled, shareable copy. Regenerated automatically on every push (see below). |
| `union-docs-latex-class/` | Git submodule pointing at [`benavt/union-docs-latex-class`](https://github.com/benavt/union-docs-latex-class). Provides the shared `union-doc.cls` class, Union fonts, and logo assets so every Union governing document has a consistent look. |
| `.github/workflows/compile-latex.yml` | GitHub Actions workflow that compiles the `.tex` to PDF, uploads it as a build artifact, and commits the updated `GC_Bylaws.pdf` back to the branch. |
| `LICENSE` | License covering the contents of this repository. |

## How the document is structured

`GC_Bylaws.tex` uses the `union-doc` class from the submodule. The top of the
file only configures document metadata (title, subtitle, cover logo, cover
note, TOC depth, etc.); the body then uses a small set of class-provided
commands — `\DocArticle`, `\DocParagraph`, and standard `enumerate`
environments — to write the articles of the Bylaws. Current articles:

1. Preamble
2. Purpose
3. Eligibility
4. Membership
5. Elections and Terms of Office
6. Officers
7. Meetings
8. Graduate Student Council Responsibilities
9. Amendments

Per Article IX, amendments must be proposed at least one week before adoption
and require a two-thirds majority of the voting membership of the Council.

## Cloning

Because the class files live in a submodule, clone with submodules initialized:

```bash
git clone --recurse-submodules https://github.com/benavt/GC_Bylaws.git
```

If you already cloned without submodules, run:

```bash
git submodule update --init --recursive
```

## Building locally

You need a TeX distribution with **LuaLaTeX** (TeX Live 2022+ or MacTeX
recommended), plus `latexmk`. From the repo root:

```bash
latexmk -lualatex -shell-escape GC_Bylaws.tex
```

or, equivalently, a direct LuaLaTeX invocation run twice so the table of
contents resolves:

```bash
lualatex --shell-escape GC_Bylaws.tex
lualatex --shell-escape GC_Bylaws.tex
```

The output is `GC_Bylaws.pdf`.

## Automated builds

Every push that touches `GC_Bylaws.tex`, the workflow, the submodule, or
`.gitmodules` triggers `.github/workflows/compile-latex.yml`, which:

1. Checks out the repo with submodules.
2. Compiles `GC_Bylaws.tex` with `xu-cheng/latex-action` using LuaLaTeX and
   the fonts bundled in the `union-docs-latex-class` submodule.
3. Uploads the resulting PDF as a workflow artifact (`compiled-pdfs`).
4. On `push` events, commits the updated `GC_Bylaws.pdf` back to the branch
   so the repo always carries a current typeset copy.

The workflow can also be run manually from the Actions tab via
**workflow_dispatch**.

## Proposing changes

1. Open a branch and edit `GC_Bylaws.tex`.
2. Verify the document still compiles locally (or rely on the CI build).
3. Open a pull request. The CI workflow will compile the PDF and attach it
   as an artifact so reviewers can read the rendered result.
4. Once the amendment is adopted by the Council (and, where required,
   presented to the Student Senate), merge the PR so the committed PDF
   reflects the newly adopted text.

## Questions

For questions about the Bylaws themselves, email
[grad-council@rpi.edu](mailto:grad-council@rpi.edu).

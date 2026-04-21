# GC Bylaws

This repository contains the Graduate Council bylaws source for the
`2026-04-21` branch revision.

The canonical LaTeX source is [`GC_Bylaws.tex`](GC_Bylaws.tex).
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

## Git conventions for Union documents

When you commit changes to a Union governing document, write the commit message
so someone reviewing the history can immediately tell **what changed** and
**which final approval date the text corresponds to**.

### Recommended commit format

Use this pattern:

```text
<document name>: <short description> (final approval: YYYY-MM-DD)
```

Examples:

- `Senate Bylaws: update election procedure language (final approval: 2026-04-21)`
- `Union Constitution: incorporate approved amendment 3 (final approval: 2026-02-06)`
- `Executive Board Rules: fix numbering and adopted wording (final approval: 2025-11-14)`

Conventions to follow:

- Use the **final approval date**, not the date you happened to make the edit.
- Write the date in **ISO format**: `YYYY-MM-DD`.
- Keep the subject line focused on the approved change itself, not on your
  editing process. For example, prefer `incorporate approved budget language`
  over `make edits from meeting`.
- If a change has **not** received final approval yet, make that explicit in
  the commit message instead of guessing a date. For example:
  `Senate Bylaws: draft revisions for review (pending final approval)`.

This convention makes it much easier to audit the repository later against
minutes, ratification records, and released PDFs.

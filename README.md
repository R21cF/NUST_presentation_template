# Beamer_template_NUST

An unofficial beamer template for research presentations by NUST postgraduate students
(proposal defence, pre-defence, final defence). The layout was taken from a finished MS
pre-defence deck, so every frame of the usual defence outline is already present with
placeholder text and a layout that has been used in front of a committee.

## Files

| File | Purpose |
|---|---|
| `NUST_presentation_template.tex` | The template. Edit the bracketed placeholders and the frame bodies. |
| `references.bib` | Three dummy entries so the `\cite` commands resolve. Replace with your own bibliography, or delete it: the bibliography is optional (see below). |
| `nust-logo.png` | Title-page logo. |

## Build

```
latexmk -pdf NUST_presentation_template.tex
```

The bibliography is optional. If `references.bib` is present next to the `.tex` file it is
used (biblatex, IEEE numeric style, which needs `biber`); if it is absent, biblatex is not
loaded, every `\cite` prints nothing, and the References frame is skipped, so the file builds
with `pdflatex` alone. Figures are looked up in
the template directory and in `figures/`; the placeholder grey boxes are drawn with TikZ and
are meant to be replaced by `\includegraphics`.

## What is in it

- **Aspect ratio is one setting**: the `aspectratio=` number on the `\documentclass` line
  (`43` by default; `169` for widescreen; `1610`, `149`, `141`, `54`, `32` also work). Widths
  in the file are fractions of the text width and placeholder heights fractions of the frame
  height, and the fixed-width result tables sit in `adjustbox` so they shrink to their column,
  so a change of ratio needs no other edit. Check the densest frames after switching.
- `infolines` outer theme, `rectangles` inner theme, a NUST red/grey colour scheme defined
  once at the top (`nustred`, `nustgrey`).
- A title page carrying the defence type, degree, supervisor and department.
- A two-column outline that splits the ten numbered sections five and five; adjust the
  `sections=` ranges if you add or remove sections.
- One frame per section of the outline: Introduction (background, motivation), Literature
  Review (two review frames, research gaps), Problem Statement, Research Questions, Research
  Objectives, Methodology (justification, alternatives, three "details" frames with the
  construction / baseline / protocol tables), Implementation, Results and Evaluation (five
  result-frame layouts, the "how the research questions are answered" tables, discussion,
  threats to validity), Conclusion (with limitations and future work), a links frame, the
  reference list and a closing frame.
- Helpers: `\placeholderfig{width}{height}{text}` for a figure stand-in (width as a fraction
  of the current text width, height as a fraction of the frame height), `\rqplus` /
  `\rqminus` markers for the summary tables, and `Y` / `F` column types for the wide
  `tabularx` tables.

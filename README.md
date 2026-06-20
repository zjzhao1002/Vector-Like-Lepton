# Constraints on New Physics Particles

This repository collects working notes and presentation material on current LHC constraints for vector-like leptons and other beyond-the-Standard-Model particles. The material covers vector-like and long-lived leptons, heavy vector bosons, neutral and charged Higgs bosons, doubly charged Higgs bosons, and several long-lived supersymmetric-particle scenarios.

The repository contains two LaTeX documents:

- [Draft article](draft/JHEP.pdf), typeset with the JHEP style and supported by a BibTeX database.
- [Presentation](slides/pre.pdf), typeset with Beamer and a custom university theme.

Both documents are works in progress; check the cited ATLAS and CMS publications before using numerical limits in new work.

## Repository structure

| Path | Description |
| --- | --- |
| `draft/main.tex` | Main source for the JHEP-style article |
| `draft/biblio.bib` | BibTeX references used by the article |
| `draft/jheppub.sty` | Local JHEP document style |
| `draft/JHEP.bst` | JHEP bibliography style |
| `draft/JHEP.pdf` | Pre-built article PDF |
| `slides/pre.tex` | Main source for the Beamer presentation |
| `slides/collegebeamer.sty` | Custom 16:9 Beamer theme |
| `slides/src/` | Logos and backgrounds for the supported themes |
| `slides/img/` | Figures used by the presentation |
| `slides/gallery/` | Theme and layout examples |
| `slides/pre.pdf` | Pre-built presentation PDF |

## Requirements

A reasonably complete TeX Live installation is recommended. The build uses:

- `latexmk`, pdfLaTeX, and BibTeX for the article;
- `latexmk` and XeLaTeX for the slides;
- common LaTeX packages including Beamer, `xeCJK`, `mathbbol`, `threeparttable`, `booktabs`, `makecell`, TikZ, and `animate`.

On macOS, these tools and packages are available in a full MacTeX installation. On Linux, install the equivalent TeX Live package groups provided by your distribution.

## Building

Clone the repository:

```bash
git clone https://github.com/zjzhao1002/Vector-Like-Lepton.git
cd Vector-Like-Lepton
```

Build the article from the repository root. The `-cd` option makes `latexmk` compile inside the source directory, where it can find the local JHEP style and bibliography files:

```bash
latexmk -cd -pdf draft/main.tex
```

The generated document is `draft/main.pdf`. To remove auxiliary build files:

```bash
latexmk -cd -c draft/main.tex
```

Build the slides with XeLaTeX; compiling inside `slides/` ensures that the image paths resolve correctly:

```bash
latexmk -cd -xelatex slides/pre.tex
```

The generated presentation is `slides/pre.pdf`. Clean its auxiliary files with:

```bash
latexmk -cd -c slides/pre.tex
```

## Editing the material

Add or update article references in `draft/biblio.bib`, then cite their BibTeX keys from `draft/main.tex`. `latexmk` automatically runs BibTeX and repeats the required LaTeX passes.

The presentation theme is selected in `slides/pre.tex`:

```tex
\usepackage[hnu,en]{collegeBeamer}
```

The first option selects the visual identity and the second selects the language. The bundled visual options are `polyu`, `szu`, `hnu`, `swu`, `hit`, `saes`, and `red`; the language options are `en` and `zh`. Slides using Chinese text should be compiled with XeLaTeX.

When adding figures, place presentation assets under `slides/img/` and keep paths relative to the `slides/` directory.

## Build notes

The current sources compile successfully with TeX Live 2024. The article build reports a duplicate `table:vll` label and a few typesetting warnings; the slide build reports non-fatal font and PDF-bookmark warnings. These do not prevent PDF generation, but should be reviewed before publication.

# apa2bib

apa2bib is a command line utility for converting APA-formatted references into [bibtex](http://www.bibtex.org/) references for use with [latex](http://www.latex-project.org/). apa2bib is written in [perl](http://www.perl.org/) and works by matching references to regular expressions. apa2bib works with books (with volume and edition numbers), chapters in edited books, journal articles, magazine articles (e.g., Science and Nature), and in-press, submitted and unpublished manuscripts.

By using the [APA6](http://www.ctan.org/pkg/apa6) latex package and the [apacite](http://www.ctan.org/tex-archive/biblio/bibtex/contrib/apacite/) bibtex package, one can produce APA-formatted manuscripts using latex. (These files are packaged in the [tex-live](http://www.tug.org/texlive/) distribution of tex and latex.)

Here is an example of apa2bib at work:

```bash
echo "Stewart, N., & Ellis, A. W. (2008). Order of acquisition in learning perceptual categories: A laboratory analogue of the age of acquisition effect? Psychonomic Bulletin & Review, 15, 70-74." | apa2bib

@article{StewartEllis08,
author  = {Stewart, N. and Ellis, A. W.},
year    = {2008},
title   = {Order of acquisition in learning perceptual categories: A laboratory analogue of the age of acquisition effect?},
journal = {Psychonomic Bulletin \& Review},
volume  = {15},
pages   = {70--74},
}

```

A text file of many APA formatted references can be converted into a file of bibtex formatted entries:



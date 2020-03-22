# apa2bib

apa2bib is a command line utility for converting APA-formatted references into [bibtex](http://www.bibtex.org/) references for use with [latex](http://www.latex-project.org/). 

apa2bib contains some useful perl regular expressions (regexes) for parsing APA formatted references.

apa2bib is written in [perl](http://www.perl.org/) and works by matching references to regular expressions. apa2bib works with books (with volume and edition numbers), chapters in edited books, journal articles, magazine articles (e.g., Science and Nature), and in-press, submitted and unpublished manuscripts.

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

```bash
apa2bib < refs.txt > refs.bib
```

apa2bib performs error checking. It makes the bibtex entry and then uses the entry to regenerate the original reference. If the two do not match, then the best guess at the bibtex entry is printed with a warning. For example:

```bash
echo "Stewart, N., Ellis, A. W. (2008). Order of acquisition in learning perceptual categories: A laboratory analogue of the age of acquisition effect? Psychonomic Bulletin & Review, 15, 70-74." | apa2bib

ORIGINAL:      Stewart, N., Ellis, A. W. (2008). Order of acquisition in learning perceptual categories: A laboratory analogue of the age of acquisition effect? Psychonomic Bulletin & Review, 15, 70-74.
RECONSTRUCTED: Stewart, N., & Ellis, A. W. (2008). Order of acquisition in learning perceptual categories: A laboratory analogue of the age of acquisition effect? Psychonomic Bulletin & Review, 15, 70-74.
RAW:           Stewart, N., Ellis, A. W. (2008). Order of acquisition in learning perceptual categories: A laboratory analogue of the age of acquisition effect? Psychonomic Bulletin & Review, 15, 70-74.
@article{StewartEllis08,
author  = {Stewart, N. and Ellis, A. W.},
year    = {2008},
title   = {Order of acquisition in learning perceptual categories: A laboratory analogue of the age of acquisition effect?},
journal = {Psychonomic Bulletin \& Review},
volume  = {15},
pages   = {70--74},
}
```

Because the original reference here is missing an "&" between the author names, the reconstructed version does not match. But, in this case, the best guess at the bibtex reference is correct.

# Thanks

Thanks to Tim Kelly for code for issue numbers and DOIs.

# Options

apa2bib takes two command line options.

* --no-check disables checking

* --help displays brief help

# Installing

apa2bib requires perl. I used perl version 5.8.8. You'll need these three files

* apa2bib --- The main perl script

* apa2bib_makefile --- This makefile uses latex to build a dvi file containing the reference during the error checking process

* apa2bib_process --- This bash shell script processes the text output from the dvi file back into the plain text format for comparison with the original during the error check process

Copy these three files to the same location in your \$PATH (e.g., ~/bin). apa2bib and apa2bib_process will need to be executable (chmod +x apa2bib apa2bib_process).

For the error checking you'll need latex installed with the apa6 latex style and the apacite referencing installed, but you need these anyway to make your manuscripts. You'll also need dvi2tty to convert latex references back into text to compare with the original. When running apa2bib with the --no-check option you don't need these dependencies and you don't need apa2bib_makefile or apa2bib_process.

# Bugs

I've tested apa2bib on a set of about 2,000 references, but if you find any bugs please e-mail [neil.stewart@wbs.ac.uk](mailto:neil.stewart@wbs.ac.uk). Include the APA formatted reference text file, the version of apa2bib, and any output. Bug fixes are especially welcome.



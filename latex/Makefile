# Makefile to create PDF documents from LaTeX-Files
# Needed software packages: pdflatex, rubber
# License: No copyright, just do what the heck you want with it



SUBDIR_ROOTS := TeX_files 
DIRS := . $(shell find $(SUBDIR_ROOTS) -type d )
GARBAGE_PATTERNS := "*.gz(busy)" *.aux *.log  *.aux *.bbl *.log *.out *.synctex.gz *.fls *.toc 
GARBAGE_PATTERNS_ALL := "*.gz(busy)" *.aux *.log *.pdf *.aux *.bbl *.log *.out *.synctex.gz *.fls *.toc *.dvi 
GARBAGE := $(foreach DIR,$(DIRS),$(addprefix $(DIR)/,$(GARBAGE_PATTERNS)))
GARBAGE_ALL := $(foreach DIR,$(DIRS),$(addprefix $(DIR)/,$(GARBAGE_PATTERNS_ALL)))


all: pdf clean

pdf:
	for file in $$(ls *tex | cut -d \. -f 1) ; do make $$file.pdf ; done

%.pdf: %.tex
	rubber -m pdftex $<
	mv $@ ../target/pdf/

clean:
	rm -f $(GARBAGE_PATTERNS) 

cleanall:
	rm -f $(GARBAGE_PATTERNS_ALL) 

.PHONY: all pdf clean cleanall
.SILENT: pdf

# vim: set tabstop=4 shiftwidth=4 noexpandtab

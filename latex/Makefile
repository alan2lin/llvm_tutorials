# Makefile to create PDF documents from LaTeX-Files
# Needed software packages: pdflatex, rubber
# License: No copyright, just do what the heck you want with it



SUBDIR_ROOTS := TeX_files 
DIRS := . $(shell find $(SUBDIR_ROOTS) -type d )
GARBAGE_PATTERNS := "*.gz(busy)" *.aux *.log  *.aux *.bbl *.log *.out *.synctex.gz *.fls *.toc 
GARBAGE_PATTERNS_ALL := $(GARBAGE_PATTERNS) *.pdf  *.dvi *.md 
GARBAGE := $(foreach DIR,$(DIRS),$(addprefix $(DIR)/,$(GARBAGE_PATTERNS)))
GARBAGE_ALL := $(foreach DIR,$(DIRS),$(addprefix $(DIR)/,$(GARBAGE_PATTERNS_ALL)))


all: pdf md clean
pdf: zh_pdf mix_pdf 
md: zh_md

zh_pdf:
	@echo "纯中文版生成开始...."
	for file in $$(ls *tex | cut -d \. -f 1) ; do make $${file}_zh.pdf ; done


%_zh.pdf: %.tex
	@echo "纯中文版生成...."
	rubber -m pdftex --jobname=$(basename $<)_zh $< 
	@echo "拷贝到targe...."
	mv $@ ../target/pdf/

mix_pdf:
	@echo "双语版生成开始...."
	for file in $$(ls *tex | cut -d \. -f 1) ; do make $${file}_mix.pdf ; done

%_mix.pdf: %.tex
	@echo "双语版生成...."
	rubber -m pdftex --jobname=$(basename $<)_mix $< 
	@echo "拷贝到targe...."
	mv $@ ../target/pdf/

zh_md:
	@echo "md版生成..."
	for file in $$(ls *tex | cut -d \. -f 1) ; do make $${file}_zh.md ; done

%_zh.md: %.tex
	@echo "纯中文版生成...."
	pandoc -f latex -t markdown $< -o $(basename $<)_zh.md
	@echo "拷贝到targe...."
	mv $@ ../target/md/

clean:
	@echo "清理...."
	rm -f $(GARBAGE_PATTERNS) 

cleanall:
	@echo "清理所有...."
	echo $(GARBAGE_ALL)
	rm -f $(GARBAGE_ALL) 

.PHONY: all pdf zh_pdf clean cleanall
.SILENT: pdf

# vim: set tabstop=4 shiftwidth=4 noexpandtab

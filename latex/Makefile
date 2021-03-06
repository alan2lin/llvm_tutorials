# Makefile to create PDF documents from LaTeX-Files
# Needed software packages: pdflatex, rubber
# License: No copyright, just do what the heck you want with it



SUBDIR_ROOTS := chapters 
DIRS := . $(shell find $(SUBDIR_ROOTS) -type d ) resources/images-gen
GARBAGE_PATTERNS := "*.gz(busy)" *.aux *.log  *.aux *.bbl *.log *.out *.synctex.gz *.fls *.toc \
       	*.nlo *.nls \
	*.glo *.glg *.gls *.ist *.ilg \
	*.acn *.acr *.alg 
GARBAGE_PATTERNS_ALL := $(GARBAGE_PATTERNS) *.pdf  *.dvi *.md *.svg *.png *.jpg
GARBAGE := $(foreach DIR,$(DIRS),$(addprefix $(DIR)/,$(GARBAGE_PATTERNS)))
GARBAGE_ALL := $(foreach DIR,$(DIRS),$(addprefix $(DIR)/,$(GARBAGE_PATTERNS_ALL))) 
TARGET_DIR := ../target
TARGET_FILES :=$(shell find $(TARGET_DIR)/ -type f -name "*" )
RESOURCES_DIR := resources
DOT_FILES := $(shell find $(RESOURCES_DIR)/dot/ -type f -name "*.dot" )

view: all openpdf
all: pdf md clean 
pdf: zh_pdf mix_pdf 
md: zh_md mix_md


zh_pdf: common_dep
	@echo "纯中文版pdf生成开始...."
	for file in $$(ls *tex | cut -d \. -f 1) ; do make $${file}_zh.pdf ; done


%_zh.pdf: %.tex
	@echo "纯中文版pdf生成...."
#	rubber -m pdftex --jobname=$(basename $<)_zh   $< 
#	latex --jobname=$(basename $<)_zh  '\newcommand{\eng}{false} \input{$<}'   
#	dvipdf $(basename $<)_zh.dvi
	xelatex -jobname=$(basename $<)_zh  '\newcommand{\eng}{false} \input{$<}'   
	makeglossaries $(basename $<)_zh
	makeindex $(basename $<)_zh.nlo -s `apt-file search nomencl.ist | cut -d \: -f 2` -o $(basename $<)_zh.nls
	xelatex -jobname=$(basename $<)_zh  '\newcommand{\eng}{false} \input{$<}'   
	@echo "拷贝到target...."
	mv $@ $(TARGET_DIR)/pdf/

mix_pdf: common_dep
	@echo "双语版生pdf成开始...."
	for file in $$(ls *tex | cut -d \. -f 1) ; do make $${file}_mix.pdf ; done

%_mix.pdf: %.tex
	@echo "双语版pdf生成...."
#	rubber -m pdftex --jobname=$(basename $<)_mix  $< 
#	latex --jobname=$(basename $<)_mix  '\newcommand{\eng}{true} \input{$<}'  
#	dvipdf $(basename $<)_mix.dvi
	xelatex -jobname=$(basename $<)_mix  '\newcommand{\eng}{true} \input{$<}'  
	makeglossaries $(basename $<)_mix
	makeindex $(basename $<)_mix.nlo -s `apt-file search nomencl.ist | cut -d \: -f 2` -o $(basename $<)_mix.nls
	xelatex -jobname=$(basename $<)_mix  '\newcommand{\eng}{true} \input{$<}'  
	@echo "拷贝到target...."
	mv $@ $(TARGET_DIR)/pdf/

zh_md: common_dep
	@echo "纯中文版md开始..."
	for file in $$(ls *tex | cut -d \. -f 1) ; do make $${file}_zh.md ; done

%_zh.md: %.tex
	@echo "纯中文版md生成...."
	pandoc -f latex -t markdown $< -o $(basename $<)_zh.md
	@echo "拷贝到targe...."
	mv $@ $(TARGET_DIR)/md/

mix_md: common_dep
	@echo "双语版md开始..."
	for file in $$(ls *tex | cut -d \. -f 1) ; do make $${file}_mix.md ; done

%_mix.md: %.tex
	@echo "纯中文版md生成...."
	pandoc -f latex -t markdown $< -o $(basename $<)_mix.md
	@echo "拷贝到targe...."
	mv $@ $(TARGET_DIR)/md/

common_dep:
	@echo " commond dependency..."
	mkdir -p $(TARGET_DIR)/pdf/
	mkdir -p $(TARGET_DIR)/md/resources
	dot -Tsvg $(DOT_FILES) -o $(RESOURCES_DIR)/images-gen/$(basename $(notdir $(DOT_FILES))).svg 
	cp -R $(RESOURCES_DIR)/images-gen $(TARGET_DIR)/md/resources
	cp -R $(RESOURCES_DIR)/images $(TARGET_DIR)/md/resources

clean:
	@echo "清理...."
	rm -f $(GARBAGE) 

cleanall:
	@echo "清理所有...."
	rm -f $(GARBAGE_ALL) 
	rm -rf $(TARGET_DIR)/*

init_ubuntu:
	@echo "在ubuntu下安装相关的依赖包"
	sudo apt-file  update
	sudo apt update -y
	sudo apt upgrade -y
	sudo apt install -y texstudio texstudio-doc  texstudio-l10n latex-cjk-all texlive-xetex texlive-lang-chinese texlive-fonts-extra texlive-latex-extra texlive-latex-recommended texlive-publishers latexmk
	sudo apt install -y rubber  pandoc pandoc-citeproc pandoc-citeproc-preamble  pandoc-data pandoc-sidenote graphviz

init_centos:
	@echo "在centos下安装相关的依赖包"
	@echo "尚未实现 todo...."

openpdf:
	xdg-open $(TARGET_DIR)/pdf/llvm_tutorials_mix.pdf

.PHONY: all pdf zh_pdf mix_pdf md zh_md mix_md init_ubuntu init_centos clean cleanall view 
.SILENT: pdf

# vim: set tabstop=4 shiftwidth=4 noexpandtab

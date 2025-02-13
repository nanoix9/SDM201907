all: test_paper

# If you decide to go with pandoc-citeproc
#	pandoc -s -F pandoc-crossref -F pandoc-citeproc meta.yaml --data-dir=data-dir --template=mytemplate.tex -N \
#	-f markdown -t latex+raw_tex+tex_math_dollars+citations -o main.pdf main.md

# You can still use pandoc-crossref to easily reference figures with [@fig:label]

STYLE_DIR=../style
STYLE=$(STYLE_DIR)/apa-aut.csl
DOC_STYLE=$(STYLE_DIR)/sdm.docx
TEX_TMPL=$(STYLE_DIR)/sdm.tex
CSS_FILE=$(STYLE_DIR)/aut.css

NAME=ass1a
MD_FILE=$(NAME).md

SUMMARY_NAME=$(NAME)-summary
SUMMARY_FILE=$(SUMMARY_NAME).md

BIB_FILE=$(NAME).bib

tex:
	pandoc -s \
		-F pandoc-crossref  \
		--natbib ass1a-tex.yaml \
		--metadata-file ass1a-tex.yaml \
		--csl=$(STYLE) \
		--template=$(TEX_TMPL) \
		--bibliography=ass1a.bib \
	 	-f markdown \
		-t latex+raw_tex+tex_math_dollars+citations \
		-o ass1a.tex \
		ass1a.md
	
	#xelatex ass1a.tex
	#bibtex ass1a
	#xelatex ass1a.tex
	#xelatex ass1a.tex


pdf:
	pandoc -s \
		--number-section \
		--filter pandoc-crossref \
		--filter pandoc-citeproc \
		--bibliography=ass1a.bib \
		--csl=$(STYLE) \
		--metadata=link-citations \
		--metadata=reference-section-title:References \
		--pdf-engine=xelatex \
		--template=$(TEX_TMPL) \
	 	-f markdown \
		-o $(NAME).pdf $(NAME).md
	# \
	--number-section \
	--template=$(TEX_TMPL) \
		--filter pandoc-citeproc \

pdf-summary:
	pandoc -s \
		--pdf-engine=xelatex \
		--template=$(TEX_TMPL) \
	 	-f markdown \
		-o $(SUMMARY_NAME).pdf $(SUMMARY_FILE)

html:
	pandoc -s -F pandoc-citeproc --bibliography=$(NAME).bib --csl=$(STYLE) -N \
		--metadata=link-citations \
		--metadata=reference-section-title:References \
		--css $(STYLE_DIR)/aut.css \
		-f markdown -t html -o $(NAME).html $(NAME).md

docx:
	pandoc -s -F pandoc-citeproc --bibliography=$(NAME).bib --csl=$(STYLE) -N \
	 	--reference-doc=$(DOC_STYLE) \
		--metadata=link-citations \
		--metadata=reference-section-title:References \
	 	-f markdown -t docx -o $(NAME).docx $(NAME).md

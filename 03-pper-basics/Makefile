PDF_DIR=target

LATEX_ARGS=--interaction=nonstopmode -shell-escape -file-line-error -output-directory $(PDF_DIR) -file-line-error

LATEX=pdflatex

SRCS = $(wildcard *.tex)
PDFS = $(patsubst %.tex,$(PDF_DIR)/%.pdf,$(SRCS))

JUNK =  *.toc *.aux *.pdf *.ps *.eps *.log *.lof *.bbl *.blg *.dvi *.log *.out
JUNK_PARAMS = $(foreach mask,$(JUNK),-name "$(mask)" -or )

.PHONY: all clean pdf

all: pdf $(PDFS)

pdf: $(PDFS)

$(PDF_DIR)/%.pdf: %.tex
	@echo ""
	@echo "== Compiling $*..."
	@echo ""
	mkdir -p $(PDF_DIR)
	$(LATEX) $(LATEX_ARGS) $*
	$(LATEX) $(LATEX_ARGS) $*

clean:
	find . \( $(JUNK_PARAMS) -false \) -delete
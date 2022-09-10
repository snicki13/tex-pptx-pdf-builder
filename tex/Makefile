# Taken from https://blog.martisak.se/2020/05/11/gitlab-ci-latex-pipeline/

SOURCES=Beispiel.tex
PDF_OBJECTS=$(SOURCES:.tex=.pdf)

LATEXMK=latexmk
LATEXMK_OPTIONS=-bibtex -pdf -xelatex

DOCKER=docker
DOCKER_COMMAND=run --rm -w /data/ --env LATEXMK_OPTIONS_EXTRA=$(LATEXMK_OPTIONS_EXTRA)
DOCKER_MOUNT=-v`pwd`:/data

pdf: $(PDF_OBJECTS)

%.pdf: %.tex
	@echo Input file: $<
	$(LATEXMK) $(LATEXMK_OPTIONS_EXTRA) $(LATEXMK_OPTIONS) $<

clean:
	-$(LATEXMK) -bibtex -C main
	-make -C figures clean

local:
	$(DOCKER) $(DOCKER_COMMAND) $(DOCKER_MOUNT) texlive/texlive \
		make pdf

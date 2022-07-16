# Taken from https://blog.martisak.se/2020/05/11/gitlab-ci-latex-pipeline/

SOURCES=Beispiel.tex
PDF_OBJECTS=$(SOURCES:.tex=.pdf)

LATEXMK=latexmk
LATEXMK_OPTIONS=-bibtex -pdf -pdflatex="pdflatex -interaction=nonstopmode"

DOCKER=docker
DOCKER_COMMAND=run --rm -w /data/ --env LATEXMK_OPTIONS_EXTRA=$(LATEXMK_OPTIONS_EXTRA)
DOCKER_MOUNT=-v`pwd`:/data

all: render

pdf: $(PDF_OBJECTS)

%.pdf: %.tex
	@echo Input file: $<
	$(LATEXMK) $(LATEXMK_OPTIONS_EXTRA) $(LATEXMK_OPTIONS) $<

clean:
	-$(LATEXMK) -bibtex -C main
	-make -C figures clean

dist-clean: clean
	-rm $(FILENAME).tar.gz

render:
	$(DOCKER) $(DOCKER_COMMAND) $(DOCKER_MOUNT) blang/latex:ctanfull \
		make pdf

check:

	@- $(foreach FILE, $(PDF_OBJECTS), \
		test -e $(FILE) ; \
	)

	rspec spec/pdf_spec.rb

figures:
	$(DOCKER) $(DOCKER_COMMAND) $(DOCKER_MOUNT) python:3.8 \
		make -C /data/figures

debug:
	$(DOCKER) $(DOCKER_COMMAND) -it $(DOCKER_MOUNT) blang/latex:ctanfull \
		bash

check_docker:
	$(DOCKER) $(DOCKER_COMMAND) -it $(DOCKER_MOUNT) ruby:2.7.1 \
		bundle update --bundler; make check

SOURCES=Lorem-Ipsum.pptx
PDF_OBJECTS=$(SOURCES:.pptx=.pdf)

pptx: $(PDF_OBJECTS)

%.pdf: %.pptx
	@echo Input file: $<
	soffice --headless --convert-to pdf $<

staple: 
	stapler cat Lorem-Ipsum.pdf 1 "Lorem-Ipsum-1.pdf"
	stapler cat Lorem-Ipsum.pdf 2 "Lorem-Ipsum-2.pdf"

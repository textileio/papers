BUILDDIR=build
FILENAME=index

all: pdf

pdf:
	mkdir -p $(BUILDDIR)
	pandoc $(FILENAME).md metadata.yaml \
	--standalone \
	--filter pandoc-crossref \
	--citeproc \
	--from=markdown+tex_math_single_backslash+tex_math_dollars+raw_tex \
	--template=template.latex \
	--to=pdf \
	--output=$(BUILDDIR)/$(FILENAME).pdf

clean:
	rm build/*

.PHONY: all clean pdf
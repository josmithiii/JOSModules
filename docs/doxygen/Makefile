SHELL := /bin/bash

MDIR=../../modules
BDIR=build
DDIR=doc

SOURCE_FILES := $(shell find $(MDIR) -type f -name "jos_*.h" -or -name "jos_*.dox" | sed 's/ /\\ /g')

.PHONY: clean

o: $(DDIR)/index.html
	open $<

$(DDIR)/index.html: $(BDIR)/jos_modules.dox Doxyfile
	/bin/cp jos_modules.dox $(BDIR)
	doxygen

$(BDIR)/jos_modules.dox: process_source_files.py $(SOURCE_FILES)
	echo SOURCE_FILES from $(MDIR) = $(SOURCE_FILES) > /dev/null
	python $< $(MDIR) $(BDIR)

i install: $(DDIR)/index.html
	rsync -auv $(DDIR)/ ccrma-gate.stanford.edu:~jos/web/jos_modules

clean:
	rm -rf $(BDIR) $(DDIR)

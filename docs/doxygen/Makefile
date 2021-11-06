SHELL := /bin/bash

MDIR=../../modules
BDIR=build
DDIR=doc

#DOXYGEN := doxygen jos_modules.config
#DOXYGEN := doxygen Doxyfile
DOXYGEN := doxygen
MAINPAGE = jos_modules_mainpage.dox
# fails: MAINPAGE = jos_modules.md

SOURCE_FILES := $(shell find $(MDIR) -type f \
	-name "jos_*.h" -or -name "jos_*.dox" \
	-name "juce_*.h" -or -name "juce_*.dox" \
	| sed 's/ /\\ /g')

.PHONY: clean

co:
	make clean
	make $(DDIR)/index.html
	open $(DDIR)/index.html

$(DDIR)/index.html: $(BDIR)/jos_modules.dox Doxyfile
	/bin/cp $(MAINPAGE) $(BDIR)
	$(DOXYGEN)

$(BDIR)/jos_modules.dox: process_source_files.py $(SOURCE_FILES)
	python $< $(MDIR) $(BDIR)

# Seems to not include juce_* !?
#	echo SOURCE_FILES from $(MDIR) = $(SOURCE_FILES) > /dev/null

i install: $(DDIR)/index.html
	rsync -auv $(DDIR)/ ccrma-gate.stanford.edu:~jos/web/jos_modules

clean:
	rm -rf $(BDIR) $(DDIR)

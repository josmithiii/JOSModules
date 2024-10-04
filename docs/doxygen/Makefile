SHELL := /bin/bash

MDIR=../../modules
BDIR=build
DDIR=doc

#DOXYGEN := doxygen josm_modules.config
#DOXYGEN := doxygen Doxyfile
#DOXYGEN := doxygen -u
DOXYGEN := doxygen
MAINPAGE = josm_modules_mainpage.dox
# fails: MAINPAGE = josm_modules.md
# MOVED TO ../../Archive

SOURCE_FILES := $(shell find $(MDIR) -type f -name "josm_*.h" -or -name "josm_*.dox" | sed 's/ /\\ /g')
#SOURCE_FILES := $(shell find $(MDIR) -type f -name "josm_*.h" -or -name "josm_*.dox" -name "juce_*.h" -or -name "juce_*.dox" -or -name "foleys_*.dox" | sed 's/ /\\ /g')

.PHONY: clean

o: $(DDIR)/index.html
	open $<

co:
	make clean
	make $(DDIR)/index.html
	open $(DDIR)/index.html

$(DDIR)/index.html: $(BDIR)/josm_modules.dox Doxyfile
	/bin/cp $(MAINPAGE) $(BDIR)
	$(DOXYGEN)

$(BDIR)/josm_modules.dox: process_source_files.py $(SOURCE_FILES)
	echo SOURCE_FILES from $(MDIR) = $(SOURCE_FILES) > /dev/null
	python $< $(MDIR) $(BDIR)

# Seems to not include juce_* !?
#	echo SOURCE_FILES from $(MDIR) = $(SOURCE_FILES) > /dev/null

i install: $(DDIR)/index.html
	rsync -auv $(DDIR)/ ccrma-gate.stanford.edu:~jos/web/josm_modules

clean:
	rm -rf $(BDIR) $(DDIR)

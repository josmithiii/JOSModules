all:
	open Reverb.jucer

cmake:
	echo "Assuming FRUT used"
	/bin/rm -rf build
	mkdir build && cd build/ && cmake .. -GXcode && cmake --build . --parallel

clean:
	/bin/rm -rf Builds/ JuceLibraryCode/

all:
	open Reverb.jucer

cmake:
	echo "Assuming FRUT used to set up ../CMakeLists.txt"
	/bin/rm -rf build
	mkdir build && cd build/ && cmake .. -GXcode && cmake --build . --parallel

clean:
	/bin/rm -rf Builds/ JuceLibraryCode/

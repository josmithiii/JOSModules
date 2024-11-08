# Faust Source

This directory can be used to regenerate the Faust-derived C++ from Faust source.
However, the resulting C++ is tracked in git, so this directory does not normally participate in any builds.
The plan is to run make after installing a new Faust release from time to time.
The Makefile produces fresh header files in ./faustheadersdir/.
These are included in-place where needed, such as in ../effects/jos_freeverb.cpp:12 .


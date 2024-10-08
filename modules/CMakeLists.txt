# For CMake builds, say
# set(JOSM_MODULES_DIR "${CMAKE_CURRENT_LIST_DIR}/path/to/JOSModules/modules")
# add_subdirectory(${JOSM_MODULES_DIR} josm_modules)

juce_add_modules(
  josm_faust
)

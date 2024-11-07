# For CMake builds, say
# set(JOSM_MODULES_DIR "${CMAKE_CURRENT_LIST_DIR}/path/to/JOSModules/modules")
# add_subdirectory(${JOS_MODULES_DIR} jos_modules)

juce_add_modules(jos_faust)

target_compile_options(jos_faust
    INTERFACE
    $<TARGET_PROPERTY:jos_warning_flags,INTERFACE_COMPILE_OPTIONS>
  )

find_package(SWIG)

if(NOT SWIG_FOUND)
    return()
endif()

include(${SWIG_USE_FILE})

set(CMAKE_SWIG_FLAGS "-DSWIG_CSHARP")
add_definitions(-Wno-cast-qual -Wno-shadow -Wno-maybe-uninitialized)
set_source_files_properties(../../OgreMain/include/Ogre.i PROPERTIES CPLUSPLUS ON)
swig_add_module(Ogre csharp ../../OgreMain/include/Ogre.i)
SWIG_LINK_LIBRARIES(Ogre OgreMain)
install(TARGETS ${SWIG_MODULE_Ogre_REAL_NAME} LIBRARY DESTINATION lib/)

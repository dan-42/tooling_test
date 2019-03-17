cmake_minimum_required( VERSION 3.14 )

project( TheProject   VERSION 1.0.0  DESCRIPTION "Example project for CMake (using CMake 3.14 or newer)." )

##
## Settings
##
## -fPIC
set( CMAKE_POSITION_INDEPENDENT_CODE ON ) 

## Copy all executables into the same output folder
## This works but is not best practice?
#set (CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR})
#set (CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR})


##
## Inlcude libs
##
add_subdirectory(libs)

##
## Inlcude libs
##
add_subdirectory(app)


cmake_minimum_required( VERSION 3.14)

include(GenerateExportHeader)

project( lib1  VERSION 1.0.0  DESCRIPTION "The lib1" )

##
## Create Target as shared lib
##
#ADD_LIBRARY(lib1 SHARED )
ADD_LIBRARY(lib1 STATIC )

## 
## Required include search-paths and constexpr support.
##
target_include_directories(
	lib1
    PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}/src" 
	PUBLIC "${CMAKE_CURRENT_BINARY_DIR}"
)

##
## Generate Export Header 
##
GENERATE_EXPORT_HEADER(
	lib1           
    BASE_NAME lib1
    EXPORT_MACRO_NAME LIB1_EXPORTS
    EXPORT_FILE_NAME lib1_exports.hpp
    STATIC_DEFINE SHARED_EXPORTS_BUILT_AS_STATIC
)

##
##
##
target_sources( lib1
	PRIVATE	src/lib1.cpp 
	PUBLIC	src/lib1.hpp 
		    ${CMAKE_CURRENT_BINARY_DIR}/lib1_exports.hpp
)		

##
## Compiler requirements
##
target_compile_features( 
	lib1
    PUBLIC cxx_constexpr 
)

##
## REQUIREMENTS
##
#target_link_libraries( lib1 PUBLIC Boost::outcome )

##
## Create ALIAS targets.
##
add_library( libs::lib1 ALIAS lib1 )
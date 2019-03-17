cmake_minimum_required( VERSION 3.14 )

project( app   VERSION 1.0.0  DESCRIPTION "Example project for CMake (using CMake 3.14 or newer)." )



##
## Executable
##
add_executable( app )

target_sources( 
	app 
	PRIVATE "src/main.cpp" 
)

##
##
##
target_link_libraries( 
	app
    PRIVATE libs::lib1
)

##
##
##
#install(TARGETS mylib
#  ARCHIVE
#  DESTINATION lib
#  COMPONENT libraries)
install(TARGETS app
  RUNTIME
  DESTINATION bin
  COMPONENT applications)
#install(FILES mylib.h
#  DESTINATION include
#  COMPONENT headers)

set(CPACK_GENERATOR WIX)
set(CPACK_COMPONENTS_ALL applications)
set(CPACK_PACKAGE_NAME "MyApp")
set(CPACK_PACKAGE_VENDOR "Dan")
set(CPACK_PACKAGE_DESCRIPTION_SUMMARY "MyApp - CPack test")
set(CPACK_PACKAGE_VERSION "1.0.0")
set(CPACK_PACKAGE_VERSION_MAJOR "1")
set(CPACK_PACKAGE_VERSION_MINOR "0")
set(CPACK_PACKAGE_VERSION_PATCH "0")
set(CPACK_PACKAGE_INSTALL_DIRECTORY "Dan MyApp")

# This must always be last!
include(CPack)


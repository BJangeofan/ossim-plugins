SET(BUILD_OSSIM_FRAMEWORKS "OFF")
SET(OSSIM_PLUGIN_LINK_TYPE "SHARED")

SET( CMAKE_CXX_FLAGS  "${CMAKE_CXX_FLAGS} -std=c++11" )

# Add our include and library...
find_package(ossim)
if(OSSIM_FOUND)
   include_directories( ${OSSIM_INCLUDE_DIR} )
   set( requiredLibs ${requiredLibs} ${OSSIM_LIBRARIES} )
else(OSSIM_FOUND)
   message(FATAL_ERROR "Could not find ossim")
endif(OSSIM_FOUND)
INCLUDE_DIRECTORIES(${CMAKE_CURRENT_SOURCE_DIR})

find_package(PDAL)
if(PDAL_FOUND)
   include_directories( ${PDAL_INCLUDE_DIR} )
   set(requiredLibs ${requiredLibs} ${PDAL_LIBRARIES} )
else(PDAL_FOUND)
   message(FATAL_ERROR "Could not find ossim")
endif(PDAL_FOUND)

INCLUDE_DIRECTORIES(${CMAKE_CURRENT_SOURCE_DIR})

add_subdirectory( src )

#IF(BUILD_OSSIM_TESTS)
#   add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/test ${CMAKE_CURRENT_BINARY_DIR}/test)
#ENDIF()


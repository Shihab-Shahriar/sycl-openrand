if(WIN32)
        set(CMAKE_CXX_COMPILER "icx-cl")
        set(CMAKE_C_COMPILER "icx-cl")
else()
        set(CMAKE_CXX_COMPILER "icpx")
endif()
set(CMAKE_CXX_STANDARD 17)
if(NOT DEFINED ${CMAKE_BUILD_TYPE})
	set(CMAKE_BUILD_TYPE "RELEASE")
endif()
if( CMAKE_BUILD_TYPE STREQUAL "DEBUG" )
	set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -g -fsycl")
endif()
cmake_minimum_required (VERSION 3.18)
project (NBODY)
add_subdirectory (src)



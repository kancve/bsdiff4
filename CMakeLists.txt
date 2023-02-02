cmake_minimum_required(VERSION 3.2.0 FATAL_ERROR)

project(BSDiff4)

# options
option(BSDIFF4_WITH_BSDIFF "Build bsdiff shell." ON)
option(BSDIFF4_WITH_BSPATCH "Build bspatch shell." ON)

# default build type
if (NOT CMAKE_BUILD_TYPE)
    set(CMAKE_BUILD_TYPE "MinSizeRel" CACHE STRING
        "Choose the type of build, options are: Debug Release RelWithDebInfo MinSizeRel." FORCE)
endif()

# install configure
set (CMAKE_INSTALL_PREFIX ${CMAKE_BINARY_DIR}/dist)

add_definitions(-D_FILE_OFFSET_BITS=64)
include_directories(${CMAKE_SOURCE_DIR}/bzip2)
file (GLOB_RECURSE SOURCES_BZIP2 "${CMAKE_CURRENT_SOURCE_DIR}/bzip2/*")

# bsdiff
if (BSDIFF4_WITH_BSDIFF)
    add_executable(bsdiff ${SOURCES_BZIP2} bsdiff.c)
    install(TARGETS bsdiff DESTINATION bin)
endif()

# bspatch
if (BSDIFF4_WITH_BSPATCH)
    add_executable(bspatch ${SOURCES_BZIP2} bspatch.c)
    install(TARGETS bspatch DESTINATION bin)
endif()
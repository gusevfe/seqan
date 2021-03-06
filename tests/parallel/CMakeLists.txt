# ===========================================================================
#                  SeqAn - The Library for Sequence Analysis
# ===========================================================================
# File: /tests/parallel/CMakeLists.txt
#
# CMakeLists.txt file for the parallel module tests.
# ===========================================================================

cmake_minimum_required (VERSION 2.8.2)
project (seqan_tests_parallel)
message (STATUS "Configuring tests/parallel")

# ----------------------------------------------------------------------------
# Dependencies
# ----------------------------------------------------------------------------

# Search SeqAn and select dependencies.
set (SEQAN_FIND_DEPENDENCIES OpenMP)
find_package (CXX11)
find_package (SeqAn REQUIRED)

# ----------------------------------------------------------------------------
# Build Setup
# ----------------------------------------------------------------------------

# Add include directories.
include_directories (${SEQAN_INCLUDE_DIRS})

# Add definitions set by find_package (SeqAn).
add_definitions (${SEQAN_DEFINITIONS})

# Add CXX flags found by find_package (SeqAn).
set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${SEQAN_CXX_FLAGS} ${CXX11_CXX_FLAGS}")
#set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${SEQAN_CXX_FLAGS}")

# Update the list of file names below if you add source files to your test.
add_executable (test_parallel
               test_parallel.cpp
               test_parallel_atomic_misc.h
               test_parallel_atomic_primitives.h
               test_parallel_splitting.h
               test_parallel_queue.h)

# Add dependencies found by find_package (SeqAn).
target_link_libraries (test_parallel ${SEQAN_LIBRARIES})

# ----------------------------------------------------------------------------
# Register with CTest
# ----------------------------------------------------------------------------

add_test (NAME test_test_parallel COMMAND $<TARGET_FILE:test_parallel>)

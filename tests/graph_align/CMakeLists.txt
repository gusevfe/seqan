# ===========================================================================
#                  SeqAn - The Library for Sequence Analysis
# ===========================================================================
# File: /tests/graph_align/CMakeLists.txt
#
# CMakeLists.txt file for the graph_align module tests.
# ===========================================================================

cmake_minimum_required (VERSION 2.8.2)
project (seqan_tests_graph_align)
message (STATUS "Configuring tests/graph_align")

# ----------------------------------------------------------------------------
# Dependencies
# ----------------------------------------------------------------------------

# Search SeqAn and select dependencies.
set (SEQAN_FIND_DEPENDENCIES NONE)
find_package (SeqAn REQUIRED)

# ----------------------------------------------------------------------------
# Build Setup
# ----------------------------------------------------------------------------

# Add include directories.
include_directories (${SEQAN_INCLUDE_DIRS})

# Add definitions set by find_package (SeqAn).
add_definitions (${SEQAN_DEFINITIONS})

# Update the list of file names below if you add source files to your test.
add_executable (test_graph_align
               test_graph_align.cpp
               test_graph_impl_align.h
               test_graph_match_refinement.h)

# Add dependencies found by find_package (SeqAn).
target_link_libraries (test_graph_align ${SEQAN_LIBRARIES})

# Add CXX flags found by find_package (SeqAn).
set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${SEQAN_CXX_FLAGS}")

# ----------------------------------------------------------------------------
# Register with CTest
# ----------------------------------------------------------------------------

add_test (NAME test_test_graph_align COMMAND $<TARGET_FILE:test_graph_align>)

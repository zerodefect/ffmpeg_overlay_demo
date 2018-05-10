cmake_minimum_required(VERSION 3.4)

project(VideoPipeline)

message(STATUS "Project:    ${PROJECT_NAME}")
message(STATUS "Platform:   ${CMAKE_SYSTEM_NAME} (${CMAKE_SYSTEM})")
message(STATUS "Build Type: ${CMAKE_BUILD_TYPE}")


set(CMAKE_CXX_STANDARD 11)

# Set the location where our binaries will be stored.
# WARN/TODO: Not quite right, because .lib or .a files should
#            not go in the bin folder!
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

# Adds 'd' onto artifacts - does NOT apply to executables.
# For executables, this needs to be done an exec-by-exec
# basis.
set(CMAKE_DEBUG_POSTFIX "d")


add_executable(overlay_test main.cpp)


# Define the libraries this project depends upon
target_link_libraries(overlay_test
    avfilter
    avformat
    avcodec
    avutil)
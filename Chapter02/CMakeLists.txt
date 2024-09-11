cmake_minimum_required(VERSION 3.15)

# Project name and version
project(SubstringSort VERSION 1.0 LANGUAGES CXX)

# Set C++ standard to C++20
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED True)
set(CMAKE_CXX_EXTENSIONS OFF)  # Disable compiler-specific extensions

# Add extra warning flags for Clang or GNU compilers
if(CMAKE_CXX_COMPILER_ID MATCHES "Clang" OR CMAKE_CXX_COMPILER_ID STREQUAL "GNU")
    # add_compile_options(
        # -Wall -Wextra -Wpedantic -Wshadow -Wconversion -Wnon-virtual-dtor -Wold-style-cast
    # )
endif()

# Google Benchmark
# Download and build Google Benchmark if not available
include(FetchContent)

FetchContent_Declare(
    benchmark
    GIT_REPOSITORY https://github.com/google/benchmark.git
    GIT_TAG v1.7.1  # Or the version you want
)

# Enable downloading of dependencies (including Google Test)
set(BENCHMARK_DOWNLOAD_DEPENDENCIES ON CACHE BOOL "Download benchmark dependencies including Google Test")

FetchContent_MakeAvailable(benchmark)

# Define sources
set(SOURCES
    01_substring_sort.C
    01_substring_sort_a.C
)

# Link benchmark and pthread, atomic, rt, m libraries
find_package(Threads REQUIRED)

# Add the executable
add_executable(01_substring_sort ${SOURCES})

# Link the libraries
if(APPLE)
    target_link_libraries(01_substring_sort benchmark::benchmark Threads::Threads)
else()
    target_link_libraries(01_substring_sort benchmark::benchmark Threads::Threads pthread atomic rt m)
endif()

# Optionally enable testing (if you have tests later on)
enable_testing()
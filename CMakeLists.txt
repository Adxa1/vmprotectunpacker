cmake_minimum_required(VERSION 3.16)
project(VMProtectUnpacker LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Add include folder globally
include_directories(${CMAKE_SOURCE_DIR}/include)

# Collect sources
file(GLOB_RECURSE SOURCES "src/*.cpp")

if(NOT SOURCES)
    message(FATAL_ERROR "No source files found!")
endif()

# Create executable
add_executable(VMProtectUnpacker ${SOURCES})

# Link capstone
target_link_libraries(VMProtectUnpacker capstone)

cmake_minimum_required(VERSION 3.16)
project(VMProtectUnpacker LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Project includes
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/include)

# Find source files
file(GLOB_RECURSE SOURCES "src/*.cpp")
file(GLOB_RECURSE HEADERS "include/**/*.h")

message(STATUS "Sources found: ${SOURCES}")

if(NOT SOURCES)
    message(FATAL_ERROR "No source files found!")
endif()

# Add executable
add_executable(VMProtectUnpacker ${SOURCES} ${HEADERS})

# Include directories
target_include_directories(VMProtectUnpacker PRIVATE
    ${CMAKE_CURRENT_SOURCE_DIR}/include
)

# Find and link Capstone (from vcpkg or system)
find_package(capstone CONFIG REQUIRED)

target_link_libraries(VMProtectUnpacker
    capstone
)

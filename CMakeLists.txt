cmake_minimum_required(VERSION 3.16)
project(VMProtectUnpacker LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Collect source files
file(GLOB_RECURSE SOURCES "src/*.cpp")

if(NOT SOURCES)
    message(FATAL_ERROR "No source files found!")
endif()

add_executable(VMProtectUnpacker ${SOURCES})

# Important: include project root so includes like
# #include "vmprotectunpacker/PEParser.h" work
target_include_directories(VMProtectUnpacker PRIVATE
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${CMAKE_CURRENT_SOURCE_DIR}/include
)

# Link capstone
target_link_libraries(VMProtectUnpacker capstone)

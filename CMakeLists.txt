cmake_minimum_required(VERSION 3.10)
project(lumen)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Project submodules
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/src)

add_subdirectory("external")

# Add source files
set(SOURCES src/main.cpp)

# Compile the executable
add_executable(${PROJECT_NAME} ${SOURCES})

# Link libraries
target_link_libraries(${PROJECT_NAME} PRIVATE gui)

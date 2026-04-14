cmake_minimum_required(VERSION 3.28)
project(HelixUtil VERSION 0.1.0)

if (MSVC)
    set(CMAKE_MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>DLL")
endif ()

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR})
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR})
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR})

file(GLOB HELIX_UTIL_INCLUDE HelixUtil/include/HelixEngine/Util/*.hpp)
file(GLOB HELIX_UTIL_SOURCES HelixUtil/src/*.cpp)

add_library(${PROJECT_NAME} STATIC ${HELIX_UTIL_INCLUDE} ${HELIX_UTIL_SOURCES})
target_include_directories(${PROJECT_NAME} PUBLIC HelixUtil/include HelixUtil/extern/fast_io/include HelixUtil/extern/ktm/include)
set_target_properties(${PROJECT_NAME} PROPERTIES LINKER_LANGUAGE CXX)

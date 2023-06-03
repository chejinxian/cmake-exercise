# Required Cmake version
cmake_minimum_required(VERSION 3.10 FATAL_ERROR)

# Project name and language
project(CHAPTER_1_EXAMPLE_7 LANGUAGES C CXX)

# Set defult build type
if(NOT CMAKE_BUILD_TYPE)
    set(CMAKE_BUILD_TYPE Release CACHE STRINGS "Build type" FORCE)
endif()
message(STATUS "Build type is: ${CMAKE_BUILD_TYPE}")

message(STATUS "C flags, Debug configuration: ${CMAKE_C_FLAGS_DEBUG}")
message(STATUS "C flags, Release configuration: ${CMAKE_C_FLAGS_RELEASE}")
message(STATUS "C flags, Release configuration with Debug info: ${CMAKE_C_FLAGS_RELWITHDEBINFO}")
message(STATUS "C flags, minimal Release configuration: ${CMAKE_C_FLAGS_MINSIZEREL}")
message(STATUS "C++ flags, Debug configuration: ${CMAKE_CXX_FLAGS_DEBUG}")
message(STATUS "C++ flags, Release configuration: ${CMAKE_CXX_FLAGS_RELEASE}")
message(STATUS "C++ flags, Release configuration with Debug info: ${CMAKE_CXX_FLAGS_RELWITHDEBINFO}")
message(STATUS "C++ flags, minimal Release configuration: ${CMAKE_CXX_FLAGS_MINSIZEREL}")
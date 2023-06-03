# Required Cmake version
cmake_minimum_required(VERSION 3.10 FATAL_ERROR)

# Project name and language
project(CHAPTER_1_EXAMPLE_8 LANGUAGES C CXX)

message("C++ compiler flags: ${CMAKE_CXX_FLAGS}")

list(APPEND flags "-fPIC" "-Wall")
if(NOT WIN32)
  list(APPEND flags "-Wextra" "-Wpedantic")
endif()

add_library(geometry
  STATIC
    geometry_circle.cpp
    geometry_circle.hpp
    geometry_polygon.cpp
    geometry_polygon.hpp
    geometry_rhombus.cpp
    geometry_rhombus.hpp
    geometry_square.cpp
    geometry_square.hpp
  )

target_compile_options(geometry
  PRIVATE
    ${flags}
  )

add_executable(compute-areas compute-areas.cpp)

target_compile_options(compute-areas
  PRIVATE
    "-fPIC"
  )

target_link_libraries(compute-areas geometry)

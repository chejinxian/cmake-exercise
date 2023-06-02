# Required CMake version
cmake_minimum_required(VERSION 3.10 FATAL_ERROR)

# Project name
project(CHAPTER_1_EXAMPLE_1 LANGUAGES CXX)

# Specify the generated executable
add_executable(hello-world hello-world.cpp)

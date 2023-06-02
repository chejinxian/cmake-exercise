# # Required CMake version
# cmake_minimum_required(VERSION 3.10 FATAL_ERROR)

# # Project name
# project(CHAPTER_1_EXAMPLE_3 LANGUAGES CXX)

# # Specify the generated executable
# add_executable(hello-world hello-world.cpp)

# # Add a library
# add_library(message
#     STATIC
#         message.h
#         message.cpp
# )

# # Link to my libray
# target_link_libraries(hello-world message)

# Required CMake version
cmake_minimum_required(VERSION 3.10 FATAL_ERROR)

# Project name
project(CHAPTER_1_EXAMPLE_3 LANGUAGES CXX)

# Specify the generated executable
add_executable(hello-world hello-world.cpp)

# Add a obj library
add_library(message-objs
    OBJECT
        message.h
        message.cpp
)

# this is only needed for old compilers
set_target_properties(message-objs
    PROPERTIES
        POSITION_INDEPENDENT_CODE 1
)

# Add a shared library
add_library(message-shared
    SHARED
        $<TARGET_OBJECTS:message-objs>
)

set_target_properties(message-shared
    PROPERTIES
        OUTPUT_NAME "message"
)

# Add a static library
add_library(message-static
    STATIC
        $<TARGET_OBJECTS:message-objs>
)

set_target_properties(message-static
    PROPERTIES
        OUTPUT_NAME "message"
)

# Link to my libray
target_link_libraries(hello-world message-shared)
# Required CMake version
cmake_minimum_required(VERSION 3.10 FATAL_ERROR)

# Project name
project(CHAPTER_1_EXAMPLE_4 LANGUAGES CXX)

# Introduce some variales
set(USE_LIBRARY OFF) #assinment
message(STATUS "Compile sources into a library? ${USE_LIBRARY}") #output hint information
set(BUILD_SHARED_LIBS OFF)
list(APPEND _SOURCES message.h message.cpp) #add a local variable

# Contorl compilation based on USE_LIBRARY
if(USE_LIBRARY)
    # Add a library
    #since BUILD_SHARED_LIBS=OFF, we build a static library.
    add_library(message ${_SOURCES})
    add_executable(hello-world hello-world.cpp)
    target_link_libraries(hello-world message)

else()
    # Without library
    #compile all source files into executable
    add_executable(hello-world hello-world.cpp ${_SOURCES})
    
endif(USE_LIBRARY)

# else()和endif()中的()
# 其历史原因是，因为其能够指出指令的作用范围。例如，可以使用if(USE_LIBRARY)…else(USE_LIBRARY)…endif(USE_LIBIRAY)。
# 这个格式并不唯一，可以根据个人喜好来决定使用哪种格式。

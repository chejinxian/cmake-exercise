# # Required CMake version
# cmake_minimum_required(VERSION 3.10 FATAL_ERROR)

# # Project name
# project(CHAPTER_1_EXAMPLE_5 LANGUAGES CXX)

# # Introduce some variales

# #set(USE_LIBRARY OFF) #assinment
# option(USE_LIBRARY "Condition about compilling libraries" OFF)
# message(STATUS "Compile sources into a library? ${USE_LIBRARY}") #output hint information
# set(BUILD_SHARED_LIBS OFF)
# list(APPEND _SOURCES message.h message.cpp) #add a local variable

# # Contorl compilation based on USE_LIBRARY
# if(USE_LIBRARY)
#     # Add a library
#     #since BUILD_SHARED_LIBS=OFF, we build a static library.
#     add_library(message ${_SOURCES})
#     add_executable(hello-world hello-world.cpp)
#     target_link_libraries(hello-world message)

# else()
#     # Without library
#     #compile all source files into executable
#     add_executable(hello-world hello-world.cpp ${_SOURCES})
    
# endif(USE_LIBRARY)
# Required CMake version


cmake_minimum_required(VERSION 3.10 FATAL_ERROR)

# Project name
project(CHAPTER_1_EXAMPLE_5 LANGUAGES CXX)

# Introduce some variales

#set(USE_LIBRARY OFF) #assinment
option(USE_LIBRARY "Condition about compilling libraries" OFF)
message(STATUS "Compile sources into a library? ${USE_LIBRARY}") #output hint information
# set(BUILD_SHARED_LIBS OFF)

include(CMakeDependentOption)
cmake_dependent_option(MAKE_STATIC_LIBRARY "Compile sources into a static library" OFF "USE_LIBRARY" ON) #if USE_LIBRARY=ON, MAKE_STATIC_LIBRARY=OFF
cmake_dependent_option(MAKE_SHARED_LIBRARY "Compile sources into a static library" ON "USE_LIBRARY" ON) #and MAKE_SHARED_LIBRARY=ON
message(STATUS "MAKE_STATIC_LIBRARY=${MAKE_STATIC_LIBRARY}")
message(STATUS "MAKE_SHARED_LIBRARY=${MAKE_SHARED_LIBRARY}")


list(APPEND _SOURCES message.h message.cpp) #add a local variable

# Contorl compilation based on USE_LIBRARY
if(USE_LIBRARY)
    # # Add a library
    # #since BUILD_SHARED_LIBS=OFF, we build a static library.
    # add_library(message ${_SOURCES})
    # add_executable(hello-world hello-world.cpp)
    # target_link_libraries(hello-world message)

    message(STATUS "MAKE_STATIC_LIBRARY=${MAKE_STATIC_LIBRARY}")
    message(STATUS "MAKE_SHARED_LIBRARY=${MAKE_SHARED_LIBRARY}")

    if(MAKE_SHARED_LIBRARY)
        add_library(message SHARED ${_SOURCES})
        # add_executable(hello-world hello-world.cpp)
        # target_link_libraries(hello-world message)
    endif(MAKE_SHARED_LIBRARY)

    if(MAKE_STATIC_LIBRARY)
        add_library(message STATIC ${_SOURCES})
        # add_executable(hello-world hello-world.cpp)
        # target_link_libraries(hello-world message)
    endif(MAKE_STATIC_LIBRARY)

    add_executable(hello-world hello-world.cpp)
    target_link_libraries(hello-world message)

else()
    # Without library
    #compile all source files into executable
    add_executable(hello-world hello-world.cpp ${_SOURCES})
    
endif(USE_LIBRARY)

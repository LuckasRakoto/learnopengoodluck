cmake_minimum_required(VERSION 3.10)

# Project name and version
project(OpenGLProject VERSION 1.0)

set(CMAKE_C_COMPILER "gcc")
set(CMAKE_CXX_COMPILER "/usr/bin/g++")

# Set the C++ standard
set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD_REQUIRED True)

add_executable(${PROJECT_NAME} main.cpp)

# Specify paths for GLAD
set(GLAD_INCLUDE_PATH ${CMAKE_SOURCE_DIR}/libraries/glad/include)
set(GLAD_LIBRARY_PATH ${CMAKE_SOURCE_DIR}/libraries/glad/src/glad.c)

# Include GLAD
add_library(glad STATIC ${GLAD_LIBRARY_PATH})
target_include_directories(glad PUBLIC ${GLAD_INCLUDE_PATH})

# Include GLFW headers
target_include_directories(${PROJECT_NAME} PUBLIC /usr/local/include)

# Link GLFW static library
target_link_libraries(${PROJECT_NAME} /usr/local/lib/libglfw3.a)

# Link libraries
target_link_libraries(${PROJECT_NAME}
    glad
    "-framework Cocoa"
    "-framework OpenGL"
    "-framework IOKit"
)
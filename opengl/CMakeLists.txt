cmake_minimum_required( VERSION 3.14 )
include(ExternalProject)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

project(triangle-opengl)

add_compile_options("$<$<C_COMPILER_ID:MSVC>:/utf-8>")
add_compile_options("$<$<CXX_COMPILER_ID:MSVC>:/utf-8>")

add_executable(triangle-opengl
    main.cpp
)

find_package(glfw3 REQUIRED)
target_link_libraries(triangle-opengl PRIVATE glfw)

add_subdirectory(${CMAKE_SOURCE_DIR}/dependencies/glad)
target_link_libraries(triangle-opengl PRIVATE glad)

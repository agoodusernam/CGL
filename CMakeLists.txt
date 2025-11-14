cmake_minimum_required(VERSION 3.15)
project(CGL LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

find_package(glfw3 CONFIG REQUIRED)
find_package(OpenGL REQUIRED)

file(GLOB_RECURSE CGL_SOURCES
    "${PROJECT_SOURCE_DIR}/src/*.cpp"
)

file(GLOB_RECURSE CGL_HEADERS
    "${PROJECT_SOURCE_DIR}/include/*.hpp"
)

add_library(cgl STATIC ${CGL_SOURCES} ${CGL_HEADERS})


target_include_directories(cgl
    PUBLIC
        "${PROJECT_SOURCE_DIR}/include"
)


target_link_libraries(cgl
    PUBLIC
        glfw
        OpenGL::GL
)

set_target_properties(cgl PROPERTIES
    OUTPUT_NAME "cgl"
    POSITION_INDEPENDENT_CODE ON
)

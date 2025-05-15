cmake_minimum_required(VERSION 3.15)
project(app)

# statically link
set(BUILD_SHARED_LIBS OFF CACHE BOOL "")

set(SDLSHADERCROSS_DXC OFF CACHE BOOL "")
set(SDLSHADERCROSS_CLI OFF CACHE BOOL "")
set(SDLSHADERCROSS_VENDORED ON CACHE BOOL "")
set(SDLSHADERCROSS_SPIRVCROSS_SHARED OFF CACHE BOOL "")

set(SDL_TEST_LIBRARY OFF CACHE BOOL "")
set(SPIRV_SKIP_TESTS ON CACHE BOOL "")

# dependencies
add_subdirectory(external/SDL)
add_subdirectory(external/SDL_shadercross)

# build exectuable
add_executable(app main.cpp)
target_link_libraries(app PUBLIC
    SDL3::SDL3-static 
    SDL3_shadercross::SDL3_shadercross-static
)
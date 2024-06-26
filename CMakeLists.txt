cmake_minimum_required(VERSION 3.5.0)

include(FetchContent)
set(RAYLIB_VERSION 5.0)
FetchContent_Declare(
    raylib
    URL https://github.com/raysan5/raylib/archive/refs/tags/${RAYLIB_VERSION}.tar.gz
    FIND_PACKAGE_ARGS ${RAYLIB_VERSION}
)
set(BUILD_EXAMPLES OFF CACHE INTERNAL "")
set(OPENGL_VERSION "4.3")
FetchContent_MakeAvailable(raylib)

# Declare the projects here.
add_executable(NewtonFractal NewtonFractal/main.c)
add_executable(DenseInjection DenseInjection/main.c)
add_executable(TriangleNet TriangleNet/main.cpp TriangleNet/TriangleNet.cpp TriangleNet/TriangleNet.h)
add_executable(Unproject Unproject/main.cpp)
add_executable(PointOnPolygon PointOnPolygon/main.cpp)

target_link_libraries(NewtonFractal PRIVATE raylib)
target_link_libraries(DenseInjection PRIVATE raylib)
target_link_libraries(TriangleNet PRIVATE raylib)
target_link_libraries(Unproject PRIVATE raylib)
target_link_libraries(PointOnPolygon PRIVATE raylib)
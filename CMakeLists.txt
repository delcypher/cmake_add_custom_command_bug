project(foo)
cmake_minimum_required(VERSION 2.8.12)

include_directories(${CMAKE_SOURCE_DIR}/include)
add_subdirectory(lib)
add_subdirectory(test)

cmake_minimum_required(VERSION 3.8)


project(libplist VERSION 2.2.1)

set(CMAKE_C_STANDARD 99)
set(CMAKE_CXX_STANDARD 17)

message(STATUS "Operation System : ${CMAKE_SYSTEM}")
message(STATUS "CMAKE_INSTALL_PREFIX : ${CMAKE_INSTALL_PREFIX}")
message(STATUS "CMAKE_SOURCE_DIR : ${CMAKE_SOURCE_DIR}")


add_subdirectory(libcnary)
add_subdirectory(src)
add_subdirectory(tools)

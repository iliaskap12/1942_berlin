cmake_minimum_required(VERSION 3.17)
project(1942_berlin VERSION 1.0.0)

set(CMAKE_CXX_STANDARD 20)

find_package(sgg REQUIRED)

set(CMAKE_CURRENT_SOURCE_DIR src)
add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR})
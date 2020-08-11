cmake_minimum_required(VERSION 3.5)

project(CartilageSegmentation LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_WINDOWS_EXPORT_ALL_SYMBOLS 1)

add_executable(CartilageSegmentation main.cpp)

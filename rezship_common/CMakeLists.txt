cmake_minimum_required(VERSION 3.19)

project(rezship_common
        VERSION 0.1.0
        LANGUAGES CXX)

include(CTest)
enable_testing()

add_library(rezship_common main.cpp)

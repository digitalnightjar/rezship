cmake_minimum_required(VERSION 3.20)
project(rezship VERSION 0.1.0)

add_subdirectory(rezship_game)
add_subdirectory(rezship_editor)
add_subdirectory(rezship_common)

set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)

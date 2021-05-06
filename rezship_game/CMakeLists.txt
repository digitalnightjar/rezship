cmake_minimum_required(VERSION 3.19)

project(rezship_game
        VERSION 0.1.0
        LANGUAGES CXX)

include(CTest)
enable_testing()

list(APPEND CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/../cmake/sdl2)

# Find SDL2, SDL2_image and SDL2_gfx libraries
find_package(SDL2 REQUIRED)
find_package(SDL2_image REQUIRED)
#find_package(SDL2_gfx REQUIRED)
if(SDL2_FOUND)
    message("SDL2 Library:" ${SDL2_LIBRARIES})
    message("SDL2 Version:" ${SDL2_VERSION_STRING})
endif()

if(NOT SDL2MAIN_FOUND)
    message("Could not find SDL2main")
else()
    message("Found SDL2Main")
endif()

include_directories(${SDL2_INCLUDE_DIRS})
include_directories(${SDL2_IMAGE_DIRS})

add_executable(rezship_game main.cpp)

# Link SDL2::Main, SDL2::Image and SDL2::GFX to our project
#target_link_libraries(${PROJECT_NAME} SDL2::Main SDL2::Image)
target_link_libraries(rezship_game ${SDL2_LIBRARIES} SDL2::Main ${SDL2_IMAGE_LIBRARIES} SDL2::Image) 
#target_link_libraries(rezship_game "-framework Cocoa -framework OpenGL"${SDL2_LIBRARIES} ${SDL2_IMAGE_LIBRARIES})

set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)

# This is just an example on how to use cmake where a module is not in project dir

cmake_minimum_required(VERSION 3.28)
project(qualia CXX)

set(CMAKE_CXX_STANDARD 26)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)   # <-- clangd reads this

set(RAYLIB "/home/hel/Documents/Dev/raylib")

add_executable(qualia)
target_sources(qualia
  PRIVATE main.cpp
  PRIVATE FILE_SET cxx_modules TYPE CXX_MODULES
    BASE_DIRS ${CMAKE_CURRENT_SOURCE_DIR} 
    FILES 
)

target_link_libraries(qualia PRIVATE
  ${RAYLIB}/build/raylib/libraylib.a
  X11 GL m pthread dl rt
)

target_include_directories(qualia PRIVATE
  ${RAYLIB}/build/raylib/include
)


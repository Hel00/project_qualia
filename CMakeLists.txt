cmake_minimum_required(VERSION 3.28)
project(qualia CXX)

set(CMAKE_CXX_STANDARD 26)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

if(NOT TIGR_DIR)
  message(FATAL_ERROR "Pass -DTIGR_DIR=/path/to/tigr")
endif()

add_executable(qualia)
target_sources(qualia
  PRIVATE main.cpp
  PRIVATE FILE_SET cxx_modules TYPE CXX_MODULES
    BASE_DIRS ${CMAKE_CURRENT_SOURCE_DIR} 
    FILES 
)

target_link_libraries(qualia PRIVATE
  ${TIGR_DIR}/libtigr.a
  GLU
  GL
  X11
)

target_include_directories(qualia PRIVATE
  ${TIGR_DIR}
)


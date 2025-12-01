cmake_minimum_required(VERSION 3.30)
project(hello
  VERSION 1.0
  LANGUAGES C)

option(USE_CCACHE FALSE)

if (USE_CCACHE)
  find_program(CCACHE ccache)
  set(CMAKE_C_COMPILER_LAUNCHER ${CCACHE})
  set(CMAKE_CXX_COMPILER_LAUNCHER ${CCACHE})
endif ()

add_library(hello_static STATIC
  hello.c)

add_executable(hello
  main.c)

target_link_libraries(hello PUBLIC
  hello_static)

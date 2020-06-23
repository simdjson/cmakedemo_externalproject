cmake_minimum_required(VERSION 3.16)
cmake_policy(SET CMP0097 NEW)

project(simdjson_demo
  DESCRIPTION "simdjson demo"
  LANGUAGES CXX
)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)
set(CMAKE_MACOSX_RPATH OFF)
set(CMAKE_THREAD_PREFER_PTHREAD ON)
set(THREADS_PREFER_PTHREAD_FLAG ON)

set(PROJECT_VERSION_MAJOR 0)
set(PROJECT_VERSION_MINOR 0)
set(PROJECT_VERSION_PATCH 1)


include(ExternalProject)

list(APPEND CL_ARGS "-DSIMDJSON_JUST_LIBRARY=ON")
list(APPEND CL_ARGS "-DSIMDJSON_BUILD_STATIC=ON")

ExternalProject_Add(simdjson_repo
  GIT_REPOSITORY    https://github.com/simdjson/simdjson.git
  CMAKE_ARGS        ${CL_ARGS}
  GIT_TAG          02a8145b181a6a7a7534987554aef4c8d11b43ff
  GIT_SUBMODULES   ""
  GIT_SHALLOW         TRUE
)

add_library(simdjson STATIC IMPORTED)

ExternalProject_Get_Property(simdjson_repo binary_dir)
set_target_properties(simdjson PROPERTIES IMPORTED_LOCATION ${binary_dir}/src/libsimdjson.a)
ExternalProject_Get_Property(simdjson_repo source_dir)
include_directories(${source_dir}/include/)

add_subdirectory(src)

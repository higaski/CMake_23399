cmake_minimum_required(VERSION 3.19)
include(FetchContent)

project(CMake_23399 LANGUAGES CXX)

set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)

find_package(
  Qt5
  COMPONENTS Widgets
  REQUIRED)

add_executable(CMake_23399 src/main.cpp icons.qrc)

set(FETCHCONTENT_QUIET FALSE)
FetchContent_Declare(
  SDL
  GIT_REPOSITORY https://github.com/libsdl-org/SDL
  GIT_TAG release-2.0.20
  GIT_PROGRESS TRUE)
FetchContent_MakeAvailable(SDL)

target_link_libraries(CMake_23399 PRIVATE Qt5::Widgets SDL2-static)

cmake_minimum_required(VERSION 3.10)
project(googletest)

include_directories(${PROJECT_SOURCE_DIR}/googletest/include)
include_directories(${PROJECT_SOURCE_DIR}/googlemock/include)

add_subdirectory(googletest)
add_subdirectory(googlemock)

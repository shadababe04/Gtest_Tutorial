cmake_minimum_required(VERSION 3.10)
project(MyProject)

# Specify the C++ standard
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Add the include directory
include_directories(${PROJECT_SOURCE_DIR}/include)
include_directories(${PROJECT_SOURCE_DIR}/third_party/googletest/googletest/include)
include_directories(${PROJECT_SOURCE_DIR}/third_party/googletest/googlemock/include)

# Add source files
add_library(MyProjectLib src/math_op.cpp)
add_executable(MyProject src/main.cpp)

# Link the library to the executable
target_link_libraries(MyProject MyProjectLib)

# Add test files
add_executable(MyProjectTests test/math_test.cpp)
target_link_libraries(MyProjectTests gtest gmock gtest_main MyProjectLib)

# Add custom command to build and install Google Test if not installed
add_subdirectory(third_party/googletest)

enable_testing()
add_test(NAME MyProjectTests COMMAND MyProjectTests)

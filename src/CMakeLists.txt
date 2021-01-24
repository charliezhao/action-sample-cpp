cmake_minimum_required (VERSION 3.5.1)
project(BlaizeApp LANGUAGES CXX VERSION 0.0.0)

set(PROJECT_PATH $ENV{PWD}/../src)

set(CMAKE_SYSTEM_NAME Linux)
set(TARGET_ABI "linux-gnu")
set(CMAKE_CXX_COMPILER /usr/bin/g++)
set(CMAKE_CXX_FLAGS "-Wall -std=c++11 -fPIC")

set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/lib)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY $ENV{PWD}/bin)

include_directories(
    ./
)

ADD_EXECUTABLE(main main.cpp)

enable_testing()
add_test(test-1 ./bin/main)
set_tests_properties(test-1 PROPERTIES PASS_REGULAR_EXPRESSION "SUCCESS")

target_link_libraries(main)

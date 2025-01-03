cmake_minimum_required(VERSION 3.20)
project(test-mpdecimal "C" "CXX")

set(PROJECT_VERSION 0.0.1)

set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS}  ${SGX_COMMON_CFLAGS} -fPIC -Wno-attributes")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${CMAKE_C_FLAGS} -std=c++11")

message(STATUS "CMAKE_SOURCE_DIR = ${CMAKE_SOURCE_DIR}")

add_executable(${CMAKE_PROJECT_NAME}
    test.cpp
)

include_directories(
    mpdecimal-4.0.0/libmpdec
)

target_link_directories(${CMAKE_PROJECT_NAME} PRIVATE
    mpdecimal-4.0.0/libmpdec
)

target_link_libraries(${CMAKE_PROJECT_NAME}
    -lmpdec
)


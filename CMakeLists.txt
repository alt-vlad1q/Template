cmake_minimum_required(VERSION 3.13)
project(sandbox)

set(CMAKE_CXX_STANDART 14)
set(CMAKE_CXX_EXTENSIONS OFF)
set(CMAKE_CXX_STANDART_REQUIRED ON)

set(CMAKE_CXX_FLAGS_RELEASE  "-fPIC -O2 -Wl,-rpath=../lib -Wall -Werror=unused-result -Werror=return-type")
set(CMAKE_CXX_FLAGS_DEBUG    "${CMAKE_CXX_FLAGS_RELEASE} -g")
set(CMAKE_CXX_FLAGS          "${CMAKE_CXX_FLAGS_RELEASE}")

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY  ${PROJECT_SOURCE_DIR}/bin)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY  ${PROJECT_SOURCE_DIR}/lib)

add_executable(${PROJECT_NAME} main.cpp)

find_package(Boost REQUIRED)
target_link_libraries(${PROJECT_NAME} ${Boost_LIBRARIES})
target_include_directories(${PROJECT_NAME} PRIVATE ${Boost_INCLUDE_DIRS})

find_package(Qt5 REQUIRED COMPONENTS Core)
target_link_libraries(${PROJECT_NAME} Qt5::Core)

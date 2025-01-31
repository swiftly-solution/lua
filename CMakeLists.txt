cmake_minimum_required(VERSION 3.4)

project(SwiftlyLua)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

file(GLOB SOURCES "*.cpp")

add_library(lua STATIC ${SOURCES})

if(UNIX AND NOT APPLE)
    set(LINUX TRUE)
endif()

if(LINUX)
    set(CMAKE_CXX_FLAGS "-lm -ldl -lreadline -fPIC")
    add_definitions(-DLUA_USE_LINUX -DLUA_USE_READLINE)
endif()
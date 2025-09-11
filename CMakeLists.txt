cmake_minimum_required(VERSION 3.30)

project(DelHel)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -g")

add_library(${PROJECT_NAME} SHARED
        ${PROJECT_NAME}/CDelHel.cpp
        ${PROJECT_NAME}/flightplan.cpp
        ${PROJECT_NAME}/helpers.cpp
        ${PROJECT_NAME}/RadarScreen.cpp
        ${PROJECT_NAME}/route_entry.cpp
        ${PROJECT_NAME}/routing.cpp
)

target_compile_definitions(${PROJECT_NAME} PRIVATE "_AFXDLL")

target_include_directories(${PROJECT_NAME} PRIVATE "include")

target_precompile_headers(${PROJECT_NAME} PRIVATE "DelHel/pch.h")

target_link_libraries(${PROJECT_NAME} PRIVATE "${CMAKE_SOURCE_DIR}/lib/EuroScope/EuroScopePlugInDll.lib")

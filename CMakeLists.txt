cmake_minimum_required(VERSION 3.2.0)

# set a compiler to point o custom llvm/clang build
#set(CMAKE_CXX_COMPILER "/usr/local/opt/llvm/bin/clang++")

project(root-cpp)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${CMAKE_SOURCE_DIR}/cmake_modules")
set(Arrow_FIND_QUIETLY OFF)

# find root and arrow
find_package(ROOT)
find_package(Arrow)

add_definitions(${ROOT_CXX_FLAGS})

include_directories(SYSTEM ${ARROW_INCLUDE_DIR})
include_directories(${PROJECT_SOURCE_DIR} ${ROOT_INCLUDE_DIRS})

add_executable(test-root-arrow ${CMAKE_SOURCE_DIR}/src/root-cpp/test.cpp)
target_link_libraries(test-root-arrow ${ROOT_LIBRARIES} ${ARROW_SHARED_LIB})

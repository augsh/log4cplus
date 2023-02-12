cmake_minimum_required(VERSION 3.20)

project(log4cplus)

set(CMAKE_CXX_STANDARD 17)

add_library(${PROJECT_NAME} INTERFACE IMPORTED GLOBAL)
target_include_directories(${PROJECT_NAME} INTERFACE include)
file(GLOB_RECURSE SO_FILES "./lib/*.so")
target_link_libraries(${PROJECT_NAME} INTERFACE ${SO_FILES})

if(NOT ${OUT} STREQUAL "")
  message("Set output directory to ${OUT}")
  file(GLOB_RECURSE LIBS "./lib/*")
  file(COPY ${LIBS} DESTINATION ${OUT_LIB})
endif()

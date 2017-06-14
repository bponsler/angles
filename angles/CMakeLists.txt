cmake_minimum_required(VERSION 2.8)
project(angles)

# Add support for C++11
if(NOT WIN32)
  add_definitions(-std=c++11)
endif()

find_package(ament_cmake REQUIRED)
find_package(ament_cmake_python REQUIRED)

ament_python_install_package(${PROJECT_NAME})

set(INCLUDE_DIRS include ${ament_cmake_INCLUDE_DIRS})
include_directories(${INCLUDE_DIRS})

set(LIBRARY_DIRS ${ament_cmake_LIBRARY_DIRS})

link_directories(${LIBRARY_DIRS})

set(LIBS ${ament_cmake_LIBRARIES})

install(DIRECTORY include/${PROJECT_NAME}/
  DESTINATION include/${PROJECT_NAME}
  FILES_MATCHING
  PATTERN "*.h")

if(BUILD_TESTING)
  add_subdirectory(test)
endif()

ament_export_dependencies(ament_cmake)
ament_export_dependencies(ament_cmake_python)
ament_export_include_directories(${INCLUDE_DIRS})

ament_package()

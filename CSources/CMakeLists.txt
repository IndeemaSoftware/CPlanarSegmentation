cmake_minimum_required(VERSION 2.8.12)

project(PlanarSegmentation DESCRIPTION "Planar Segmentation wrapper over PCL lib")

set(CMAKE_INCLUDE_CURRENT_DIR ON)
set(CMAKE_AUTOMOC ON)

include_directories( ${MY_SOURCE_DIR} )

add_library(${PROJECT_NAME} SHARED CPlanarSegmentation.mm)

cmake_minimum_required(VERSION 2.6 FATAL_ERROR)
find_package(PCL 1.3 REQUIRED COMPONENTS common io segmentation keypoints)
include_directories(${PCL_INCLUDE_DIRS})
link_directories(${PCL_LIBRARY_DIRS})
add_definitions(${PCL_DEFINITIONS})
target_link_libraries(${PROJECT_NAME} ${PCL_SEGMENTATION_LIBRARIES} ${PCL_COMMON_LIBRARIES} ${PCL_IO_LIBRARIES})

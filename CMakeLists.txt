cmake_minimum_required(VERSION 3.0)
set(CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR})
find_package(OpenCV 4 REQUIRED)
find_package(Eigen3 REQUIRED)
find_package(Ceres  REQUIRED)

include_directories(${OpenCV_INCLUDE_DIRS})
include_directories(${EIGEN3_INCLUDE_DIR})
include_directories(${CERES_INCLUDE_DIRS})
include_directories(include/predictor include/data_type include/common)
add_compile_definitions(PROJECT_DIR="${PROJECT_SOURCE_DIR}")
aux_source_directory(src/predictor predictor_src)
aux_source_directory(src/detector detector_src)
add_library(predictor  SHARED ${predictor_src})
add_library(detector  SHARED ${detector_src})

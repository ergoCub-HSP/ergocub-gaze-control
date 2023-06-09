################################################################################
#                                                                              #
# Copyright (C) 2020 Fondazione Istituto Italiano di Tecnologia (IIT)          #
# All Rights Reserved.                                                         #
#                                                                              #
################################################################################

cmake_minimum_required(VERSION 3.12)

project(gaze_controller LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

# Create the component (navigation client)
find_package(YARP COMPONENTS os dev idl_tools REQUIRED)

add_library(gaze_controller STATIC)
# Create the grasp_interface C++ Library
yarp_add_idl(IDL_GEN_FILES gaze-controller.thrift)

target_sources(gaze_controller
    PRIVATE
    ${IDL_GEN_FILES}
)
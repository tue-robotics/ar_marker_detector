cmake_minimum_required(VERSION 2.8.3)
project(ar_marker_detector)

find_package(catkin REQUIRED COMPONENTS
    artoolkit
    rgbd
    tf
    message_generation
)

# find_package(Boost REQUIRED COMPONENTS system program_options)
# find_package(PCL REQUIRED)
# find_package(OpenCV REQUIRED)

# ------------------------------------------------------------------------------------------------
#                                     ROS MESSAGES AND SERVICES
# ------------------------------------------------------------------------------------------------

# Generate messages
# add_message_files(
#    FILES
#    message1.msg
#    ...
# )

# Generate services
 add_service_files(
    FILES
    Toggle.srv
)

# Generate added messages and services with any dependencies listed here
generate_messages(
    DEPENDENCIES
)

# ------------------------------------------------------------------------------------------------
#                                          CATKIN EXPORT
# ------------------------------------------------------------------------------------------------

catkin_package(
#  INCLUDE_DIRS include
#  LIBRARIES bla
#  CATKIN_DEPENDS other_catkin_pkg
#  DEPENDS system_lib
)

# ------------------------------------------------------------------------------------------------
#                                              BUILD
# ------------------------------------------------------------------------------------------------

include_directories(
    include
    ${catkin_INCLUDE_DIRS}
)

# add_library(library_name
#     src/lib_source_file1.cpp
#     ...
# )
# target_link_libraries(library_name ${catkin_LIBRARIES})

add_executable(ar_marker_detector
    src/ar_marker_detector.cpp
    src/object.cpp
)
target_link_libraries(ar_marker_detector ${catkin_LIBRARIES})
add_dependencies(ar_marker_detector ${PROJECT_NAME}_gencpp)


cmake_minimum_required(VERSION 2.8.3)

project(robot_geometry_msgs)



# check c++11 / c++0x
include(CheckCXXCompilerFlag)
CHECK_CXX_COMPILER_FLAG("-std=c++11" COMPILER_SUPPORTS_CXX11)
CHECK_CXX_COMPILER_FLAG("-std=c++0x" COMPILER_SUPPORTS_CXX0X)
if(COMPILER_SUPPORTS_CXX11)
    #set(CMAKE_CXX_FLAGS "-std=c++11")
    add_definitions(-std=c++11)
elseif(COMPILER_SUPPORTS_CXX0X)
    #set(CMAKE_CXX_FLAGS "-std=c++0x")
    add_definitions(-std=c++0x)
else()
    message(FATAL_ERROR "The compiler ${CMAKE_CXX_COMPILER} has no C++11 support. Please use a different C++ compiler.")
endif()





find_package(catkin REQUIRED
                COMPONENTS message_generation std_msgs geometry_msgs)



add_message_files(
    DIRECTORY
        msg
    FILES
        PointWithCovariance.msg
        PointWithCovarianceStamped.msg
        RobotState.msg


)



generate_messages(DEPENDENCIES std_msgs geometry_msgs)




catkin_package(
    CATKIN_DEPENDS message_runtime std_msgs geometry_msgs
	)



#include_directories(${catkin_INCLUDE_DIRS})


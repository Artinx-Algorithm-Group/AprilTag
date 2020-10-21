cmake_minimum_required(VERSION 3.0.0)
project(OpenCV_template VERSION 0.1.0)

# include(CTest)
# enable_testing()

find_package(OpenCV REQUIRED)


SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -pthread")


# aux_source_directory(./src DIR_SRCS)
# aux_source_directory(./inc DIR_SRCS)
# aux_source_directory(./inc/apriltag DIR_SRCS)
# aux_source_directory(./inc/apriltag/common DIR_SRCS)




# include_directories(/home/babyxin/AprilTag/sample/buildDLL/install/include)


# add_executable(OpenCV_template ${DIR_SRCS})

# include_directories(/home/babyxin/AprilTag/sample/buildDLL/libaprilTagLocator)
# include_directories(/home/babyxin/AprilTag/sample/buildDLL/libaprilTagLocator/apriltag)
# include_directories(./inc/apriltag/common)
include_directories(../buildDLL/libaprilTagLocator)
include_directories(/usr/local/include/apriltag)
include_directories(/usr/local/include/apriltag/common)
# add_executable(OpenCV_template ${DIR_SRCS})
ADD_EXECUTABLE(OpenCV_template ./main.cpp)



target_link_libraries(OpenCV_template /usr/local/lib/libapriltag_lib.so)
target_link_libraries(OpenCV_template ${OpenCV_LIBS})



# set(CMAKE_BUILD_TYPE "Debug")

# set(CPACK_PROJECT_NAME ${PROJECT_NAME})
# set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
# include(CPack)

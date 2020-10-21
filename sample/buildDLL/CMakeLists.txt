cmake_minimum_required(VERSION 3.0.0)
project(OpenCV_template VERSION 0.1.0)

# include(CTest)
# enable_testing()

find_package(OpenCV REQUIRED)


SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -pthread")

aux_source_directory(./libaprilTagLocator DIR_SRCS)
aux_source_directory(./libaprilTagLocator/apriltag DIR_SRCS)
aux_source_directory(./libaprilTagLocator/apriltag/common DIR_SRCS)
# aux_source_directory( DIR_SRCS)

include_directories(./install/include/apriltag)
include_directories(./install/include)
# include_directories(./libaprilTagLocator)

ADD_EXECUTABLE(OpenCV_template ${DIR_SRCS})


# SET(${apriltag_lib} ./apriltag)
# set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR} ../runWithDLL/lib)

set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ../install/lib)
ADD_LIBRARY(apriltag_lib SHARED ${DIR_SRCS} )
# LINK_DIRECTORIES(/usr/local/lib)
# TARGET_LINK_LIBRARIES(OpenCV_template ${apriltag_lib})

target_link_libraries(apriltag_lib ${OpenCV_LIBS})

# set(CMAKE_BUILD_TYPE "Debug")

# set(CPACK_PROJECT_NAME ${PROJECT_NAME})
# set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
# include(CPack)




install(TARGETS apriltag_lib LIBRARY DESTINATION lib)

INSTALL(FILES ${PROJECT_SOURCE_DIR}/libaprilTagLocator/aprilTagLocator.hpp
DESTINATION include)


INSTALL(DIRECTORY ${PROJECT_SOURCE_DIR}/libaprilTagLocator/apriltag
DESTINATION include)



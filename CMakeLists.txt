cmake_minimum_required(VERSION 3.5)

project(glm_ros)

set(CMAKE_BUILD_TYPE Release)

set(LIBRARY_NAME "${PROJECT_NAME}")

find_package(catkin)
catkin_package(LIBRARIES ${LIBRARY_NAME})

add_library(${LIBRARY_NAME} INTERFACE)

target_include_directories(${LIBRARY_NAME} INTERFACE glm/)

add_dependencies(${LIBRARY_NAME} ${catkin_EXPORTED_TARGETS}) 

## Mark the library for installations
install(TARGETS 
    ${LIBRARY_NAME}
    ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
    LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
    RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

# install header files
install(
    DIRECTORY 
    glm/glm/
    DESTINATION ${CATKIN_PACKAGE_INCLUDE_DESTINATION}
    FILES_MATCHING PATTERN "*.h"
)


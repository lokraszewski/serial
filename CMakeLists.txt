cmake_minimum_required(VERSION 2.8.3)
project(serial)

set(PROJECT_BRIEF "\"Serial Port library written in C++\"")

# if(UNIX AND NOT APPLE)
#     # If Linux, add rt and pthread
#     set(rt_LIBRARIES rt)
#     set(pthread_LIBRARIES pthread)
#     catkin_package(
#         LIBRARIES ${PROJECT_NAME}
#         INCLUDE_DIRS include
#         DEPENDS rt pthread
#     )
# else()
#     # Otherwise normal call
#     catkin_package(
#         LIBRARIES ${PROJECT_NAME}
#         INCLUDE_DIRS include
#     )
# endif()

# Enable/disable testing
option(TESTS_ENABLED "Enable automatic tests" OFF)

set(LIBRARY_OUTPUT_PATH "${CMAKE_BINARY_DIR}/lib")
set(EXECUTABLE_OUTPUT_PATH "${CMAKE_BINARY_DIR}/bin")

set(CMAKE_CXX_FLAGS_DEBUG "-Wall -O0 -ggdb")
set(CMAKE_CXX_FLAGS_RELEASE "-Wall -O2")

set(CMAKE_INCLUDE_CURRENT_DIR ON)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

if (NOT CMAKE_BUILD_TYPE)
    message(STATUS "No build type selected, defaulting to Debug")
    set(CMAKE_BUILD_TYPE "Debug")
endif()

add_subdirectory(serial)



## Uncomment for example
# add_executable(serial_example examples/serial_example.cc)
# add_dependencies(serial_example ${PROJECT_NAME})
# target_link_libraries(serial_example ${PROJECT_NAME})

## Include headers
# include_directories(include)

## Install executable
# install(TARGETS ${PROJECT_NAME}
#     ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
#     LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
# )

# ## Install headers
# install(FILES include/serial/serial.h include/serial/v8stdint.h
#   DESTINATION ${CATKIN_GLOBAL_INCLUDE_DESTINATION}/serial)

# ## Tests
# if(CATKIN_ENABLE_TESTING)
#     add_subdirectory(tests)
# endif()

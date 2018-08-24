# Sources
set(serial_SRCS
    src/serial.cc
)

if(APPLE)
  # If OSX
  list(APPEND serial_SRCS src/impl/unix.cc)
  list(APPEND serial_SRCS src/impl/list_ports/list_ports_osx.cc)
elseif(UNIX)
    # If unix
    list(APPEND serial_SRCS src/impl/unix.cc)
    list(APPEND serial_SRCS src/impl/list_ports/list_ports_linux.cc)
else()
    # If windows
    list(APPEND serial_SRCS src/impl/win.cc)
    list(APPEND serial_SRCS src/impl/list_ports/list_ports_win.cc)
endif()

message(STATUS "Building ${PROJECT_NAME} with: ")
foreach (_src ${serial_SRCS})
    message(STATUS "  ${_src}")
endforeach()


## Add serial library
add_library(${PROJECT_NAME} ${serial_SRCS})

# setup include directories
target_include_directories(${PROJECT_NAME} PUBLIC
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
  $<INSTALL_INTERFACE:include>
)

if(APPLE)
  target_link_libraries(${PROJECT_NAME} ${FOUNDATION_LIBRARY} ${IOKIT_LIBRARY})
elseif(UNIX)
  target_link_libraries(${PROJECT_NAME} rt pthread)
else()
  target_link_libraries(${PROJECT_NAME} setupapi)
endif()


 # setup export preprocessor definitions
if(BUILD_SHARED_LIBS)
  target_compile_definitions(${PROJECT_NAME} PRIVATE ${PROJECT_NAME}_EXPORTS)
  target_compile_definitions(${PROJECT_NAME} INTERFACE ${PROJECT_NAME}_IMPORTS)
endif()

if(TESTS_ENABLED)
  message(STATUS "Testing enabled.")
  add_subdirectory(test)
else()
  message(STATUS "Testing disabled.")
endif()

cmake_minimum_required (VERSION 2.6) 

set(CMAKE_BUILD_TYPE DEBUG)
set(CMAKE_FIND_FRAMEWORK NEVER FORCE)
set(CMAKE_FIND_APPBUNDLE NEVER)

project(adapter)

set(CMAKE_BUILD_TYPE DEBUG)
set(CMAKE_FIND_FRAMEWORK NEVER FORCE)
set(CMAKE_FIND_APPBUNDLE NEVER)

set(YAML_CPP_SOURCE_DIR ../yaml/src)
set(YAML_CPP_INCLUDE_DIR ../yaml/include)
set(ADAPTER_CPP_SOURCE_DIR ../src)
set(ADAPTER_CPP_INCLUDE_DIR ../src)

#
file(GLOB yaml_sources ${YAML_CPP_SOURCE_DIR}/[a-z]*.cpp)
file(GLOB adapter_sources ${ADAPTER_CPP_SOURCE_DIR}/[a-z_]*.cpp)
file(GLOB modbus_sources [a-zA-Z_]*.cpp [a-z]*.c)
file(GLOB headers [a-z_]*.hpp)

include_directories(${YAML_CPP_SOURCE_DIR} ${YAML_CPP_INCLUDE_DIR} ${ADAPTER_CPP_INCLUDE_DIR})

add_executable(adapter ${yaml_sources} ${adapter_sources} ${modbus_sources})

if(WIN32)
  target_link_libraries(adapter wsock32.lib)
endif(WIN32)



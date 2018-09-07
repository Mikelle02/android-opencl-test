cmake_minimum_required(VERSION 3.4.1)

set(CMAKE_VERBOSE_MAKEFILE on)
set(libs "${CMAKE_SOURCE_DIR}/src/main/jniLibs")

add_library(libOpenCL SHARED IMPORTED )
add_library(androidHardwareCommon10 SHARED  IMPORTED)

set_target_properties(libOpenCL PROPERTIES IMPORTED_LOCATION "${libs}/${ANDROID_ABI}/libOpenCL.so")

add_library( native-lib SHARED src/main/cpp/native-lib.cpp )
find_library(  log-lib log )
target_link_libraries( native-lib libOpenCL ${log-lib} )
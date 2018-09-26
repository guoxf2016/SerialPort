
# Sets the minimum version of CMake required to build the native library.

cmake_minimum_required(VERSION 3.4.1)


include_directories(${CMAKE_SOURCE_DIR}/src/main/cpp/include)

add_library( # Sets the name of the library.
             native-lib

             # Sets the library as a shared library.
             SHARED

             # Provides a relative path to your source file(s).
             src/main/cpp/native-lib.cpp )

find_library( # Sets the name of the path variable.
              log-lib

              # Specifies the name of the NDK library that
              # you want CMake to locate.
              log )

add_library(serial_port SHARED src/main/cpp/SerialPort.c)

target_link_libraries( # Specifies the target library.
                       native-lib

                       # Links the target library to the log library
                       # included in the NDK.
                       ${log-lib} )

                       target_link_libraries(serial_port log android)
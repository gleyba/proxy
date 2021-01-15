cmake_minimum_required(VERSION 3.15)
project(envoy)

set(CMAKE_CXX_STANDARD 17)

execute_process(
    COMMAND
    bazel run //:cmake_gen
    RESULT_VARIABLE ret
)
if(NOT ret EQUAL "0")
    message( FATAL_ERROR "Bad bazel exit status")
endif()

include(cmake_gen/all_deps.cmake)
include(cmake_gen/all.cmake)
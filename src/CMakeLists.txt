# cmake_minimum_required(VERSION 3.19)
# 注意：此处没有 project() 命令

include(FetchContent)
FetchContent_Declare(
    fmt
    GIT_REPOSITORY https://github.com/fmtlib/fmt.git
    GIT_SHALLOW ON
    GIT_TAG "9.1.0"
)
FetchContent_MakeAvailable(fmt)


# fmt_test_lib
add_library(
    fmt_wrapper_lib 
    STATIC 
    fmt_wrapper.cc
)
add_library(fmt_test_lib::fmt_test_lib ALIAS fmt_test_lib)


target_include_directories(
    fmt_wrapper_lib
    PUBLIC
    ${PROJECT_SOURCE_DIR}/include
)

target_link_libraries(
    fmt_wrapper_lib
    PUBLIC
    fmt::fmt
)

# test main
add_executable(
    fmt_test_main
    main.cpp
)

target_include_directories(
    fmt_test_main
    PRIVATE
    ${CMAKE_CURRENT_SOURCE_DIR}/
)

target_link_libraries(
    fmt_test_main
    fmt_wrapper_lib
)


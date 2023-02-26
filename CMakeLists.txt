cmake_minimum_required(VERSION 3.19)
project(fmt_test LANGUAGES C CXX)

# 导出 compile_commands.json 文件
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)
set(CMAKE_CXX_STANDARD 17)

add_subdirectory(src)

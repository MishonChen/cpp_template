#要求 CMake 最低版本
cmake_minimum_required(VERSION 3.5.0)
#工程名称（根目录必须设置工程名称，设置相同工程名的文件将会被视作同一工程）
project(cpp_template VERSION 0.1.0 LANGUAGES C CXX)
# cpp 版本
set(CMAKE_CXX_STANDARD 20)
#添加源外构建，增加 include 的搜索路径（类似于 C++ 添加头文件搜索路径）
set(CMAKE_MODULE_PATH
    ${CMAKE_MODULE_PATH}
    ${CMAKE_CURRENT_SOURCE_DIR}/cmake_modules
    )
#添加 basicEnv 文件中的内容（类似于 C++ 中的 #include）
include(basic_env)

add_executable(build_file src/main.cpp)
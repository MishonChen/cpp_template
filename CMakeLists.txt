# 检查 CMake 版本
cmake_minimum_required(VERSION 3.19)
project(cpp_template VERSION 0.1.0 LANGUAGES C CXX)

# 设置 C++ 标准
set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD_REQUIRED True)
set(CMAKE_CXX_EXTENSIONS OFF)

# 启用调试模式和 AddressSanitizer
if(CMAKE_BUILD_TYPE STREQUAL "Debug")
    # 添加调试信息和额外警告
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -g3 -DDEBUG -Wall -Wextra -Wpedantic")
    set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -g3 -DDEBUG -Wall -Wextra -Wpedantic")

    # 启用 AddressSanitizer (内存检查)
    set(SANITIZE_ADDRESS ON)
    if(SANITIZE_ADDRESS)
        add_compile_options(-fsanitize=address)
        add_link_options(-fsanitize=address)
    endif()
endif()

# 添加可执行文件
add_executable(build_file src/main.cpp)

# 查找 fmt 包
find_package(fmt CONFIG REQUIRED)

# 将 fmt 链接到目标
target_link_libraries(build_file PRIVATE fmt::fmt)

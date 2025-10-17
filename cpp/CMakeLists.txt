cmake_minimum_required(VERSION 3.16)
project(cpp)

# 设置 C++ 标准
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# 生成静态库（或 SHARED 动态库）
add_library(${PROJECT_NAME} STATIC src/func.cpp)
# 头文件路径（供 Rust FFI 使用）
target_include_directories(${PROJECT_NAME} PUBLIC ${CMAKE_SOURCE_DIR}/include)
install(TARGETS ${PROJECT_NAME} DESTINATION ${CMAKE_SOURCE_DIR}/install)

# # 生成可执行文件
set(PROJECT_EXEC_NAME ${PROJECT_NAME}_bin)
add_executable(${PROJECT_EXEC_NAME} main.cpp src/func.cpp)
target_include_directories(${PROJECT_EXEC_NAME} PUBLIC include)
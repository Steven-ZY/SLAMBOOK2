# 声明要求的cmake最低版本
cmake_minimum_required(VERSION 2.8)

# 声明一个cmake工程
project(HelloSLAM)

# 添加一个可执行程序
# 语法：add_executable(程序名  源代码文件)
add_executable(HelloSLAM helloSLAM.cpp)

# 添加一个叫作“hello”的静态库
add_library(hello libhelloSLAM.cpp)

# 添加一个叫做“hello_shared”的共享库
add_library(hello_shared SHARED libhelloSLAM.cpp)

# 添加一个可执行程序
# 链接到使用的静态库上,注意到usehello.cpp和hello.a链接到一起，
# 前面生成库的时候hello.a和libhelloSLAM.cpp有关，
# 所以usehello.cpp和libhelloSLAM.cpp有了联系
add_executable(usehello usehello.cpp)
target_link_libraries(usehello hello)

# 添加一个可执行程序
# 链接到使用的共享库上
add_executable(usehello_shared usehello.cpp)
target_link_libraries(usehello_shared hello_shared)


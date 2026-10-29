# Cmake

 ## 从源代码到可执行程序
      hello.c(文本)
### - 预处理
      展开头文件
      g++ -E main.cpp -o main.ii
      hello.i(文本)
### - 编译
      生成汇编语言
      g++ -S main.ii -o main.s
      hello.s(文本)
### - 汇编
      生成机器码
      g++ -c main.s -o main.o
      hello.o
### - 链接
      g++ main.o add.o -o demo
      链接到静态库或者动态库（共享库）
一次性全执行 : ==g++ main.cpp add.cpp -o demo==
      

## CMakeLists.txt 文件
### 格式
###### 命令名(参数列表)
文件名为cmakelist.txt，不可随意改变
每一个Cmake项目至少要有一个cmakelist.txt文件
=>cmake项目 ： 由cmake管理的一个由源代码，配置文件以及其他相关文件组成的整体

#### 命令
  - cmake_minimum_required(VERSION 3.10)  ---指定CMAKE最低版本
  - project(<项目名> [语言]) -----定义项目名称和语言
  - aux_source_directory(. 变量名1) -----取出当前目录下的所有指定语言文件
  - add_executable(<目标名>  <源文件>或 ${变量名1}) ----将指定源文件编译生成一个可执行文件
  ```cmake
  cmake_minimum_required(VERSION 3.10)
  project(project1 cpp)
  add_source_directory(. CMAKRLEARN)
  add_executable(main2 ${CMAKRLEARN})
  target_include_directories(main2 PRIVATE include)
  #局部绑定头文件，只给main2用，PRIVATE表示当前头文件只允许给main2用
  ```
#### 规则

头文件一般放在include文件夹里，源文件一般放在src文件夹里，cmake生成的其他文件放在build文件夹里，生成的目标文件放在bin文件夹里
实现：
```cmake
cmake_minimum_required(VERSION 3.19)
project(project3)
aux_source_directory("${CMAKE_CURRENT_SOURCE_DIR}/src" SOURCES)
add_executable(demo ${SOURCES})
target_include_directories(demo PRIVATE "${CMAKE_SOURCE_DIR}/include")
```
#### 增量构建
      有时只改了一部分文件，没有全改，不用全编译
      For example:
```shell
      vim main.cpp
      vim add.cpp
      g++ main.cpp add.cpp -o demo
      ./demo
      vim add.cpp
      g++ -c add.cpp
      g++ add.cpp main.cpp -o demo
```
==makefile文件中增量构建由make自动判断，由于add.cpp时间戳晚于add.o，判定被修改，重新编译，然后检查依赖，发现demo，也会重新编译==

# catkin

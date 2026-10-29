# Cmake

 ## 从源代码到可执行程序
      hello.c(文本)
### - 预处理
      展开头文件
      g++ -E main.cpp -o main.i
      hello.i(文本)
### - 编译
      生成汇编语言
      g++ -S main.i -o main.s
      hello.s(文本)
### - 汇编
      生成机器码
      g++ -c main.s -o main.o
      hello.o
### - 链接
      g++ main.o add.o -o demo
      链接到静态库或者动态库（共享库）
      

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
  ```
#### 规则

头文件一般放在include文件夹里，源文件一般放在src文件夹里，cmake生成的其他文件放在build文件夹里，生成的目标文件放在bin文件夹里
实现：
```cmake
cmake_minimum_required(VERSION 3.19)
project(project3)
set (EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)
add_source_directory(src CMAKELEARN)
include_directories(include)
add_exevutable(main3 ${CMAKELEARN})
```

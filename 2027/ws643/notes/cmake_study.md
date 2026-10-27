# Cmake

## cmakelists.txt 文件
### 格式
###### 命令名(参数列表)
文件名为cmakelist.txt，不可随意改变
每一个Cmake项目至少要有一个cmakelist.txt文件
=>cmake项目 ： 由cmake管理的一个由源代码，配置文件以及其他相关文件组成的整体

#### 命令
  - cmake_minimum_required(VERSION 3.10)  ---指定CMAKE最低版本
  - project(<项目名> [语言]) -----定义项目名称和语言
  - add_executable(<目标名>  <源文件>) ----将指定源文件编译生成一个可执行文件
>> cmake 使用

##### cmake 概述

```
    CMake 是一个项目构建工具，并且是跨平台的。关于项目构建我们所熟知的还有 Makefile（通过 make 命令进行项目的构建），大多是 IDE 软件都集成了 make，比如：VS 的 nmake、linux 下的 GNU make、Qt 的 qmake 等，如果自己动手写 makefile，会发现makefile 通常依赖于当前的编译平台，而且编写 makefile 的工作量比较大，解决依赖关系时也容易出错

    而 CMake 恰好能解决上述问题， 其允许开发者指定整个工程的编译流程，在根据编译平台，自动生成本地化的Makefile和工程文件，最后用户只需 make 编译即可，所以可以把 CMake 看成一款自动生成 Makefile 的工具，其编译流程如下图：
```

![image](https://github.com/chuanchuan11/compile/assets/42632290/83e67295-9dba-4aaa-bdb8-041a86ef2c80)

```
    CMake优点：
        1) 跨平台
        2) 能够管理大型项目
        3) 简化编译构建过程和编译过程
        4) 可扩展：可以为 cmake 编写特定功能的模块，扩充 cmake 功能
```

##### cmake 使用

1. 注释

```
1) 注释行: #, 可以放在任何位置

    # 这是一个 CMakeLists.txt 文件

2) 注释块: #[[ ]]

    #[[ 这是一个 CMakeLists.txt 文件。
        这是一个 CMakeLists.txt 文件
        这是一个 CMakeLists.txt 文件
     ]]
```

2. 基础语法

```
1) cmake_minimum_required:指定使用的 cmake 的最低版本, 可选非必须, 如果不加可能会有警告, 限制当前使用的最小版本

    cmake_minimum_required(VERSION 3.0)  //最小版本3.0, 如果使用语法较新, 可能在低版本上识别不到

2) project：定义工程名称，并可指定工程的版本、工程描述、web 主页地址、支持的语言（默认情况支持所有语言），如果不需要这些都是可以忽略的，只需要指定出工程名字即可

    # PROJECT 指令的语法是：
            project(<PROJECT-NAME>
                   [VERSION <major>[.<minor>[.<patch>[.<tweak>]]]]
                   [DESCRIPTION <project-description-string>]
                   [HOMEPAGE_URL <url-string>]
                   [LANGUAGES <language-name>...])
    # 示例:
            project(CALC)
            
3) add_executable：定义工程会生成一个可执行程序
    
    # 语法: 
            add_executable(可执行程序名 源文件名称)   # 这里的可执行程序名和 project 中的项目名没有任何关系;源文件多个可用空格或 ; 间隔

    #示例:
            # 样式1
            add_executable(app add.c div.c main.c mult.c sub.c)
            # 样式2
            add_executable(app add.c;div.c;main.c;mult.c;sub.c)

4) 


```























参考:
    
    (1) https://subingwen.cn/cmake/CMake-primer/index.html

    (2) video: https://www.bilibili.com/video/BV14s4y1g7Zj/?spm_id_from=333.337.search-card.all.click&vd_source=98927128f68a56b0d2bde9738177a671

>> demo1

```
(1) 所有源文件都在一个文件夹下
    $ tree
    .
    ├── add.c
    ├── div.c
    ├── head.h
    ├── main.c
    ├── mult.c
    └── sub.c

(2) CMakeList.txt编写

    cmake_minimum_required(VERSION 3.0)
    project(CALC)
    add_executable(app add.c div.c main.c mult.c sub.c)

(3) 执行cmake . 生成makefile
  
     cmake后跟的CMakeLists.txt所在路径

(4) 执行命令之后，看一下源文件所在目录中是否多了一些文件, 且生成Makefile
    $ tree -L 1
    .
    ├── add.c
    ├── CMakeCache.txt         # new add file
    ├── CMakeFiles             # new add dir
    ├── cmake_install.cmake    # new add file
    ├── CMakeLists.txt
    ├── div.c
    ├── head.h
    ├── main.c
    ├── Makefile               # new add file
    ├── mult.c
    └── sub.c

(5) 执行 make 生成可执行程序
    
    app

```

    问题: 
    
        如果在 CMakeLists.txt 文件所在目录执行了 cmake 命令之后就会生成一些目录和文件（包括 makefile 文件），如果再基于 makefile文件执行 make 命令，程序在编译过程中还会生成一些中间文件和一个可执行文件，这样会导致整个项目目录看起来很混乱，不太容易管理和维护
        
        此时我们就可以把生成的这些与项目源码无关的文件统一放到一个对应的目录里边，比如将这个目录命名为 build:

```
(1) 创建build目录，在目录中执行cmake

    $ mkdir build
    $ cd build
    $ cmake ..

(2) 查看build目录, 中间文件都生成在其中, 不会与源文件混淆
    $ tree build -L 1
    build
    ├── CMakeCache.txt
    ├── CMakeFiles
    ├── cmake_install.cmake
    └── Makefile

```



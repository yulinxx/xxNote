## find_package

```cmake
cmake_minimum_required(VERSION 3.0)
project(helloworld)
add_executable(helloworld hello.c)
find_package(Zlib)

# Global approach
if(ZLIB_FOUND)
   include_directories(${ZLIB_INCLUDE_DIRS})
   target_link_libraries (helloworld ${ZLIB_LIBRARIES})
endif()

# Modern CMake targets approach
if(TARGET zlib::zlib)
   target_link_libraries(helloworld zlib::zlib)
endif()
```



`find_package`用于查找包（通常是使用三方库），并返回关于包的细节（使用包所依赖的头文件、库文件、编译选项、链接选项等）  
  与[`find_libaray`](https://www.jianshu.com/p/8a64c77343cb)直接在指定搜索目录下搜索库不同，`find_package`命令可以获取更多的信息，那么它的搜索方式也是与`find_libaray`不一样，它有两种不同的搜索方式，因此在介绍这个命令的细节之前，先简单介绍一下`find_package`命令的两种搜索模式：**模块模式**（`Module mode`）和**配置模式**（`Config mode`）。



链接：https://www.jianshu.com/p/a0915895dbbc  


当执行find_package()这条命令后,Cmake 就会从某些路径中找这Findxxx.cmake文件或者xxxConfig.cmake文件，Cmake找到任意一个之后就会执行这个文件，然后这个文件执行后就会设置好一些Cmake变量。比如下面的变量（NAME表示库的名字 比如可以用Opencv 代表Opencv库）:

```cmake
<NAME>_FOUND
<NAME>_INCLUDE_DIRS or <NAME>_INCLUDES
<NAME>_LIBRARIES or <NAME>_LIBRARIES or <NAME>_LIBS
<NAME>_DEFINITIONS
```

https://blog.csdn.net/chengde6896383/article/details/86497016

一般常用的就是xxx_FOUND 、xxx_INCLUDE_DIRS、xxx_LIBS，分别代表是否找到库的标志、库的头文件路径、库文件路径。

**Module模式(仅仅查找Findxxx.cmake文件):**
`cmake -DCMAKE_INSTALL_PREFIX=路径` ，那么此时CMAKE_ROOT就代表那个你写入的路径 。刚刚说道第一优先级的路径搜索没有找到Findxxx.cmake文件，就会到第二优先级的路径下搜索。如果Cmake在两个路径下都没有找到Findxxx.cmake文件。那么Cmake就会进入Config模式。

**Config模式（仅仅查找xxxConfig.cmake文件）：**
优先搜索xxx_DIR 指定的路径。如果在CMakeLists.txt中没有设置这个cmake变量。也就是说没有下面的指令:
`set(xxx_DIR "xxxConfig.cmkae文件所在的路径")`
那么Cmake就不会搜索xxx_DIR指定的路径，此时Cmake 就会自动到第二优先级的路径下搜索，也就是/usr/local/lib/cmake/xxx/中的xxxConfig.cmake文件。



 

## 循环遍历

##### 遍历list所有元素

*语法如下*

```cmake
foreach(<loop_var> <items>)
    <command>
endeach()
```

*举例如下*

```cmake
set(LIST_SRC a.cpp b.cpp c.cpp)
foreach(item ${LIST_SRC})
    message(STATUS "item is ${item}")
endforeach()
```

##### 从零开始到目标结果，stop不可为负数，默认步长为1

*语法如下*

```cmake
foreach(<loop_var> RANGE <stop>) 
```

*举例如下*

```cmake
foreach(i RANGE 5)
    message(STATUS "i = ${i}")
endforeach()
```

##### 在起始位置和截至位置的跳动，左右都是闭区间，步长可指定，默认为1

*语法如下*

```cmake
foreach(<loop_var> RANGE <start> <stop> [<step>])
```

*举例如下*

```cmake
foreach(j RANGE 3 6)
    message("j = ${j}") 
endforeach()
foreach(k RANGE 3 6 2)
    message("k = ${k}") 
endforeach()
```

###### 多集合的并集

- LISTS可以认为是一个有名的集合，入set(A a b c)
- ITEMS可以认为是一个匿名的集合，如a b c  
  *语法如下*

```cmake
foreach(loop_var IN [LISTS [<lists>] [ITEMS [<items>]]])
```

*举例如下*

```cmake
set(A a b c)
set(B "1 2 3")

foreach(i IN ITEMS A B)
    message("i = ${i}")
endforeach()

foreach(i IN LISTS A B)
    message("i = ${i}")
endforeach()
```



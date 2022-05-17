[Valgrind官网https://valgrind.org/](https://valgrind.org/)

[valgrind 3.19.0 (tar.bz2)](https://sourceware.org/pub/valgrind/valgrind-3.19.0.tar.bz2) [16MB] - 11 April 2022.

valgrind安装： 

```bash
sudo apt install valgrind kcachegrind
```

源码安装:

```bash
//valgrind下载：
http://valgrind.org/downloads/valgrind-3.19.0.tar.bz2

valgrind安装：
1. tar -jxvf valgrind-3.19.0.tar.bz2
2. cd valgrind-3.19.0
3. ./configure
4. make
5. sudo make install
```

Linux动态分析工具valgrind使用入门_guotianqing的博客-CSDN博客_linux valgrind使用

https://blog.csdn.net/guotianqing/article/details/104023641

### Valgrind

Valgrind是用于构建动态分析工具的仪器框架。

Valgrind工具可以自动检测许多内存管理和线程错误，并能够详细分析应用程序。

Valgrind发行版有6个强大的工具：
(1). 一个内存错误检测器
(2). 两个线程错误检测器
(3). 一个缓存和分支预测分析器
(4). 一个调用图生成缓存和分支预测分析器
(5). 一个堆分析器

上述工具能够帮助程序员快速高效地分析程序问题所在。

###### 使用

LinuxC++内存泄漏检测神器valgrind - 知乎

https://zhuanlan.zhihu.com/p/458505244

用法: valgrind[options] prog-and-args [options]:  

常用选项，适用于所有Valgrind工具  
-tool= 最常用的选项。运行 valgrind中名为toolname的工具。默认memcheck。 h –help 显示帮助信息。  
-version 显示valgrind内核的版本，每个工具都有各自的版本。  
q –quiet 安静地运行，只打印错误信息。  
v –verbose 更详细的信息, 增加错误数统计。  
-trace-children=no|yes 跟踪子线程? [no]  
-track-fds=no|yes 跟踪打开的文件描述？[no]  
-time-stamp=no|yes 增加时间戳到LOG信息? [no]  
-log-fd= 输出LOG到描述符文件 [2=stderr]  
-log-file= 将输出的信息写入到filename.PID的文件里，PID是运行程序的进行ID  
-log-file-exactly= 输出LOG信息到 file  
-log-file-qualifier= `取得环境变量的值来做为输出信息的文件名。 [none]`  
-log-socket=ipaddr:port 输出LOG到socket ，ipaddr:port  
LOG信息输出:  
-xml=yes 将信息以xml格式输出，只有memcheck可用  
-num-callers= show callers in stack traces [12]  
-error-limit=no|yes 如果太多错误，则停止显示新错误? [yes]  
-error-exitcode= 如果发现错误则返回错误代码 [0=disable]  
-db-attach=no|yes 当出现错误，valgrind会自动启动调试器gdb。[no]  
-db-command= 启动调试器的命令行选项[gdb -nw %f %p]  
适用于Memcheck工具的相关选项：  
-leak-check=no|summary|full 要求对leak给出详细信息? [summary]  
-leak-resolution=low|med|high how much bt merging in leak check [low]  
-show-reachable=no|yes show reachable blocks in leak check? [no]

### KCacheGrind

Callgrind通过Valgrind框架使用运行时检测来进行缓存模拟和调用图生成。这样，即使是共享库和动态打开的插件也可以进行分析。可以将Callgrind生成的数据文件加载到KCachegrind中以浏览性能结果。但是包中还有一个命令行工具可以从数据文件中获取ASCII报告，而无需使用KCachegrind。

KCachegrind能够可视化其他分析器的输出使用带有硬件性能计数器的统计采样。还有可用于分析Python，PHP和PERL的输出的转换器。

https://www.jianshu.com/p/9e14e9936ff1

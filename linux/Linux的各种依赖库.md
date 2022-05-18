- Could NOT find Jasper (missing: JASPER_LIBRARIES JASPER_INCLUDE_DIR)
  https://askubuntu.com/questions/1079956/what-is-the-library-to-be-installed-for-jasper-h-header-file

```bash
wget http://archive.ubuntu.com/ubuntu/pool/main/j/jasper/libjasper-dev_1.900.1-debian1-2.4ubuntu1.3_amd64.deb
wget http://archive.ubuntu.com/ubuntu/pool/main/j/jasper/libjasper1_1.900.1-debian1-2.4ubuntu1.3_amd64.deb

sudo apt-get install ./libjasper-dev_1.900.1-debian1-2.4ubuntu1.3_amd64.deb ./libjasper1_1.900.1-debian1-2.4ubuntu1.3_amd64.deb
```

- minizip 
  No package 'minizip' found
  `sudo apt install libminizip-dev`

- bison
  `sudo apt-get install bison`
  GNU bison 是属于 GNU 项目的一个语法分析器生成器。(vcpkg install opencv 的时候需要)

- Looking for IceConnectionNumber in ICE - found
  CMake Error at CMakeLists.txt:213 (message):
  RandR headers not found; install **libxrandr** development package

```bash
x@x:~$ sudo apt search libxrandr
Sorting... Done
Full Text Search... Done
libxrandr-dev/jammy 2:1.5.2-1build1 amd64
  X11 RandR extension library (development headers)

libxrandr2/jammy,now 2:1.5.2-1build1 amd64 [installed,automatic]
  X11 RandR extension library

x@x:~$ sudo apt install libxrandr-dev
```

- - libatlas

  `sudo apt-get install libatlas-base-dev` OpenBLAS 是一个优化的 BLAS 库，基于 GotoBLAS2 1.13 BSD 版本。

BLAS（Basic Linear Algebra Subprograms 基础线性代数程序集）是一个应用程序接口（API）标准，用以规范发布基础线性代数操作的数值库（如矢量或矩阵乘法）。该程序集最初发布于 1979 年，并用于建立更大的数值程序包（如 LAPACK）。在高性能计算领域，BLAS 被广泛使用。例如，LINPACK 的运算成绩则很大程度上取决于 BLAS 中子程序 DGEMM 的表现。为提高性能，各軟硬件厂商则针对其產品对 BLAS 接口实现进行高度优化。



- VCPKG OpenCV
  
  libxdamage-dev
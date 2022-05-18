## Linux上的OpenGL开发环境搭建:

在Linux下你需要链接**libGL.so**库文件，这需要添加`-lGL`到你的链接器设置中。如果找不到这个库你可能需要安装Mesa  (`sudo apt install mesa-utils`)

对于用GCC编译的Linux用户建议使用这个命令行选项`-lglfw3 -lGL -lX11 -lpthread -lXrandr -lXi -ldl`。没有正确链接相应的库会产生 *undefined reference* (未定义的引用) 这个错误。  

查看OpoenGL版本:`glxinfo | grep -i opengl`

```bash
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: NVIDIA GeForce GTX 1050 Ti/PCIe/SSE2
OpenGL core profile version string: 4.6.0 NVIDIA 510.60.02
OpenGL core profile shading language version string: 4.60 NVIDIA
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 4.6.0 NVIDIA 510.60.02
OpenGL shading language version string: 4.60 NVIDIA
OpenGL context flags: (none)
OpenGL profile mask: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.2 NVIDIA 510.60.02
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20
OpenGL ES profile extensions:
```

可能需要安装如下信赖库:

```bash
sudo apt install libxinerama-dev

sudo apt install libxcursor-dev

sudo apt install libxi-dev
```

## GLFW 窗口

[https://github.com/glfw/glfw](https://github.com/glfw/glfw)  

[http://www.glfw.org/download.html](http://www.glfw.org/download.html)

> GLFW is an Open Source, multi-platform library for OpenGL, OpenGL ES and Vulkan application development. It provides a simple, platform-independent API for creating windows, contexts and surfaces, reading input, handling events, etc.   
> 
> GLFW是一个专门针对OpenGL的C语言库，它提供了一些渲染物体所需的最低限度的接口。它允许用户创建OpenGL上下文，定义窗口参数以及处理用户输入。

```bash
- x@x:~/cppProj/depends/$ git clone git@github.com:glfw/glfw.git
- x@x:~/cppProj/depends/glfw$ mkdir build
- x@x:~/cppProj/depends/glfw$ cd build/
- x@x:~/cppProj/depends/glfw/build$ cmake ..
- x@x:~/cppProj/depends/glfw/build$ make 
- x@x:~/cppProj/depends/glfw/build$ make install 
```

安装目录:  

```bash
Install the project...
-- Install configuration: ""
-- Installing: /usr/local/lib/libglfw3.a
-- Installing: /usr/local/include/GLFW
-- Installing: /usr/local/include/GLFW/glfw3.h
-- Installing: /usr/local/include/GLFW/glfw3native.h
-- Installing: /usr/local/lib/cmake/glfw3/glfw3Config.cmake
-- Installing: /usr/local/lib/cmake/glfw3/glfw3ConfigVersion.cmake
-- Installing: /usr/local/lib/cmake/glfw3/glfw3Targets.cmake
`-- Installing: /usr/local/lib/cmake/glfw3/glfw3Targets-noconfig.cmake
-- Installing: /usr/local/lib/pkgconfig/glfw3.pc
```

## GLEW

> The OpenGL Extension Wrangler Library (GLEW) is a cross-platform open-source C/C++ extension loading library.

OpenGL扩展库是个简单的工具，用于帮助C/C++开发者初始化扩展（OpenGL扩展功能）并书写可移植的应用程序。GLEW当前支持各种各样的操作系统，包含Windows，Linux，Darwin，Irix与Solaris。

```bash
x@x:~/cppProj/depends$ git clone git@github.com:nigels-com/glew.git

x@x:~/cppProj/depends/glew$ sudo make install
install -d -m 0755 "/usr/local/include/GL"
install -m 0644 include/GL/wglew.h "/usr/local/include/GL/"

or:
sudo apt-get install libglew-dev
```

## GLM 矩阵库

[http://glm.g-truc.net](http://glm.g-truc.net)

[Tags · g-truc/glm · GitHub](https://github.com/g-truc/glm/tags)

> OpenGL Mathematics (GLM) is a header only C++ mathematics library for graphics software based on the OpenGL Shading Language (GLSL) specifications.
> GLM provides classes and functions designed and implemented with the same naming conventions and functionality than GLSL so that anyone who knows GLSL, can use GLM as well in C++.

GLM是OpenGL Mathematics的缩写，它是一个只有头文件的库，也就是说我们只需包含对应的头文件就行了，不用链接和编译。GLM可以在它们的网站上下载。把头文件的根目录复制到你的includes文件夹，然后你就可以使用这个库了。

```bash
x@x:~/cppProj/depends$ git clone git@github.com:g-truc/glm.git
x@x:~/cppProj/depends/glm$ mkdir build
x@x:~/cppProj/depends/glm$ cd build/

x@x:~/cppProj/depends/glm/build$ cmake ..
x@x:~/cppProj/depends/glm/build$ make
x@x:~/cppProj/depends/glm/build$ sudo make install
```

```bash
[100%] Built target test-perf_vector_mul_matrix

Install the project...
-- Install configuration: ""

-- Installing: /usr/local/include/glm
-- Installing: /usr/local/include/glm/mat4x2.hpp
-- Installing: /usr/local/include/glm/integer.hpp
-- Installing: /usr/local/include/glm/mat3x3.hpp

-- Installing: /usr/local/include/glm/gtc
-- Installing: /usr/local/include/glm/gtc/matrix_inverse.hpp
-- Installing: /usr/local/include/glm/gtc/epsilon.inl
-- Installing: /usr/local/include/glm/gtc/bitfield.hpp

-- Installing: /usr/local/include/glm/glm.hpp
-- Installing: /usr/local/include/glm/exponential.hpp
-- Installing: /usr/local/include/glm/packing.hpp

-- Installing: /usr/local/include/glm/gtx
-- Installing: /usr/local/include/glm/gtx/intersect.hpp
-- Installing: /usr/local/include/glm/gtx/dual_quaternion.hpp

-- Installing: /usr/local/include/glm/mat4x3.hpp
-- Installing: /usr/local/include/glm/vector_relational.hpp
-- Installing: /usr/local/include/glm/mat2x2.hpp
-- Installing: /usr/local/include/glm/vec4.hpp

-- Installing: /usr/local/include/glm/detail
-- Installing: /usr/local/include/glm/detail/type_vec2.hpp
-- Installing: /usr/local/include/glm/detail/func_integer.inl

-- Installing: /usr/local/include/glm/ext.hpp
-- Installing: /usr/local/include/glm/vec2.hpp
-- Installing: /usr/local/include/glm/geometric.hpp

-- Installing: /usr/local/include/glm/simd
-- Installing: /usr/local/include/glm/simd/packing.h
-- Installing: /usr/local/include/glm/simd/exponential.h

-- Installing: /usr/local/include/glm/mat2x4.hpp
-- Installing: /usr/local/include/glm/vec3.hpp

-- Installing: /usr/local/include/glm/ext
-- Installing: /usr/local/include/glm/ext/vector_double2_precision.hpp
-- Installing: /usr/local/include/glm/ext/quaternion_transform.hpp

-- Installing: /usr/local/include/glm/mat4x4.hpp
-- Installing: /usr/local/include/glm/common.hpp
-- Installing: /usr/local/include/glm/mat3x4.hpp
-- Installing: /usr/local/include/glm/fwd.hpp

-- Installing: /usr/local/lib/cmake/glm/glmConfig.cmake
-- Installing: /usr/local/lib/cmake/glm/glmConfigVersion.cmake
```

## GLAD 图像加载

[https://github.com/Dav1dde/glad](https://github.com/Dav1dde/glad)

[http://glad.dav1d.de](http://glad.dav1d.de/)  

> Multi-Language Vulkan/GL/GLES/EGL/GLX/WGL Loader-Generator based on the official specs.

GLAD的配置与大多数的开源库有些许的不同，GLAD使用了一个[在线服务](http://glad.dav1d.de/)。在这里我们能够告诉GLAD需要定义的OpenGL版本，并且根据这个版本加载所有相关的OpenGL函数。

打开GLAD的[在线服务](http://glad.dav1d.de/)，将语言(Language)设置为**C/C++**，在API选项中，选择**3.3**以上的OpenGL(gl)版本。之后将模式(Profile)设置为**Core**，并且保证选中了**生成加载器**(Generate a loader)选项。现在可以先（暂时）忽略扩展(Extensions)中的内容。都选择完之后，点击**生成**(Generate)按钮来生成库文件。

GLAD现在应该提供给你了一个zip压缩文件，包含两个头文件目录，和一个**glad.c**文件。将两个头文件目录（**glad**和**KHR**）复制到你的**Include**文件夹中（或者增加一个额外的项目指向这些目录），并添加**glad.c**文件到你的工程中。

Ubuntu22.04 LTS 本机生成的地址:
[https://glad.dav1d.de/#language=c&specification=gl&api=gl%3D4.6&api=gles1%3D1.0&api=gles2%3D3.2&api=glsc2%3D2.0&profile=compatibility&loader=on](https://glad.dav1d.de/#language=c&specification=gl&api=gl%3D4.6&api=gles1%3D1.0&api=gles2%3D3.2&api=glsc2%3D2.0&profile=compatibility&loader=on)

经过前面的这些步骤之后，你就应该可以将以下的指令加到你的文件顶部了：

```c
#include <glad/glad.h> 
```

将生成的文件复至系统目录下:

```bash
x@x:~/cppProj/depends/glad/include$ sudo cp -r . /usr/local/include/

x@x:~/cppProj/depends/glad/src$ sudo cp -r . /usr/local/include/
```

## ASSIMP 3D模型加载

[http://assimp.org/](http://assimp.org/)

[https://github.com/assimp/assimp](https://github.com/assimp/assimp)  

> Open Asset Import Library (assimp)
> A library to import and export various 3d-model-formats including scene-post-processing to generate missing render data.

`git clone git@github.com:assimp/assimp.git`

ssimp可以导入几十种不同格式的模型文件（同样也可以导出部分模型格式）。只要Assimp加载完了模型文件，我们就可以从Assimp上获取所有我们需要的模型数据。Assimp把不同的模型文件都转换为一个统一的数据结构，所有无论我们导入何种格式的模型文件，都可以用同一个方式去访问我们需要的模型数据。

[https://learnopengl-cn.github.io/03%20Model%20Loading/01%20Assimp/](https://learnopengl-cn.github.io/03%20Model%20Loading/01%20Assimp/)

一个非常流行的模型导入库是[Assimp](http://assimp.org/)，它是**Open Asset Import Library**（开放的资产导入库）的缩写。Assimp能够导入很多种不同的模型文件格式（并也能够导出部分的格式），它会将所有的模型数据加载至Assimp的通用数据结构中。当Assimp加载完模型之后，我们就能够从Assimp的数据结构中提取我们所需的所有数据了。由于Assimp的数据结构保持不变，不论导入的是什么种类的文件格式，它都能够将我们从这些不同的文件格式中抽象出来，用同一种方式访问我们需要的数据。

当使用Assimp导入一个模型的时候，它通常会将整个模型加载进一个**场景**(Scene)对象，它会包含导入的模型/场景中的所有数据。Assimp会将场景载入为一系列的节点(Node)，每个节点包含了场景对象中所储存数据的索引，每个节点都可以有任意数量的子节点

- ubuntu安装assimp 方式1:
  
  ```bash
  x@x:~/cppProj/depends/$ git clone git@github.com:assimp/assimp.git
  x@x:~/cppProj/depends/assimp$ mkdir build
  x@x:~/cppProj/depends/assimp$ cd build/
  x@x:~/cppProj/depends/assimp/build$ cmake ..
  x@x:~/cppProj/depends/assimp/build$ make
  x@x:~/cppProj/depends/assimp/build$ sudo make install
  ```

```bash
x@x:~/cppProj/depends/assimp/build$ sudo make install
Install the project...
-- Install configuration: ""
-- Installing: /usr/local/lib/cmake/assimp-5.2/assimpConfig.cmake
-- Installing: /usr/local/lib/cmake/assimp-5.2/assimpConfigVersion.cmake
-- Installing: /usr/local/lib/cmake/assimp-5.2/assimpTargets.cmake
-- Installing: /usr/local/lib/cmake/assimp-5.2/assimpTargets-noconfig.cmake

-- Installing: /usr/local/lib/pkgconfig/assimp.pc

-- Installing: /usr/local/lib/libassimp.so.5.2.0
-- Installing: /usr/local/lib/libassimp.so.5
-- Installing: /usr/local/lib/libassimp.so

-- Installing: /usr/local/include/assimp/anim.h
-- Installing: /usr/local/include/assimp/Compiler/pstdint.h

-- Installing: /usr/local/bin/assimp
-- Set runtime path of "/usr/local/bin/assimp" to ""
```

- ubuntu安装assimp 方式2:
  ubuntu有库支持，在软件中心或者命令行下安装libassimp-dev,libassimp３,assimp-utils
  
  ```bash
  sudo apt-get install libassimp-dev
  sudo apt-get install libassipm3
  sudo apt-egt install assimp-utils
  ```

## SOIL 图像库

[https://github.com/SpartanJ/SOIL2](https://github.com/SpartanJ/SOIL2)

> SOIL2 is a tiny C library used primarily for uploading textures into OpenGL.
> SOIL2 is a fork of the Jonathan Dummer's [Simple OpenGL Image Library](https://web.archive.org/web/20200728145723/http://lonesock.net/soil.html).
> SOIL2 is a tiny C library used primarily for uploading textures into OpenGL. It is based on stb_image, the public domain code from Sean Barrett.
> SOIL2 extended stb_image to DDS files, and to perform common functions needed in loading OpenGL textures.
> SOIL2 can also be used to save and load images in a variety of formats (useful for loading height maps, non-OpenGL applications, etc.)

[https://learnopengl-cn.github.io/legacy/](https://learnopengl-cn.github.io/legacy/)
SOIL是简易OpenGL图像库(Simple OpenGL Image Library)的缩写，它支持大多数流行的图像格式，使用起来也很简单，你可以从他们的[主页](http://www.lonesock.net/soil.html)下载。像其它库一样，你必须自己生成.lib。你可以使用/projects文件夹内的任意一个解决方案(Solution)文件（不用担心他们的Visual Studio版本太老，你可以把它们转变为新的版本，这一般是没问题的。译注：用VS2010的时候，你要用VC8而不是VC9的解决方案，想必更高版本的情况亦是如此）来生成你自己的.lib文件。你还要添加src文件夹里面的文件到你的includes文件夹；添加`SOIL.lib`到你的链接器选项，并在你代码文件的开头加上`#include <SOIL.h>`。

https://blog.csdn.net/HHD_HHD/article/details/118165073

# stb 图像库

[stb](https://github.com/nothings/stb)

[stb_image.h](https://github.com/nothings/stb/blob/master/stb_image.h)

> single-file public domain (or MIT licensed) libraries for C/C++
> stb single-file public domain libraries for C/C++
> 
> **stb_image.h**  image loading/decoding from file/memory: JPG, PNG, TGA, BMP, PSD, GIF, HDR, PIC

https://learnopengl-cn.github.io/01%20Getting%20started/06%20Textures/

```cpp
#define STB_IMAGE_IMPLEMENTATION
#include "stb_image.h"
```

```bash
x@x:~/cppProj/depends$ git clone git@github.com:nothings/stb.git
x@x:~/cppProj/depends$ cd stb/
x@x:~/cppProj/depends/stb$ sudo mkdir /usr/local/include/stb
x@x:~/cppProj/depends/stb$ sudo cp -r . /usr/local/include/stb/
```

### 模型下载:

http://tf3dm.com/3d-model/crysis-2-nanosuit-2-97837.html
[http://tf3dm.com/](http://tf3dm.com/)   
模型下载... obj格式 等

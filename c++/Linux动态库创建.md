april@april-Ubuntu:~/Documents/source/build$ `cmake ..`

-- The C compiler identification is GNU 10.2.0

-- The CXX compiler identification is unknown

-- Check for working C compiler: /usr/bin/cc

-- Check for working C compiler: /usr/bin/cc -- works

-- Detecting C compiler ABI info

-- Detecting C compiler ABI info - done

-- Detecting C compile features

-- Detecting C compile features - done

CMake Error at CMakeLists.txt:3 (PROJECT):

No CMAKE_CXX_COMPILER could be found.

Tell CMake where to find the compiler by setting either the environment

variable "CXX" or the CMake cache entry CMAKE_CXX_COMPILER to the full path

to the compiler, or to the compiler name if it is in the PATH.

`sudo apt install gcc`

`sudo apt install g++`

april@april-Ubuntu:~/Documents/source/build$`cmake ..`

-- The CXX compiler identification is GNU 10.2.0

-- Check for working CXX compiler: /usr/bin/c++

-- Check for working CXX compiler: /usr/bin/c++ -- works

-- Detecting CXX compiler ABI info

-- Detecting CXX compiler ABI info - done

-- Detecting CXX compile features

-- Detecting CXX compile features - done

-- Configuring done

-- Generating done

-- Build files have been written to: /home/april/Documents/source/build

april@april-Ubuntu:~/Documents/source/build$

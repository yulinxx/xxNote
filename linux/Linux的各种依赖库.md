- Could NOT find Jasper (missing: JASPER_LIBRARIES JASPER_INCLUDE_DIR)
  https://askubuntu.com/questions/1079956/what-is-the-library-to-be-installed-for-jasper-h-header-file

```cmd
wget http://archive.ubuntu.com/ubuntu/pool/main/j/jasper/libjasper-dev_1.900.1-debian1-2.4ubuntu1.3_amd64.deb
wget http://archive.ubuntu.com/ubuntu/pool/main/j/jasper/libjasper1_1.900.1-debian1-2.4ubuntu1.3_amd64.deb

sudo apt-get install ./libjasper-dev_1.900.1-debian1-2.4ubuntu1.3_amd64.deb ./libjasper1_1.900.1-debian1-2.4ubuntu1.3_amd64.deb
```

No package 'minizip' found
`sudo apt install libminizip-dev`



`sudo apt-get install bison`
GNU bison 是属于 GNU 项目的一个语法分析器生成器。(vcpkg install opencv 的时候需要)
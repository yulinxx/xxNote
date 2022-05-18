### GIT

`sudo apt install git`

`ssh-keygen -t rsa -C "xx@ubuntu.com"`
`git config --global user.name "xx"`
`git config --global user.email "xx@ubuntu.com"`

在新电脑上使用Live USB，进入使用ubuntu。进入试用Ubuntu后，先获取root权限，sudopasswd root，更改root密码后，然后切换root用户。su root。

#### 修改**ROOT**密码

sudo passwd root

### VSCode 镜像

vscode.cdn.azure.cn/stable/

vscode.cdn.azure.cn/stable/dfd34e8260c270da74b5c2d86d61aee4b6d56977/code_1.66.2-1649664567_amd64.deb

env
env命令是environment的缩写，用于列出所有的环境变量；

export
单独使用export命令也可以像env列出所有的环境变量，不过export命令还有其他额外的功能；

echo $PATH
echo $PATH用于列出变量PATH的值，里面包含了已添加的目录。

设置环境变量的方法

- 1.1 临时设置
  export PATH=/home/x/share/usr/local/arm/3.4.1/bin:$PATH

- 1.2 当前用户的全局设置
  打开~/.bashrc，添加行：
  `export PATH=/home/x/share/usr/local/arm/3.4.1/bin:$PATH`
  使生效： `source .bashrc`

- 1.3 所有用户的全局设置
  `vim /etc/profile`
  在里面加入：
  `export PATH=/home/x/share/usr/local/arm/3.4.1/bin:$PATH`
  使生效 `source /etc/profile`

### 修改用户 文档,图片,下载等 默认文件夹

`~/.config/usr-dirs.dirs`

## 初装软件

```bash
sudo apt-get install pkg-config

sudo apt install build-essential build-essential libxmu-dev libxi-dev libgl-dev libgl1-mesa-dev libsqlite3-dev libglew-dev openssl libssl-dev libssl-dev libglew-dev glew-utils gengetopt libimlib2-dev libglm-dev vim git cmake cmake-gui tree curl zip unzip tar flameshot virtualenv virtualenvwrapper net-tools gitg filezilla timeshift python3-pip gnome-tweaks finger stacer ibus-rime gnome-software gnome-shell-extension-manager copyq blender meld audacious wireshark uget kdenlive nomacs qalculate-gtk vulkan-tools docker.io docker-compose python-virtualenv telegram-desktop gimp blender vlc mpv kdenlive shotcut gnome-software
```

#### Qt

`sudo apt install libxkbcommon-dev libxinerama-dev libxcursor-dev`
`sudo apt-get install stacer`

Stacer 是一个开源的系统诊断和优化工具，使用 Electron 开发框架开发。它有一个优秀的用户界面，你可以清理缓存内存、启动应用、卸载不需要的应用、掌控后台系统进程。

`sudo apt install gnome-shell-extension-manager`

`sudo apt install finger`
finger命令用于查找并显示用户信息。 http://lnmp.ailinux.net/finger

`sudo apt-get install libatlas-base-dev`
OpenBLAS 是一个优化的 BLAS 库，基于 GotoBLAS2 1.13 BSD 版本。

BLAS（Basic Linear Algebra Subprograms 基础线性代数程序集）是一个应用程序接口（API）标准，用以规范发布基础线性代数操作的数值库（如矢量或矩阵乘法）。该程序集最初发布于 1979 年，并用于建立更大的数值程序包（如 LAPACK）。在高性能计算领域，BLAS 被广泛使用。例如，LINPACK 的运算成绩则很大程度上取决于 BLAS 中子程序 DGEMM 的表现。为提高性能，各軟硬件厂商则针对其產品对 BLAS 接口实现进行高度优化。

垃圾清理工具
`sudo apt install bleachbit`

`sudo apt-get install autojump`

### 输入法

- IBUS 安装五笔 输入法
  `sudo apt-get install ibus ibus-pinyin ibus-table-wubi`

- RIME 五笔 `sudo apt-get install ibus-rime`

https://blog.csdn.net/weixin_33868027/article/details/93036999
https://zhuanlan.zhihu.com/p/47329032

- Freetype

https://freetype.org/developer.html

git clone https://gitlab.freedesktop.org/freetype/freetype.git
git clone https://gitlab.freedesktop.org/freetype/freetype-demos.git

- VBox

sudo apt install virtualbox virtualbox-dkms virtualbox-qt virtualbox-ext-pack virtualbox-guest-additions-iso

Linux下检测 内存泄露 的工具 valgrind

https://valgrind.org/downloads/current.html

卸载snap `sudo apt autoremove --purge snapd`

安装gnome-software `sudo apt install gnome-software`

删除libreoffice `sudo apt-get remove --purge libreoffice-common`

### WPS

https://www.wps.cn/product/wpslinux

#### 删掉基本不用的自带软件

`sudo apt-get remove thunderbird totem rhythmbox empathy brasero simple-scan gnome-mahjongg aisleriot gnome-mines cheese transmission-common gnome-orca gnome-sudoku`

`sudo apt-get remove onboard deja-dup`

清理没有被依赖的软件包
`sudo apt autoremove`



**Alt + F2 输入 r 重启桌面**



#### ubuntu 安装使用eigen3 (两种方式)

https://ppipp.blog.csdn.net/article/details/100653731

Linux 安装Boost - 知乎

https://zhuanlan.zhihu.com/p/345522404

### BOOST

下载好了以后，解压 .bz2 文件

tar -jxvf xx.tar.bz2

解压之后，进入解压目录，执行：

./bootstrap.sh

sudo ./b2
sudo ./b2 install

step3：测试

#include
#include
using namespace std;
using namespace boost;
int fun(int x,int y){return x+y;}
int main(){
 int m=1;int n=2;
 cout<

编译：

g++ test.cpp -o test

最后执行的结果是 3

切换到cd /etc/profile.d目录下，使用超级用户创建文件boost.sh，里面添加如下内容

```bash
#!/bin/sh

BOOST_ROOT=/home/zbb/boost_1_66_0

BOOST_INCLUDE=/usr/local/include/boost

BOOST_LIB=/usr/local/lib

export BOOST_INCLUDE BOOST_LIB BOOST_ROOT
```

修改boost.sh的权限 sudo chmod +x boost.sh，执行source boost.sh

### 

### FreeType

git clone https://gitlab.freedesktop.org/freetype/freetype.git

cd builds

cmake ..

make

sudo make install

sudo apt install mesa-common-dev

20210827#_Ubuntu 20.04 优化_mob604756ef5a44的技术博客_51CTO博客

https://blog.51cto.com/u_15127558/4120146



#### Java

1下载Java tar 或 deb

https://www.oracle.com/java/technologies/downloads/

2.解压或安装

tar -zxvf jdk-8u211-linux-x64.tar.gz

或: sudo dpkg -i jdk-11.0.15_linux-x64_bin.deb

3.移动到自己想放的位置

##将文件从下载目录 挪到/usr/local/ install 下

sudo mv jdk1.8.0_171 /usr/local/install/jdk1.8

4.设置环境变量

sudo vim /etc/profile

export JAVA_HOME=/usr/local/jdk1.8

export JRE_HOME=${JAVA_HOME}/jre

export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib

export PATH=.:${JAVA_HOME}/bin:$PATH

deb安装则配置如下:

export JAVA_HOME=/usr/lib/jvm/jdk-11

export JRE_HOME=${JAVA_HOME}

export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib

export PATH=${JAVA_HOME}/bin:$PATH

5.使修改的配置立刻生效

source /etc/profile

6.检查是否安装成功

java -version





#### PIP设置源

x@x:~$ pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple



##### Ubuntu 安装FSearch

类似Windows上的everything

sudo add-apt-repository ppa:christian-boxdoerfer/fsearch-daily

sudo apt update

sudo apt install fsearch 或 sudo apt install fsearch-trunk





安装媒体解码器来播放 MP3、MPEG4 和其他格式媒体文件



### gnome 插件:

IBUS: Customize IBUS

特效: Burn My Windows

桌面指示器: Improved Workspace Indicator

GTK Title Bar

键盘大写/数字切换提示:Lock Keys

CPU内存等监视:Vitals

天气: OpenWeather

声音输出选择: Sound output device chooser

顶部状态栏透明: Transparent Top Bar

壁纸切换: wallpaper switcher

Top Bar

任务栏 透明

实现顶栏自动透明的插件：Transparent Top Bar (Adjustable transparency)

剪贴板工具：Clipboard indicator

关闭gnome的某某软件已准备：NoAnnoyance v2

去除顶栏的无障碍图标：Remove Accessibility

去除顶栏的无障碍图标：Remove Accessibility

大写锁定以及num状态开关提示：Lock Keys

将窗口上方的状态栏去掉 No title bar

cpu以及系统负载监测工具：Vitals

声音输入输出设备选择 Sound input & output device chooser

农历插件 Lunar Calendar

依赖:

sudo apt install gir1.2-lunardate-3.0

sudo apt install liblunar-date-3.0-1

显示拼音的解决:

sudo cp /usr/share/locale/zh_CN/LC_MESSAGES/lunar-date.mo /usr/share/locale/en_US/LC_MESSAGES/

---

#### 备份

Ubuntu如何备份和恢复系统 - CharyGao - 博客园
https://www.cnblogs.com/Chary/p/14957970.html

`sudo su`

`cd /`

`tar -jpcvf /home/x/ubuntu_`date +%Y%m%d_%H`.tar.bz2 --exclude=/tmp --exclude=/proc --exclude=/lost+found --exclude=/sys --exclude=/var/backups --exclude=/var/log --exclude=/var/tmp --exclude=/var/cache --exclude=/cdrom --exclude=/media --exclude=/mnt --exclude=/opt --exclude=/home --exclude=/home/x --exclude=/home/x/Downloads/ --exclude=/home/x/Install --exclude=/home/x/Pictures/ --exclude=/home/x/source --exclude=/home/x/.cache --exclude=/home/x/ubuntu_`date +%Y%m%d_%H`.tar.bz2 /`

`tar -jpcvf /home/x/ubuntu_`date +%Y%m%d_%H`.tar.bz2 --exclude=/tmp --exclude=/opt --exclude=/proc --exclude=/lost+found --exclude=/sys --exclude=/var/backups --exclude=/var/log --exclude=/var/tmp --exclude=/var/cache --exclude=/var/crash --exclude=/cdrom --exclude=/media --exclude=/mnt --exclude=/opt --exclude=/home --exclude=/home/x --exclude=/home/n --exclude=/home/p --exclude=/home/x/ubuntu_`date +%Y%m%d_%H`.tar.bz2`

和Windows不同，Linux不会限制root访问任何东西，你可以把分区上的所有东西都扔到一个TAR文件里去

首先成为root用户：
`sudo su`

然后进入文件系统的根目录(当然，如果你不想备份整个文件系统，你也可以进入你想要备份的目录，包括远程目录或者移动硬盘上的目录)：

`cd /`
`sudo tar -cvPzf /home/n/ubuntu20220421.tgz --exclude=/tmp --exclude=/opt --exclude=/proc --exclude=/lost+found --exclude=/sys --exclude=/var/backups --exclude=/var/log --exclude=/var/tmp --exclude=/var/cache --exclude=/var/crash --exclude=/cdrom --exclude=/media --exclude=/mnt --exclude=/opt --exclude=/home --exclude=/home/x --exclude=/home/n --exclude=/home/n / >> /home/n/ubuntu20220421_backup.log`

tar [-cvPzf] … 说明:

-c :建立一个压缩文件的参数指令
-v :压缩过程中显示文件
-P :(大写）可以使用绝对路径进行压缩
-z :采用‘gzip’压缩备份文件, 还可以用Bzip2来压缩文件(-j)，Bzip2比gzip的压缩率高，但是速度慢一些
-f :说明备份文件存放位置，在 f 之后要立即文件压缩名
–exclude FILE：在压缩的过程中，排除文件
-j参数调用bzip2来进行压缩文件
-p ：使用原文件的原来属性（属性不会依据使用者而变）
-P ：可以使用绝对路径来压缩！
-c ：建立一个压缩文件的参数指令(create 的意思)；
-v ：压缩的过程中显示文件！这个常用，但不建议用在背景执行过程！
-f ：使用档名，请留意，在 f 之后要立即接档名喔！不要再加参数！

使用下面的命令来恢复系统：
`tar xvpfz backup.tgz -C /`

如果你的档案文件是使用Bzip2压缩的，应该用：
`tar xvpjf backup.tar.bz2 -C /`

-x ：解开一个压缩文件的参数指令

-v ：压缩的过程中显示文件！这个常用，但不建议用在背景执行过程！

-p ：使用原文件的原来属性（属性不会依据使用者而变）

-P ：可以使用绝对路径来压缩

-f ：使用档名，请留意，在 f 之后要立即接档名喔！不要再加参数！

　　　例如使用『 tar -zcvfP tfile sfile』就是错误的写法，要写成

　　　『 tar -zcvPf tfile sfile』才对喔！

如果加 j 参数，则以 .tar.bz2 来作为附档名

-j ：是否同时具有 bzip2 的属性？亦即是否需要用 bzip2 压缩？

如果加 z 参数，则以 .tar.gz 或 .tgz 来代表 gzip 压缩过的 tar file ～

使用下面的命令来恢复系统：(/ 代表根目录)
`tar xvpfz backup.tgz -C /`

如果你的档案文件是使用Bzip2压缩的，应该用：
`tar xvpfj backup.tar.bz2 -C /`

注意：上面的命令会用档案文件中的文件覆盖分区上的所有文件。

执行恢复命令之前请再确认一下你所键入的命令是不是你想要的，执行恢复命令可能需要一段不短的时间。

恢复命令结束时，你的工作还没完成，别忘了重新创建那些在备份时被排除在外的目录：

```
mkdir proc
mkdir lost+found
mkdir mnt
mkdir sys
```

等等

当你重启电脑，你会发现一切东西恢复到你创建备份时的样子了！

/proc：一个虚拟文件系统，系统运行的每一个进程都会自动在这个目录下面创建一个进程目录。既然是系统自动创建，也就没必要备份的必要了。

/tmp：一个临时文件夹，系统的一些临时文件会放在这里。

/lost+found：系统发生错误时（比如非法关机），可以在这里找回一些丢失文件。

/media：多媒体挂载点，像u盘、移动硬盘、windons分区等都会自动挂载到这个目录下。

/mnt：临时挂载点，你可以自己挂载一些文件系统到这里。

/run：系统从启动以来产生的一些信息文件。

--------------------------

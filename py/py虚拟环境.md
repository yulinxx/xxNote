linux安装
`sudo apt install python-virtualenv`
使用方法


`x@x:~/pyProj$ virtualenv btqEnv`

`x@x:~/pyProj$ cd btqEnv`

`x@x:~/pyProj/btqEnv$ source ./bin/activate` 

`(btqEnv) x@x:~/pyProj/btqEnv$`



`virtualenv [虚拟环境名称]`



 如，创建**ENV**的虚拟环境 virtualenv ENVvirtualenv  -p (指定python版本, 可以省略)  ENV(创建名为env的虚拟环境)
启动虚拟环境
`cd ENVsource ./bin/activate`
注意此时命令行会多一个(ENV)，ENV为虚拟环境名称，接下来所有模块都只会安装到该目录中去。
退出虚拟环境
1deactivate

windows下搭建python虚拟环境

1.Python安装
官网地址  http://www.python.org/
验证安装：管理员身份运行cmd，输入python
验证pip是否随python安装成功：pip show pip
升级pip的命令：python -m pip install -U pip
安装pillow库：pip install pillow
卸载pillow库：pip uninstall pillow

【python】pip默认源更换为清华镜像(升级 pip 到最新的版本后再进行配置)
临时更换
pip install package -i https://pypi.tuna.tsinghua.edu.cn/simple
永久使用
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple

2.IDLE安装（PyCharm专业版）
官网地址 https://www.jetbrains.com
淘宝买专业版账号
账号：1323040114
密码：wey2021wey

3.建立virtualenv 虚拟环境
管理员身份运行cmd
安装：
pip install virtualenv
可以在命令行界面中验证安装：
where virtualenv

创建专门的虚拟环境文件夹：
mkdir d:\Python_virtualenvs

不指定python版本,使用默认python版本，创建名为django_env的虚拟环境
 virtualenv  D:/sm/pyProj/pythonEnvs/django_env

例：指定版本创建一个for_django虚拟环境：
virtualenv –p C:/Users/niesi/AppData/Local/Programs/Python/Python38/python.exe  D:/sm/pyProj/pythonEnvs/django_env
注：-p： 指定你要虚拟的Python版本，这里选择了本地的python3.8

4.使用虚拟环境
进入你要使用的虚拟环境的目录下的script文件夹，运行activate命令 (按Tab键自动完成)
.\activate
pip install django

切换至指定目录，新建一个工程即可

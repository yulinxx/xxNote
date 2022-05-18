### git   放弃 本地修改 撤销提交

🙈🐵🐸🐽🐷🙊🐒🐔🐧🐧🐦🦉[git常见用法和问题处理笔记](https://blog.csdn.net/weixin_41707419/article/details/123766077)

- -----------❤️  未使用 git add 缓存代码时
  `git checkout -- <filepathname>`

- -----------🐤 已经使用了 git add 缓存了代码
  `git reset HEAD <filepathname>`

- -----------🌸 已经用 git commit 提交了代码
  `git reset --hard HEAD^ `

#### Github进行fork后如何与原仓库同步

```
#添加upstream
git remote add upstream xxxx.git
#检查是否成功
git remote -v 
#将未提交的进行提交
git push origin master
#抓取原仓库的更新
git fetch upstream
#合并远程的master分支
git merge upstream/master
#再执行命令 git push 把本地仓库向fork的仓库推送修改
git push  origin master
```

#### git 加tag

```bash
git tag -a v0.0.1 -m "v0.0.1发布"
git push origin v0.0.1
```

在控制台打印出当前仓库的所有标签：git tag
搜索符合模式的标签：`git tag -l 'v0.0.*'`
创建附注标签：`git tag -a v0.0.1 -m "v0.0.1发布"`
删除标签：`git tag -d v0.0.1`

查看标签的版本信息：`git show v0.0.1`
指向打v0.0.2标签时的代码状态：`git checkout v0.0.2`
将v0.0.1标签提交到git服务器：`git push origin v0.0.1`
将本地所有标签一次性提交到git服务器：`git push origin –tags`

https://www.jianshu.com/p/cdd80dd15593

tag主要用于发布版本的管理,一个版本发布之后,我们可以为git打上 v.1.0.1 v.1.0.2 ...这样的标签。

tag 对应某次commit, 是⼀个点，是不可移动的。
branch 对应⼀系列commit，是很多点连成的⼀根线，有⼀个HEAD 指针，是可以依靠 HEAD 指针移动的。
所以，两者的区别决定了使⽤⽅式，改动代码⽤ branch ,不改动只查看⽤ tag。  

### git 冲突:

[Your local changes to the following files would be overwritten by mergegit](https://blog.csdn.net/qq_41018861/article/details/118442711)

- 保留本地的方式修改

```bash
# 备份当前的工作区的内容, 让工作区保证和上次提交的内容一致
git stash 
# 拉取最新的代码
git pull
# 从Git栈中读取最近一次保存的内容，恢复工作区的相关内容
git stash pop
```

- 放弃本地修改
  
  只保留服务器端代码，则直接回退到上一个版本，再进行pull：

```bash
git reset --hard
git pull origin master
```

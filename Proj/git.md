### git   放弃 本地修改 撤销提交

🙈🐵🐸🐽🐷🙊🐒🐔🐧🐧🐦🦉🦅
-----------❤️
未使用 git add 缓存代码时
git checkout -- <filepathname>

-----------🐤
已经使用了 git add 缓存了代码
git reset HEAD <filepathname>

-----------🌸
已经用 git commit 提交了代码
git reset --hard HEAD^ 

————————————————
https://blog.csdn.net/weixin_41707419/article/details/123766077

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

https://www.jianshu.com/p/cdd80dd15593

tag主要用于发布版本的管理,一个版本发布之后,我们可以为git打上 v.1.0.1 v.1.0.2 ...这样的标签。

tag 对应某次commit, 是⼀个点，是不可移动的。
branch 对应⼀系列commit，是很多点连成的⼀根线，有⼀个HEAD 指针，是可以依靠 HEAD 指针移动的。
所以，两者的区别决定了使⽤⽅式，改动代码⽤ branch ,不改动只查看⽤ tag。

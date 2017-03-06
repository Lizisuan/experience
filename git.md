# git

## 目录

- [开始 init](#init)
- [克隆 clone](#clone)
- [管理主机 remote](#remote)
- [分支 branch](#branch)
- [取更新 fetch](#fecth)
- [上传 push](#push)
- [拉取 pull](#pull)
- [配置.gitignore文件](#ignore)

### init

* git init

* git remote add origin(主机名称) url(链接)

* git status

* git add -A

* git commit -m '提交说明'

* git push origin(主机名) master(分支名) , 默认分支上传

### clone

> 克隆会自动与目标地址进行关联

* git clone url , 克隆目标地址

* git clone url 本地目录名 , 克隆目标地址到本地的目标文件夹

* git clone -o 主机名 url , 原本默认命名为origin的主机名进行指定命名

### remote

* git remote , 列出所有远程主机

* git remote -v , 看远程主机的网址

* git remote show 主机名 , 查看主机的详细信息

* git remote add 主机名 网址 , 添加远程主机

* git remote rm 主机名 , 删除远程主机

* git remote rename 原主机名 新主机名 , 改远程主机名

### branch

* git branch -r , 查看远程分支

* git branch -a , 查看所有分支

* git branch 分支名 , 但还处在原分支

* git checkout -b 分支名 , 创建并切换分支

* git checkout 分支名 , 切换分支

* git branch --set-upstream master 远程主机名/远程分支名 , 本地的mster与远程的指定分支建立 "追踪" 关系 

### fetch

> 该命令通常来查看其他人的进程, 取回的代码对你本地的没有任何影响

* git fetch 远程主机名 , 取回远程主机的更新

* git fetch 远程主机名 分支名 , 取回特定分支的更新

取回的更新,在本地要用 "远程主机名/分支名" 的形式来读取 , 例如 origin 主机的 master , 就要用 origin/master

如果要合并远程分支

* git merge origin/master , 在当前分支上 , 合并origin/master

* git rebase origin/master , 同上


### push

* git push origin(主机名) master(分支名) , 默认分支上传

### pull

> 通常用于取回远程主机的更新, 再与本地的指定分支合并 

* git pull <远程主机名> <远程分支名>:<本地分支名> , 取回主机的更新并且与本地合并

* git pull <远程主机名> <远程分支名> , 与本地的master分支合并可以省略本地分支名

* git pull <远程主机名> , 若远程和本地存在"追踪"的关系 , 可省略后面的参数

* git pull -p 本地删除远程已经删除了的分支 , 相当于 下面的命令
> git fetch --prune origin
> git fetch -p


当本地库有修改, 但是没有提交到git库中, pull命令会提示

> error: Your local changes to the following files would be overwritten by merge

解决方法:

1. git checkout -f , 撤销自己对本地的修改 
2. git stash , 暂时搁置当前的本地修改, 倒退到改动之前的状态来进行pull, 然后撤销搁置 : git stash pop
3. git  reset --hard origin/master  强制覆盖


### ignore

* touch .gitignore , 用git工具创建只有后缀的文件

1. build/ , 忽略build文件夹
2. !a.html , 这个文件不会被忽略
3. *.html , 忽略所有html文件
4. *.[0a] , 忽略所有以 ".o" 或 ".a" 后缀的文件
...
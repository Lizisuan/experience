# git

## 目录

- [对一个新项目进行管理](#init)
- [克隆一个项目 继续开发](#clone)
- [创建新的分支](#branch)
- [其他命令](#other)
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

* git clone url

* git status

...

### branch

* git branch 分支名 , 但还处在原分支

* git checkout -b 分支名 , 创建并切换分支

* git checkout 分支名 , 切换分支

### other

* git push -u origin master -f , 强制覆盖
* git pull <远程主机名> <远程分支名>:<本地分支名> , 取回主机的更新并且与本地合并

### ignore

* touch .gitignore , 用git工具创建只有后缀的文件

1. build/ , 忽略build文件夹
2. !a.html , 这个文件不会被忽略
3. *.html , 忽略所有html文件
4. *.[0a] , 忽略所有以 ".o" 或 ".a" 后缀的文件
...
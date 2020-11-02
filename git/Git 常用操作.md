#  Git 常用操作

## 基本操作

```shell
git init                      #初始化项目
git add 文件名                #添加指定文件
git add .                     #添加所以文件
git commit -m "提交注释"       #添加一个版本
git log                       #查看历史版本（不包含回退部分的）
git reflog                    #查看历史版本（详细 ，包含回退部分的版本）
git reset --hard 提交的版本号  #回退到指定的历史版本
git check out                 #

git reset --soft
git reset head
git reset --mix

git rm file                  #删除本地及仓库中的文件
git rm --cached file         #删除仓库中的文件，保留本地的文件 如果使用 git rm --cached 删除了仓库中的文件，而且后续不想跟踪此文件，只需将此文件加入 .gitignore 中即可。

# gitlab 自己创建代码托管（基于linux）
```

## 分支操作

### 删除远程分支

```shell
git branch -a #查看已有的本地及远程分支
git push origin --delete dev  #删除远程分支
git branch -d dev #删除本地分支
git remote update origin --prune(-p) #更新远程分支列表
```

### 推送到远程

```shell

git remote add origin ....... # 添加git地址
git push origin dev  推送到线上dev分支
git pull origin dev  获取线上的dev分支

提交的代码晚于github行的代码，会有错误提示，叫你重新拉取代码
拉取代码会提示你合并代码

git pull origin dev =  git fetch origin dev  
                    +  git merge origin/dev


git pull 的代码会有分叉（有忘记提交的代码的情况：比如在公司开的代码已经commit 但是忘提交，回家继续开发提交，第二天到都公司pull代码就会出现分叉）

下面的方法不会有分叉
git fetch origin dev
git rebase origin/dev   #rebase 保持提交记录的整洁
```



### git本地库同时关联多个远程仓库

```shell
// 设置多个远程仓库
git remote add github ....... # 添加git地址
git remote add gitee ....... # 添加gitee地址
git push github master  # 推送到线上github仓库
git push gitee master  # 推送到线上gitee仓库

```



### 暂存以及复原当前工作环境  [git stash 常用命令](https://www.jianshu.com/p/0cde1c60c101)

```shell

git stash save '需要暂存代码备注' #暂存当前工作环境
git stash list  # 查看暂存区列表
git stash apply stash@{0} #应用某个存储,但不会把存储从存储列表中删除，默认使用第一个存储,即stash@{0}，如果要使用其他个，git stash apply stash@{$num} ， 比如第二个：git stash apply stash@{1} 
git stash pop stash@{0} #命令恢复之前缓存的工作目录，将缓存堆栈中的对应stash删除，并将对应修改应用到当前的工作目录下,默认为第一个stash,即stash@{0}，如果要应用并删除其他stash，命令：git stash pop stash@{$num} ，比如应用并删除第二个：git stash pop stash@{1}
git stash drop stash@{0} #丢弃stash@{$num}存储，从列表中删除这个存储
git stash clear #删除所有缓存的stash
git stash show stash@{0} #显示做了哪些改动，默认show第一个存储,如果要显示其他存贮，后面加stash@{$num}，比如第二个 git stash show stash@{1}

```

### 




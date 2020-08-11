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

# gitlab 自己创建代码托管（基于linux）
```

## 分支操作

### 删除远程分支

```shell
git branch -a #查看已有的本地及远程分支
git push origin --delete dev  #删除远程分支
git branch -d dev #删除本地分支
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




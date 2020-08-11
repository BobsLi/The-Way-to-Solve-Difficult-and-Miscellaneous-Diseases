# git

##### 1. windows下git下载失败或者很慢的解决方法  
   (解决windows下载git失败情况
)[https://blog.csdn.net/huobaopaopao/article/details/83417199] 

##### 2. git克隆项目失败 
   + 错误码1045（文件太大） 
     ```
     方法一：
     采用SSH克隆（这个亲测有用）
     方法2：
     扩大缓存
     #首先设置通信缓存大小
      git config http.postBuffer 524288000  
     #然后把缓存清除
      git filter-branch --index-filter 'git rm -r --cached --ignore-unmatch <file/dir>' HEAD
     ```

##### 3. Git管理代码：标签使用 [https://www.jianshu.com/p/36384e7eccc1](https://www.jianshu.com/p/36384e7eccc1)

##### 4. Git 配置 Github、Gitlab、Gitee 多平台 SSH-Key [https://www.jianshu.com/p/f039c0e954f5](https://www.jianshu.com/p/f039c0e954f5)  [https://gitee.com/help/articles/4229#article-header0](https://gitee.com/help/articles/4229#article-header0)

##### 5. git本地库同时关联多个远程仓库[https://www.liaoxuefeng.com/wiki/896043488029600/1163625339727712](https://www.liaoxuefeng.com/wiki/896043488029600/1163625339727712)
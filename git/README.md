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

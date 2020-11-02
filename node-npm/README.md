# node
1. npm重新指定 registry 来解决 npm 安装速度慢的问题 (设置国内镜像) 
    ```bash
    npm config set registry https://registry.npm.taobao.org npm info underscore
    ```
   (设置npm的registry)[https://www.cnblogs.com/jianxian/p/12559469.html]

2. 查询npm全局安装包路径
	```bash
	npm root -g
	```
	
3. npm删除项目所有依赖和清缓存
	清缓存：
	
	```bash
	npm cache verify
	```
	或者
	```bash
	npm cache clean --force
	```
	
	删除项目所有依赖：
	```bash
	npm uninstall *
	```
	

4. 一键更新package.json中所有模块的版本 (一键更新package.json中所有模块的版本)[https://www.jianshu.com/p/ce9a46ae3a03]

   ```
   // 安装
   npm install npm-check-updates -g 
   
   // 使用
   npm-check-updates 或者 ncu
   ```

5. npm 安装chromedriver 报错 (vuejs npm chromedriver 报错)[https://www.cnblogs.com/web-record/p/9450709.html]
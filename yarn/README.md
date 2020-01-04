#### 用yarn升级vue-cli失败
(1) 先删除之前的vue-cli
```bash
	yarn global remove @vue/cli
```
(2) 清除yarn缓存 
```bash
	yarn cache clean
```
(3) 重新安装新的vue-cli
```bash
	yarn global add @vue/cli
```
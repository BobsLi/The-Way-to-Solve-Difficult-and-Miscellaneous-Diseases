##### vscode
1. vscode代码保存时自动格式化成ESLint风格（支持VUE） ，参考 [vscode代码保存时自动格式化成ESLint风格](https://www.jianshu.com/p/68dbca4a9a11)  
2. 同步插件配置到其他电脑 参考[使用Settings Sync同步你的vscode配置](https://www.jianshu.com/p/3470c040c050)  
7b5d2f5281fa1cf840634889c913f4a456e9752c
3. 生成vue代码片段,参考[vscode设置vue代码片段](https://segmentfault.com/a/1190000015336481) 
4. 配置vscode支持webpack的alias，参考[配置vscode支持webpack的alias](https://www.jianshu.com/p/552eac30ddbf)

##### vue router
1. 当角色权限改变时，需要删除之前角色的动态添加的路由？  
   解决方法：所有的 vue-router 注册的路由信息都是存放在matcher之中的，所以当我们想清空路由的时候，我们只要新建一个空的Router实例，将它的matcher重新赋值给我们之前定义的路由就可以了，详情[Detail see](https://github.com/vuejs/vue-router/issues/1234#issuecomment-357941465)

##### element ui
1. el-input如果需要处理键盘操作需要加上.native    
   eg: <el-input v-model="todo" @keyup.enter.native="addTodo"></el-input>  
2. el-checkbox,如果需要在不同地方用同一个checkbox渲染，那需要绑定同样的key值
#### vscode
1. vscode代码保存时自动格式化成ESLint风格（支持VUE） ，参考 [vscode代码保存时自动格式化成ESLint风格](https://www.jianshu.com/p/68dbca4a9a11)  
2. 同步插件配置到其他电脑 参考[使用Settings Sync同步你的vscode配置](https://www.jianshu.com/p/3470c040c050)  
7b5d2f5281fa1cf840634889c913f4a456e9752c
3. 生成vue代码片段,参考[vscode设置vue代码片段](https://segmentfault.com/a/1190000015336481) 
4. 配置vscode支持webpack的alias，参考[配置vscode支持webpack的alias](https://www.jianshu.com/p/552eac30ddbf)

#### vue
1. 不翻墙情况下谷歌浏览器安装vue插件(Vue Devtools)
   [Chrome 浏览器安装Vue插件方法](https://www.cnblogs.com/wbl001/p/11063613.html) 
2. 设置全局scss变量 
有的时候你想要向 webpack 的预处理器 loader 传递选项。你可以使用 vue.config.js 中的 css.loaderOptions 选项。比如你可以这样向所有 Sass/Less 样式传入共享的全局变量：
```bash
// vue.config.js
module.exports = {
  css: {
    loaderOptions: {
      // 给 sass-loader 传递选项
      sass: {
        // @/ 是 src/ 的别名
        // 所以这里假设你有 `src/variables.sass` 这个文件
        data: `@import "~@/variables.sass"`
      },
      // 默认情况下 `sass` 选项会同时对 `sass` 和 `scss` 语法同时生效
      // 因为 `scss` 语法在内部也是由 sass-loader 处理的
      // 但是在配置 `data` 选项的时候
      // `scss` 语法会要求语句结尾必须有分号，`sass` 则要求必须没有分号
      // 在这种情况下，我们可以使用 `scss` 选项，对 `scss` 语法进行单独配置
      scss: {
        data: `@import "~@/variables.scss";`
      },
      // 给 less-loader 传递 Less.js 相关选项
      less:{
        // http://lesscss.org/usage/#less-options-strict-units `Global Variables`
        // `primary` is global variables fields name
        globalVars: {
          primary: '#fff'
        }
      }
    }
  }
}
```
3. vue组件内过滤器this指向undefined？  
   vue中的过滤器更偏向于对文本数据的转化，而不能依赖this上下文，如果需要使用到上下文this我们应该使用computed计算属性的或者一个method方法[这里查看 有关 this undefined in filters 的 issue](https://github.com/vuejs/vue/issues/5998)  

#### vue router
1. 当角色权限改变时，需要删除之前角色的动态添加的路由？  
   解决方法：所有的 vue-router 注册的路由信息都是存放在matcher之中的，所以当我们想清空路由的时候，我们只要新建一个空的Router实例，将它的matcher重新赋值给我们之前定义的路由就可以了，详情[Detail see](https://github.com/vuejs/vue-router/issues/1234#issuecomment-357941465)

#### element ui
1. el-input如果需要处理键盘操作需要加上.native    
   eg: <el-input v-model="todo" @keyup.enter.native="addTodo"></el-input>  
2. el-checkbox,如果需要在不同地方用同一个checkbox渲染，那需要绑定同样的key值

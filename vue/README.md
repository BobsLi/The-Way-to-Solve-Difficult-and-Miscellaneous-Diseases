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
        // 注意：在 sass-loader v7 中，这个选项名是 "data"
        prependData: `@import "~@/variables.sass"`
      },
      // 默认情况下 `sass` 选项会同时对 `sass` 和 `scss` 语法同时生效
      // 因为 `scss` 语法在内部也是由 sass-loader 处理的
      // 但是在配置 `data` 选项的时候
      // `scss` 语法会要求语句结尾必须有分号，`sass` 则要求必须没有分号
      // 在这种情况下，我们可以使用 `scss` 选项，对 `scss` 语法进行单独配置
      scss: {
        prependData: `@import "~@/variables.scss";`
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
3. vue组件内filters过滤器中this指向undefined？  
   vue中的过滤器更偏向于对文本数据的转化，而不能依赖this上下文，如果需要使用到上下文this我们应该使用computed计算属性的或者一个method方法[这里查看 有关 this undefined in filters 的 issue](https://github.com/vuejs/vue/issues/5998)  

4. vue组件中样式影响子组件里的样式？
	（1）创建一个没有scoped 的style里面编写子组件的样式；
	（2） 在有scoped 的style里面 使用 /deep/ 或 ::v-deep 选择器，只适用于sass/less的预编译器
5. vue使用SockJS实现webSocket通信 
	[示例1](https://www.cnblogs.com/luoxuemei/p/10115679.html) 
	[示例2](https://juejin.im/post/5b7fd02d6fb9a01a196f6276)
6. vue+axios以流的形式下载文件[https://www.jianshu.com/p/bc2551e1ab2a](https://www.jianshu.com/p/bc2551e1ab2a)
7. vue组件内使用v-charts无法显示标题解决方法[https://www.cnblogs.com/tl542475736/p/9427768.html](https://www.cnblogs.com/tl542475736/p/9427768.html)
	```bash
	  import 'echarts/lib/component/title'
	```
	
	

#### vue router
1. 当角色权限改变时，需要删除之前角色的动态添加的路由？  
   解决方法：所有的 vue-router 注册的路由信息都是存放在matcher之中的，所以当我们想清空路由的时候，我们只要新建一个空的Router实例，将它的matcher重新赋值给我们之前定义的路由就可以了，详情[Detail see](https://github.com/vuejs/vue-router/issues/1234#issuecomment-357941465)

#### element ui
1. el-input如果需要处理键盘操作需要加上.native    
   eg: <el-input v-model="todo" @keyup.enter.native="addTodo"></el-input>  
   
2. el-checkbox,如果需要在不同地方用同一个checkbox渲染，那需要绑定同样的key值

3. 表单验证，验证字段值必须大于1的正数(文档上描述有问题[详情](https://github.com/yiminghe/async-validator))
   ```bash
	{ type: 'number', min: 0, message: '值必须大于1的正数' },、
   ```

4. 表单动态验证实时生效，需要验证的表单字段规则必须设为{}或者[{}],然后根据逻辑动态添加规则

   ```
   this.$set(this.formRules, 'populationBase', this.setPopulationBaseRules())
   ```

5. 解决表格固定列错位问题

   ```
   this.$refs.tableRef.doLayout()
   ```


6. date-picker,显示类型动态切换（year、monthrange）下拉框位置错位：[解决方法el-date-picker加上key](https://codepen.io/bobsli/pen/XWRvazW)
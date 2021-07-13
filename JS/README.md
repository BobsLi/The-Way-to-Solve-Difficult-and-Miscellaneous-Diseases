# JS常见集锦
#### 1.表达式 a ? !!+a : true 使用场景  
    该表达式适用于变量a不是空字符串并且是任意非数字字符串 
#### 2.多维树形嵌套数组和一维扁平化数组互转（树形菜单居多）
```bash
    // 一维数组： 
    [
        {
            id: 1000,
            parentId: 0,
            name: '一级菜单1'
        },
        {
            id: 1100,
            parentId: 1000,
            name: '二级菜单1'
        },
        {
            id: 1200,
            parentId: 1000,
            name: '二级菜单2'
        },
        {
            id: 1110,
            parentId: 1100,
            name: '三级菜单1'
        },
        {
            id: 2000,
            parentId: 0,
            name: '一级菜单2'
        },
    ]
    
    // 树形数组：
    [
        {
            id: 1000,
            parentId: 0,
            name: '一级菜单1',
            children: [
                {
                    id: 1100,
                    parentId: 1000,
                    name: '二级菜单1',
                    children: [
                        {
                            id: 1110,
                            parentId: 1100,
                            name: '三级菜单1'
                        },
                    ]
                },
                {
                    id: 1200,
                    parentId: 1000,
                    name: '二级菜单2'
                },
            ]
        },
        {
            id: 2000,
            parentId: 0,
            name: '一级菜单2'
        },
    ]
```
   **多维转一维：迭代遍历多维数组保存到一个数组里面**
```bash
    eg:
        /**
         * 将多维数组构成的路由拉平成一维数组
         * @param {array} routes 需要拉平的路由数组
         * @param {array} flatRoutes 保存拉平后的路由数组
         */
        function routesFlat(routes, flatRoutes = [], parentId = 0) {
          routes.forEach((route) => {
            route.parentId = parentId
            // 如果存在子路由，则需要再次拉平数组
            const childrenRoutes = route.children
            if (childrenRoutes && childrenRoutes.length > 0) {
              const flag = window.btoa(route.name) // 唯一标志以name字段base64编码命名
              routesFlat(childrenRoutes, flatRoutes, flag)
              if (route.children) {
                route.children = []
              }
            }
            flatRoutes.push(route)
          })
        }
```

   **一维转多维：思路：主要是将一级路由数组通过某一唯一键组成映射关系，然后遍历一级路由，将子路由挂到父路由所对应的映射信息的childer字段上面**
 ```bash
    eg:
    
    function routesNest(flatRoutes) {
      const mapRoutes = [] // 存放路由映射关系
      const routes = [] // 最终生成的路由
      // 生成path->路由信息的映射表
      for (const index of flatRoutes.keys()) {
        const route = flatRoutes[index]
        mapRoutes[route.name] = route
      }
      for (const index of flatRoutes.keys()) {
        const route = flatRoutes[index]
        if (route.parentId === 0) {
          routes.push(route)
        } else {
          const children = mapRoutes[route.parentId].children
          if (children) {
            children.push(route)
          }
        }
      }
      return routes
    }
 ```

#### 3. 让div聚焦问题
必须先通过js设置div可编辑（不能直接在div上加contentEditable属性），然后在设置div聚焦，具体步骤如下
```
const divObj = document.getElementById(id);
divObj.contentEditable = true
divObj.focus()
```
#### 4. 纯数字不能直接使用toString()方法,浏览器会把.解析为小数点直接报错 

#### 5. 判断对象属性是否存在[https://eslint.bootcss.com/docs/rules/no-prototype-builtins/](https://eslint.bootcss.com/docs/rules/no-prototype-builtins/)
	```bash
		eg:
		const obj = {
		  one: 1,
		  two: 2
		}
		// false
		obj.hasOwnProperty('one') // Do not access Object.prototype method 'hasOwnProperty' from target object
		
		// true
		Object.prototype.hasOwnProperty.call(obj, 'one')
	```

#### 6.  image访问图片跨域问题[https://juejin.cn/post/6844903795726483463](https://juejin.cn/post/6844903795726483463)

​	1. 同一张图片或者同一个地址，同时被 'img' 所访问，而随后后又会被如 JS 中去访问。而图片存储的地址是跨域的，那么就可能因为缓存问题而导致 JS 中的访问出现跨域问题。

​	2. 解决的办法是让 'img' 标签和 JS 中的访问都走跨域访问的方式，这样既可以解决跨域访问的问题，也可以解决跨域图片在 canvas 中的复用。

```html
<img src="https://file-test-1259370834.cos.ap-chengdu.myqcloud.com/0000/INSTALL_CHECK_FILE/d6eff438-bb6a-4723-a0fe-743f69595e04.png" crossorigin="anonymous">
```


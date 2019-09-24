# JS常见集锦
1.  表达式 a ? !!+a : true 使用场景  
    该表达式适用于变量a不是空字符串并且是任意非数字字符串 
2.  多维树形嵌套数组和一维扁平化数组互转（树形菜单居多）
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

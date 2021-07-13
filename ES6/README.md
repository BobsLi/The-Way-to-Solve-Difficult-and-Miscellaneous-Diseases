# ES6常用或坑点
### 坑点

#### 1.扩展运算符用于数组赋值，只能放在参数的最后一位；属性解构赋值也必须为最后一个参数

```javascript
// 数组赋值
const [...butLast, last] = [1, 2, 3, 4, 5]; // 报错
const [first, ...middle, last] = [1, 2, 3, 4, 5]; // 报错

//对象赋值
let { x, ...y, z } = { x: 1, y: 2, a: 3, b: 4 }; // 报错
```
#### 2.Object.is()两个特别的值
```javascript
+0 === -0 //true
NaN === NaN // false

Object.is(+0, -0) // false
Object.is(NaN, NaN) // true
```

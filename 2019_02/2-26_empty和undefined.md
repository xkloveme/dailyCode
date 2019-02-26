# 2-26_empty 和 undefined

> 将每天看到的优秀的代码或者特别的实现，记录下来

_2019-2-26_

## empty 和 undefined

- ### 数组的 filter，以下输出结果是什么

```js
var arr = [1,2,3];
arr[10] = 9;
arr.filter((item)=> { return item === undefined? })
//答案 []
```

### 解析

_是的，答案的确是[]，不是`[undefined x 7]`。 首先，看下前两句执行后，arr 是什么_

```js
console.log(arr)
//[1,2,3, emptyx7, 9]
console.log(arr[5])
//undefined
```

```js
var b = [undefined]
b[2] = 1
console.log(b)
// (3) [undefined, empty × 1, 1]
console.log(b.map(e => 7))
// (3) [7, empty × 1, 7]
```

undefined 和数组保留的 empty 插槽并不是等同的，即使我们打印出相应的数据会显示`undefined`，但是与 js 的`undefined`是不同的，除了 arr.filter，包括 arr.map()函数都是会保留 empty 插槽的

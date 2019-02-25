# 2-25_proxy代理


> 将每天看到的优秀的代码或者特别的实现，记录下来

_2019-2-25_

```js
let  proxy  =  new  Proxy({}, {
get(trapTarget, key, receiver) {
if (!(key  in  receiver)) {
throw  new  TypeError("'属性' "+  key  +  "'不存在'")
}
console.log(receiver, 22)
return  Reflect.get(trapTarget, key, receiver)
}
})
proxy.name="jixiaokang";
console.log(proxy.name)
```

## 注释

*   `trapTarget` 被读取属性的源对象(代理的目标)
*   `key` 要读取的属性键(字符串或`Symbol`)
*   `receiver` 操作发生的对象


- 调用`new Proxy()`可创建代替其他目标(`target`)对象的代理，它虚拟化了目标，所以二者看起来功能一致。

- 代理可以拦截JS引擎内部目标的底层对象操作，这些底层操作被拦截后会触发响应特定操作的陷阱函数。

- 反射API以`Reflect`对象的形式出现，对象中方法的默认特性与相同的底层操作一致，而代理可以覆写这些操作，每个代理陷阱对应一个命名和参数都相同的`Reflect`方法


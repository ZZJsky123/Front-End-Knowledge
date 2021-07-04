## apply

```
apply(thisarg, [argments])

1. thisarg:  应绑定的函数对象，若对象为null 或者 undefined 则自动被替换为全局对象 （在非严格模式下）
2. [argments]： 数组或者类数组，当参数为类数组时，自动转化为数组
```



```javascript
Function.prototype.myapply = function(context){
    let context = context || window;
    context.fn = this
    let args = [...arguments].slice(1)[0] || []

    if (!Array.isArray(args)){
         throw new Error('TypeErroe not Array')
    }
    context.fn(...args);   // 执行该方法
    delete context.fn;  // 从对象中移除
}


```

## call

```javascript
Function.prototype.mycall = function (context){
    let context = context || window;
    context.fn = this;
    let arg = [...arguments].slice(1);
    context.fn(...arg);
    delete context.fn;
    console.log([...arguments])
}

```



## bind

```javascript
bind(thisArg, arg1,arg2,...)

1. bind 将创建一个新的函数， 新函数的this参数将被绑定为bind的第一个对象，其余参数将作为新函数的其他参数
如果 bind 函数的参数列表为空，或者thisArg是null或undefined，执行作用域的 this 将被视为新函数的 thisArg
     
2. arg1, arg2, ...
   当目标函数被调用时，被预置入绑定函数的参数列表中的参数。

3. 绑定函数也可以使用 new 运算符构造，提供的第一个参数会被忽略
```

```javascript
Function.prototype.mybind = function(context, ...args1){
    let _this = this;
    let context  = context;
    
    function res(...args2){
        if (this instanceof _this){
            _this.call(this, ...args1,...args2);
        }else{
            _this.call(context, ...args1,...args2) 
        }
    }
      function foo() {};
      if(_this.prototype) {
          foo.prototype = _this.prototype;
      }
      res.prototype = new foo();  
    
    return res
    
}

Let fn1 = foo.bind(obj2, arg1);

let obj2 = new fn1();  // 创建空对象   {}.__proto__ = res.prototype    res的this绑定为该空对象   执行
```



>  一个或运算 `||` 的链，将返回第一个真值，如果不存在真值，就返回该链的最后一个值。

> 与运算 `&&` 做了如下的事：
>
> - 从左到右依次计算操作数。
> - 在处理每一个操作数时，都将其转化为布尔值。如果结果是 `false`，就停止计算，并返回这个操作数的初始值。
> - 如果所有的操作数都被计算过（例如都是真值），则返回最后一个操作数。
>
> 换句话说，与运算返回第一个假值，如果没有假值就返回最后一个值。
>
> 上面的规则和或运算很像。区别就是与运算返回第一个假值，而或运算返回第一个真值。

## arguments 与 扩展语法

```
arrguments是函数的默认参数，它是类数组，即只拥有数组的length方法其余方法没有。
```


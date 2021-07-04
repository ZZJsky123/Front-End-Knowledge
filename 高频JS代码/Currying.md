## Curry

```javascript
var curry = (fn) => {
    judge = ...args => {
        [...args].length === fn.length
        ? fn(...args)
        : (arg) => judge(...args,arg)
    }
}

// 函数柯里化： 使用的父函数变量是 fn.length：函数所需参数个数
// 传出的内部函数： judeg(...args){}
// judeg 的两种行为 当输入参数 = fn.length  --> 执行函数fn
// 输入参数小于fn.length 继续返回judeg
// 柯里化函数返回一个包装器 该包装器是当前函数的偏函数

// judge就是偏函数
```

```javascript
函数柯里化： 函数柯里化后，当参数输入不足时返回函数的偏函数。

function curry (fn,len,...args){
   
   return function(...args2){
       let arg = [...args,...args2];
       if (arg.length >= len){
           fn.apply(this, arg);
       }else{
           return curry.call(this, fn, ...arg)
       }
   }
}
```


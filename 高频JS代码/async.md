## async

```javascript
1. async 是Generator的语法糖  
2. Generator的* 被async代替。  // async指明函数内部存在异步事件逻辑
3. Generator的yield 被await代替。 // await 后紧紧跟着异步事件逻辑，执行完当前事件后继续向下执行
4. async 最终会返回一个Promise对象。

5. aysnc 也是异步编程方案, aysnc将异步逻辑写出了同步风格。

6. async函数内部return语句返回的值，会成为then方法回调函数的参数。

7. async函数返回的 Promise 对象，必须等到内部所有await命令后面的 Promise 对象执行完，才会发生状态改变，除非遇到return语句或者抛出错误。也就是说，只有async函数内部的异步操作执行完，才会执行then方法指定的回调函数

function timer(message,delay){
    setTimeout(() => {
      console.log(String(message))
    }, delay)
}

async function asyfun(){
    await timer('第一次',1000);
    await timer('第二次',1000);
    return 2;
}

let p = asyfun();
p.then((res) => {
  console.log(res)    // 2
})
console.log(p);       
```


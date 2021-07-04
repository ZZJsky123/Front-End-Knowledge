## Promise

```javascript
1. 异步编程方案， Promise采用状态管理，首先新建一个状态为【Pending】的对象，送入一个执行函数，函数内部放置异步任务逻辑，
   执行函树共有两个参数：resolve、rejected，当异步任务完成，成功则调用resolve函数，其改变当前Promise对象状态为[Fulfilled]
并将结果传给then方法中的回调函数，随后将该回调函数加入到任务队列中，失败则会调用reject函数，其会将错误信息传递给then方法中的
onrejected回调函数(如果设置的话)，获取错误会一直向下传递直到被catch捕捉

2. 当有多个异步任务，且后一个异步任务需要前一个异步任务的结果，则可以使用Promise链式编程，或者又被称为then方法链，其核心在于
   then方法会返回Promise对象，该Promise对象存放下一次异步任务逻辑，相应的回调函数存放在紧跟其后的then方法中，该then方法又会
   返回新的Pormise对象，自此形成Promise链。 then方法返回promise对象有四种情况： 直接返回一个Promise对象，则等该Promise对
   象状态发生改变后，调用其后的then方法；2 回调函数返回的是一个thenable对象，则会被包装成一个Pormise对象，并会立即执行其then 
   方法，3.回调函数返回的是一个普通对象或者基本类型值，then方法会使用Promsie.resolve()将其包装成一个状态为Fullfilld的Promise对象，立即调用  4. 回调函数无返回，then方法会使用Promise.resolve()方法，返回一个状态为[Fulfilled]的Promise对象
   其值是上一个Promise对象的值。
```



```javascript
let PENDING = 'pending';
let FULFILLED = 'fulfilled' ;
let REJECTED = 'rejected' ;

function Promise(executor){
    let self = this
    this.status = PENDING;
    this.value = null;
    
    this.onFulfilled = [];
    this.onRejected = [];
    
    function resolve(res){
        value = res;
        if (self.status === PENDING){
           self.status = FULFILLED;
           self.onFulfilled.forEach(function(callback){
                setTimeout(() => {
                    callback(res);
                })

           }
    }
    
    function reject(err){
        self.value = err;
        if (self.status === PENDING){
          self.status = REJECTED;
          self.onRejected.forEach(function(callback){
            setTimeout(() => {
                   callback(err);
            })

         })
       }
    }
    
  executor(resolve, reject);  
    
}
```

```javascript
Promise.prototype.then = function(onfulfilled, onrejected){
       onfulfilled = typeof onfulfilled === ‘function’ ? onfulfilled : (value)=>{
              value;
       }   
       onrejected = typeof onrejected === 'function' ? onrejected : (value) => {
               value;
      }
      let self = this; 
      
      let promise  = new Promise((resolve, reject) => {
              if (self.status === FULFILLED){
                  let res = onfulfilled(self.value)
                  res instanceof Promise? res.then(resolve, reject): resolve(res)
                   
              }else if(self.status === REJECTED){
                  let err = onRejected(self.value)
                  res instanceof Promise? res.then(resolve, reject): reject(res)
                  
              }else if(self.status === PENDING){
                  self.onFulfilled.push(onfulfilled);                                                                         self.onRejected.push(onrejected);   
              }
              
          }
      )
      
      return promise;   
}
```

```javascript
Promise.prototype.all = function(promiseArray){
       
     if (!Array.isArray(promiseArray)){
        throw new TypeError('arguments should be the Array');
     }
    
     let rr =[];
     return new Promise((resolve, reject) => {
          if (!promiseArray.length){
              return resolve(rr);
          }
          promiseArray.forEach((p) =>{
              Promise.resolve(p).then((res) => { rr.push(res)})
                                .catch((err)=>{ console.log(err.message)})
          })
          if (res.length === promiseArray.length){
              resolve(rr)
          }else{
              reject(new Error('Promise failed'))
          }
     })
}
 // 静态all方法 template
 static all(promiseArr) {
      let count = 0
      let result = []
      return new MyPromise((resolve, reject) => {
        if (!promiseArr.length) {
          return resolve(result)
        }
        promiseArr.forEach((p, i) => {
          MyPromise.resolve(p).then(value => {
            count++
            result[i] = value
            if (count === promiseArr.length) {
              resolve(result)
            }
          }, error => {
            reject(error)
          })
        })
      })
    }
```

```javascript
// Promise.race 接受一组Promsie，只要有一个Promise变成fulfilled就返回，若一个promise变成rejected,返回rejected的Promise
Promise.prototype.race = function(promiseArray){
    if (!Array.isArray(promiseArray)){
        throw new TypeError('race should accept Array ');
    }
    return new Promise((resolve, reject) => {
          if (!promiseArray.length){
              return  resolve(result);
          }
         promiseArray.forEach((pp) => {
             Promise.resolve(pp).then((res) => {
                 resolve(res);
             }, err => {
                reject(err);
             })
         })
    })
}
```



```javascript
Promise.prototype.resolve = function(x){
    return x instanceof Promise? x: new Promise( resolve => {resolve(x)})
}
```


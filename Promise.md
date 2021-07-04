## Promise

```javascript
const PENDING = 'pending'
const RESOLVE = 'resolve'
const REJECTED = 'rejected'
function mypromise(fn){
    var self = this     // 保存this指针
    
    this.state = PENDING
     
    // 用于保存resolve或者rejected 传入的val参数
    this.value = null
    
    // 用于保存resolve的回调函数
    this.resolveCallbacks = []
    
    // 用于保存reject的回调函数
    this = []
                                  // 以上初始化Promise对象时创建四个属性：state，value, [],[]
    
    function resolve(value){
        if (value instanceof MyPromise){
            return value.then(resolve,reject)
        }
        
        setTimeout(() => {                       // 加入到事件循环队尾
            if (self.state === PENDING){
            self.state = RESOLVED
            
            self.value = value;
            
            self.resolveCallbacks.forEach((callback)=>{
                callback(value)
            })
          }
        },0)
    }
    
    function reject(value){
        
    }                            // 以上是定义resolve函数和reject函数
    
    try{
        fn(resolve,reject)      // fn是传进来的回调函数，在Promise内部调用并传入两个函数
    }catch(e){
        reject(e)
    }
}                              // 截止

MyPromise.prototype.then=function(onResolved,onRejected){
    onResolved = 
        typeof onResolved === 'function'
        ? onResolved
        : function(value){
              return value
          }
    onRejected = 
        typeof onRejected === 'function'
        ? onRejected
        : function(value){
             return value      
          }
    if (this.state === PENDING){
        this.resolveCallbacks.push(onResolved)
        this.rejectCallbacks.push(onRejected)
    }
    if (this.state === Resolved){
        onResolved(this.value)
    }
    if (this.state === Rejected){
        onRejected(this.value)
    }
}

// 手写Promise.all
Promise.all = function(iterator){
    if(!Array.isArray(iterator)) return;
    
    let count =0
    let res =[]
    return new Promise((resolve, reject) =>{
        for(let item of iterator){
            Promise.resolve(item)
            .then(data =>{
                res[count++] = data
                if (count === iterator.length){
                    resolve(res)
                }
            })
            .catch(e => {
                reject(e)
            })
        }
    })
}
```


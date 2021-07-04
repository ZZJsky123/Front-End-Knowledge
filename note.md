## 演草



```javascript

function mypromise(fn){
  
  const callbacks = [];
  
  function resolves(res){
      callbacks.forEach(callback => callback(res))
  }
  
  setTimeout(() = >{
      fn(resolve,reject)
  },0)
}

mypromise.prototype.then = function(onfullillment){
    this.callbacks.push(onfullillment)
    return this
}
```

```javascript

function mypromise(fn){
  const self = this
  self.states = 'pending'
  self.callbacks = [];
  self.value =null
  
  
  
  function resolves(res){
      self.states = 'fullfilled'
      self.value = res
      callbacks.forEach(callback => callback(res))
  }

  fn(resolve,reject)
}

mypromise.prototype.then = function(onfulillment){
    if(this.states === 'pending'){
        this.callbacks.push(onfulillment)
    }else{
        // 保证resolve执行完也可执行then
        onfulfillment(this.value)
    }
    return this
}
```

```javascript
function mypromise(fn){
  const self = this
  self.states = 'pending'
  self.callbacks = [];
  self.value =null
 
  function resolve(res){
      self.states = 'fullfilled'
      self.value = res
      callbacks.forEach(callback => this.handle(callback))
  }
  
  function handle(callback){
   if(this.states === 'pending'){
        this.callbacks.push(callback.onfulfillment)
        return;
    }
    if (!callback.onfulfillment)        // 当前then无回调将this.value下一个promise中
        callback.resolve(this.value)
        return;
    }
    // 当前then有回调先处理，将结果传递给下一个promise的resolve
    let res = callback.onfulfillment(this.value) 
    callback.resolve(res)
  }
  fn(resolve,reject)
}

mypromise.prototype.then = function(onfulfillment){
  return new mypromise( resolve =>{
      this.handle({
          onfulfillment: onfulfillment || null,
          resolve: resolve
      })
  })
}
```



```javascript
new mypromise((resolve,reject) => {
    let xhr = new XMLHttpRequest()
    let res;
    xhr.onreadychangestate = function(){
        if (xhr.readystate ===4 && xhr.status === 200){
            res = xhr.responseText
        }else{
            res = new Error('请求错误')
        }
    }
    xhr.open('get',url)
    xhr.send
    resolve(res)
}).then( res => {
    console.log(res)
})
```


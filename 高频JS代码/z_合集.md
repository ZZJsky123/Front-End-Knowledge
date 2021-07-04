## debounce

> 高频事件执行限制，返回函数，参数：输入函数，延时  

```javascript
function debounce(fn, delay){
   let timer = null;
   
   if (typeof fn === 'function'){
       throw new TypeError('')
   }
    
   return function(...args){
      let _this = this;
      if(timer){
          clearTimeout(timer)
      }
      timer = setTimeout(()=>{
        fn.call(_this, ...args)
      },delay)
   }

}
```

## throttle

> 高频事件执行限制，返回函数，参数：输入函数，延时

```javascript
function throttle(fn, delay){
   
   let timer = null;
   if (typeof fn === 'function'){
       throw new TypeError('')
   }
       
   return function(...args){
       let _this = this;
       if(timer){
           return;
       }
       timer = setTimeout(()=>{
           fn.call(_this, ..args)
       }, delay)
     
   }
}
```



## flatten

> 数组扁平化，将嵌套的数组转化为1维数组， 输入参数：数组，   返回：扁平数组,     迭代

```javascript
function flatten(arr){
    
    if(!Array.isArray(arr)){
         throw new TypeError('') 
    }
    if(!arr){
        return arr;            // 数组为空返回
    }
    let res =[];
    
    for (let v of arr){
       if (Array.isArray(arr)){
           res = res.concat(flattern(arr));
       }else{
          res.push(v)
       }
    }
    return res;
}

// reduce 进行简化
function flatten(arr){
    if(!Array.isArray(arr)){
         throw new TypeError('') 
    }
    if(!arr){
        return arr;            // 数组为空返回
    }
    return arr.reduce((total,cur) => {
        Array.isArray(cur)?total.concat(flatten(cur))
                          :total.concat(cur)
    },[])
}
```



## Copy

>  浅拷贝 和 深拷贝, 对象或者数组进行一个拷贝

```javascript
function shallowcopy(obj){
    
   if(!obj || typeof obj !== 'object'){
       return obj
   }
    
   let nobj = Array.isArray(obj)? []: {}
   
   if(Array.isArray(obj)){
       for (let v of obj){
           nobj.push(v);
       }
   }else{
       for (let i in obj){
           if(obj.hasOwnProperty(i)){
              nobj[i] = obj[i]; 
           }
       }
   }
   
}
```

```javascript
function deepcopy(obj){
  
  if(!obj || typeof obj !== 'object'){
      return obj
  }
    
  if(obj instanceof Date){
      return new Data(obj);
  }else if(obj instanceof RegExp){
     return new RegExp(obj);
  }
  
  let nobj = Array.isArray(obj)? []: {}
  
  let map = deepcopy.map?deepcopy.map:new Map();
    
  if(map.get(obj)){
      return map.get(obj)
  }
  
  map.set(obj, nobj);
  
  for(let i in obj){
      if(obj.hasOwnProperty(i)){
          nobj[i] = deepcopy(obj[i]);
      }
  }
   
 return nobj;
}
```

## Currying

> 函数科里化，返回偏函数，参数输入完成后执行

```javascript
function curry(fn, len, ...args){
   
  return function(...params){
      let param = [...args, ...params];
      
      if(param.length >= len){
          cb.apply(this, param)
      }else{
          return curry.call(this, fn, len, ...param);
      }
  }
}
```

> 函数输入参数是什么， 返回是什么， 内部逻辑，逻辑使用什么语法去实现
## instanceof

> instance of用于对象类型判断：
>
> ​                  obj instanceof  Array  // true  obj = []
>
> ​                  obj instanceof  Number  // true  obj = new Number()
>
> 检测机制： 右边的构造函数是否在左边实例对象的原型链上

```javascript
function myinstanceof(obj, origin){

    while(obj){
       if (obj.__proto === origin.prototype){
           return true
       }
       obj = obj.__proto__;
    }
    return false;
} 
```

总结： 用instanceof作实例对象类型检测时，采取判断思想是若实例对象是由某一个构造函数创建的，则

​             该构造函数的prototype一定在这个对象的原型链上
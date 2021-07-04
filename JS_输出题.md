## 函数

```javascript
【this 指针理解】
  1. 
    var length = 10
    function fn(){
        console.log(this.length);
        console.log(this)
    }

    var obj = {
       length:5,
       method:function(){
         fn();
         arguments[0]();
       }
    }
    obj.method(fn, 1);
 [output]： 10 2      // 解释2:arguments[0]() , 相当于arguments.fn() this.length记录的是长度
 
  2. 
   var b = 10;
    function fn(){
      console.log(this.b)
    }
    c = {
      b:11,
      fn: fn.bind(window)
    }
    c.fn();
 [output]: 10
  
```


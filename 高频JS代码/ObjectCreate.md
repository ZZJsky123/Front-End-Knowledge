

> 对象总共有三种创建方法：
>
>            1.    直接声明：          var obj = {}
>            2.     new :            var obj =  new fun()
>            3.    Object提供的方法：  var obj  = Object.create(原型对象 ) 

## Object.create

>  Object.create(原型对象,  新对象属性(可选))， 该函数会返回一个新的对象，并会将第一个参数作为新对象的原型对象与之关联。
>
> var obj = {}   等价于  var obj = Obejct.create(Object.prototype)
>
> var obj = Object.create(null)     //  会返回一个null 对象
>
> var obj = new fun()     等价于  var obj =Object. create( fun. prototype )
>
> 创建对象之初为对象添加属性， 未定义的内部属性自动为false
>
> Object.create( {},  {p: {
>
> ​         value: 1,
>
> ​         writable: false,
>
> ​         enumerable: false,
>
> ​         configurable: false
>
> },
>
> foo: { value :1}
>
> })

```javascript
Object.prototype.myobject = function(proto, propertiesOption = undefined){
   
    if (typeof proto !== 'object' ) {
          throw new TypeError('Object prototype may only be an Object: ' + proto')
    }
   if (parent === null)  return null;
   
   function F(){};
   F.prototype = proto
   const obj = new F();      // 1. 创建一个新对象  2. 新对象进行原型关联
   
   if (typeof properiesOption !== 'undefined'){
      Object.defineProperties(obj, propertyObject)
   }
   return obj
}
//  JS 函数支持默认形参
```

```javascript
new Fun();     
new 在创建实例化的过程完成以下操作：
    1. 创建一个空对象
    2. 将空对象的原型设置成Fun.prototype
    2. 执行Fun.call(obj)函数
    3. 若函数Fun无返回值，则将该对象进行返回

function create(){
    var fn = [].shift.call(arguments);   //  将arguments第一个函数参数提取出来
                                         //  这句话等价于  let args = [...arguments]
                                         //              fn = args.shift() 
    let obj = {};
    obj.__proto__ = fn.prototype;
  
    let res = fn.apply(obj, arguments);
    
    return typeof res === 'object' ? res : obj;
}
```


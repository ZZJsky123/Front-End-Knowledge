## Prototype

```
1. 每个对象都拥有一个内部属性[[prototype]] - > _proto_
2. 对象的_proto_存放着它们的原型
3. Function的原型存放在Prototype下的_proto_下
4. 对象通过原型关联是为了模仿oop语言的继承

5. _proto_下都有一个constructor属性，其指向该对象的构造函数
6. 函数使用Object.create 关联的一般方式： 
    Bar.prototype = Object.create( Foo.prototype );
   这种关联方式： Bar.prototype下的_proto_指向Foo.prototype
   错误的关联方式：Bar.prototype = Foo.prototype将Foo.prototype直接
   赋给Bar.prototype
   
7. // ES6 开始可以直接修改现有的 Bar.prototype
    Object.setPrototypeOf( Bar.prototype, Foo.prototype );
8. 检测b是否在c的原型链中：
   b.isPrototypeof(c)
9. 直接获取对象a的原型链：
    Object.getPrototypeOf(a)
10. 
```


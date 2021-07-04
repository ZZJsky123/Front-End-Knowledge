# JavaScript

## 函数

```javascript
【第一类对象】： 5条性质
        
【函数式编程】： 第1点： 函数式第一类对象

【4种函数】： 函数声明/函数表达式、立即函数、 箭头函数、 构造器函数
   
   [立即函数]的作用：

【存储函数】： 数组中存放函数如何判断函数的唯一性：为函数添加id属性

【函数参数】： 实参、形参 、 argumnets、 剩余参数、 默认参数
     
     [词法环境]： 词法环境是否在函数声明时创建，记录的是实参还是形参

【函数上下文】： this参数   函数、 方法、 构造函数、 call/apply/bind 
              、 箭头函数  绑定的优先级
              
   【闭包】： 闭包发生的条件、 变量存在于哪才可被访问
   
 【代码类型】： 全局代码、 函数代码。  
 
 【词法环境】：跟踪变量的作用域    
 
   【作用域】： 函数作用域、 块级作用域、 全局作用域、 对象作用域(with)
   
   [块级作用域中的函数声明]： 块级中的函数声明用表达式去代替
   

   
 Effective Java:
   1. 函数、方法、类的构造函数是单个构造对象的三种不同的是使用模式
   2. function中使用了this， 则单独作为函数调用不太有用
   3. 高阶函数：将函数作为参数或者返回值的函数
   4. 将函数作为参数： 传进去一段 （代码） = 值
   5. 高阶函数将代码更高效、 更简洁、 更可读
   6. call方法使得某对象调用为拥有的函数 f.call(obj)
   7. apply方法用于可变参数的方法
   8. 永远不要修改arguments， 实参与arguments一一对应，删除、修改
      都容易导致程序运行错误。
   9. 使用变量保存arguments对象： 预防函数嵌套时内部函数使用外部函数
      的arguments丢失
   10. 当给高阶函数传递对象方法时，使用匿名函数在适当的接收者上调用该方法
   11. 柯里化： 将函数与函数的参数子集绑定的技术， 使用bind函数可以完成
       函数的柯里化。
   12. 使用闭包而不是eval来封装代码： 无变量泄露的危险。

   
ES6 储一峰

let 和 const命令：
     1.
        for (let i = 0; i < 3; i++) {
          let i = 'abc';
          console.log(i);
        }
        [out]:  // abc  // abc  // abc            
        输出结果表明：循环变量声明和循环体有着不同的作用域。
     2. temporal dead zone(暂时性死区)： ES6明确规定： 如果区块中存在用let和const声明的变量，未声明之前使用他们都会报错。
     3. let不允许在相同的作用域上重复声明。函数体不能直接声明与形参相同名字的let 变量。
     4. 在块区域中声明函数：
     
             ES5： 函数只能在顶层作用域和函数作用域声明，但是浏览器并未
                  遵守依然可以声明函数，会被变量提升到外部。
             
             
             ES6：规定块级作用域中的函数声明类似于let，但是由于浏览器兼容问题，针对ES6浏览器提出三条建议：
              1. 允许在块级作用域内声明函数
              2. 函数声明类似于var， 会提升到全局作用域或者函数作用域头
              3. 函数声明还会提升到所在的块级作用域的头部。
    5. const实际上保证的，并不是变量的值不得改动，而是变量指向的那个内存地址所保存的数据不得改动
    
    6. 全局对象与顶层对象脱钩： 顶层对象在浏览器中指的是window，在Node指的是global， 在ES6中 let、const、class声明的全局变量都不会加入到顶层对象中。 
             
    
```

## 地图

```javascript
  ---         全局代码   函数代码
  ---              调用栈
  ---   全局作用域   函数作用域   块级作用域
  ---          词法环境： 跟踪变量
  
    【第一类对象】：   函数声明创建字面量。
       【函数式】：   函数名/函数表达式赋值给变量、对象属性、 数组。
                    函数名/函数表达式作为参数传递给函数。
                    函数名/函数表达式作为返回值返回。
    
       函数声明： function f(){}     单独出现在上下文中，词法环境收集
                         
       函数表达式：  var a = function f(args){}  带名字函数表达式
                   var a = function (args){}   匿名函数表达式
       
       箭头函数： () => {}    
       
       构造函数:  var a = new F()
       
         IIFE:  函数表达式被立即执行。
                (function (){})(args)
                (function (){}(args))
                +function(){}(args)
                -function(){}(args)
                !function(){}(args)
                ~function(){}(args)
       IIFE的作用： 
            1. 立即创建一个函数作用域
            2. 内部有函数时会创建闭包，用闭包访问内部变量。
            3. 模块化： 绑定特定的全局变量到函数内部，避免变量使用冲突
              (其实我们希望每一个变量都拥有自己的作用域)

       注意： 在使用IIFE时也可以调用函数的call/apply/bind等方法

  【函数调用时】：
        1、传入两个隐式参数 this、 对象arguments
        2. this是函数上下文： 方法、构造函数意义极大。
           全局函数，IIFE中this指向的是window， 严格模式下指向的是 
           undefined。
        3. 箭头函数的this， call/apply/bind在声明时已经决定
           方法： this在调用时决定
        4. 链式传递this时，离函数最近的对象作为调用者传进去。
        5. new Fun() of this， new operator生成一个新的对象，将该
           对象作为fun调用的上下文。  Fun 返回一个对象类型：函数、数组
           ..则不会将生成的新对象返回。 反之返回新的对象。
        6. call/apply/bind。 

   【函数参数获得】： 
        1. 函数的传入的实参被保存在arguments对象中，具备 length 属性
           非严格模式下，arguments与实参一一对应， 修改任意一方会导致另
           外一方的改变，永远不要修改arguments参数。严格模式下，修正了
           他们之间的绑定，修改一方不会导致另外一方改变。
        2. ...remains。 箭头函数没有 arguments 参数，用剩余参数来获
           all args ， remains是一个数组。
        3. default args ， ES6引入默认参数， 声明函数形参时可以赋予
           默认参数

   【闭包】： 闭包是一种机制： 触发、过程、目的效果
          目的效果： 内部函数可以访问并操作外部变量或者函数，只要变量
                   或函数与该函数声明所在的作用域相同。
          重要机制： 内部函数访问的外部的词法环境不会被垃圾清除
             触发： 声明内部函数时会创建闭包。

    【词法环境】  ： 规定一组标识符到特定变量和函数的联系。
       存在于： FunctionDeclaration、 WithStatement、Try-Catch

                             |--- Environment Recoder： 记录词法环境中的 identifier binding
    Lexical Environment -----|
                             |--- reference to an outer LE

                             |--- Declarative ER
    Environment Recoder -----|
                             |--- Object Environment Recoder
       
   将Lexical Environment 看作对象， 在 LE 上有两种属性,：
      1.Declarative EnvRec 记录的一组标识符绑定的是声明的变量和声明的函数。
      2.Object EnvRec 记录的一组标识符是 绑定对象 的属性。
  
   Common Method for Declar EnvRec & Obj EnvRec： 
      1. HasBinding(N)
      2. CreateMutableBinding(N, D)
      3. SetMutableBinding(N, V, S)
      4. GetMutableBinding(N, S)
      5. DeleteBinding(N)
      6. ImplictThisValue()  

   Declar EnvRec: 
      1. Delarative EnvRec 拥有 immutable Binding， 创建和初始化是分开的
        CreateImmutableBinding(N) : Create a new but uninitialised
                                    immutable binding.
      
        InitializeImmutableBinding(N,V) : N[must exist and unInitialize]
                                          Initialize: the value of N = v
      2. CreateMutableBinding(N,D)：
               1. Let envRec be the declarative environoment record
               2. Assert: envRec 未声明过N
               3. Create mutable binding in envRec for N and set its bound
                  value to undefined
               4. D is true new created Binding was deleted by a subsequent 
                  DeleteBinding call
      3. SetMutableBinding(N, v, s):
             1. Let envRec be the declarative environoment record （将当前词法环境赋给变量）
             2. Assert： envRec 声明过N
             3. N is mutable binding ， change the value of N to V
             4. N is immutable binding， thorw TypeError
      4. GetMutableBinding(N,s)
             1. Let envRec be the declarative environoment record
             2. Assert: envRec has a binding for N.
             3. If N is immutable value:
                    a. if S is false, return undefined, else throw
                        a ReferenceError exception
             4. else return the value of N
              
                
       
        
    Operate Lexical Environment：
      1. GetIdentifierReference(lex, name, strict)
         :under specific lex ，acquire bindings value of Identifier 
      name。
         a. if lex is null ， return value of Type Reference , basvalue
            is undefined.
         b. let envRec be the lex‘s Environment Recoder, use HasBind
            -ing(N), {true} return value of Tyoe Reference
         c. b is {false}, find in outer Lexical Environment
         
     2. NewDeclarativeEnvironment(E)
        : create new Lexical Environment, the outer of this LE is E
        
        a. let env be a new Lexical Environment
        b. let envRec be the env's Declarative EvnRec no binding
        c. Set env’s environment record to be envRec.
        d. Set the outer lexical environment reference of env to E.
        e. Return env.
        
     3. NewObjectEnvironment(O, E)
        a. Let env be a new Lexical Environment.
        b. Let envRec be a new object environment record containing O 
           as the binding object.
        c. Set env’s environment record to be envRec.
        d. Set the outer lexical environment reference of env to E.
        e. Return env.
                    
     
    【执行上下文】： 执行上下文 -- 作用域 -- 词法环境
        1. Active execution contexts logically form a stack. 
        2. The top execution context on this logical stack is the  running execution  
           context.
        3. the type of execution : global code 、 function 、 eval
        when context execution is created ， the following states are
     created as the same time:
         1. LexcialEnvironment  : Lexical Environment
         2. VariableEnvironment : environment record holds bindings created
                                  by VariableStatement and FunctionDeclarations
         3. ThisBinding
     
     创建执行上下文， LexicalEnvironment / VariableEnvironment 赋予相同值。
  in ES6， LexcialEnvironment record the functionDeclaration / let /
  const. VariableEnvironment records the var
  in ES5, Variables and functions declared are added as bindings in that VariableEnvironment’s Environment Record. 
  
  in ES5 Entering Function execution context 
     1. set ThisBinding: if [Strict] set ThisBinding to thisArg
     2. else if thisArg is null or undefined,  ThisBinding -> global
     3. else if thisArg is not object , set ThisBinding -> ToObject(thisArg)
     4. else set ThisBinding -> thisArg                                            5. loalEnv = new DelcarativeEnvironment([[Scope]])            
     6. Set the LexicalEnvironment to localEnv.                                    7. Set the VariableEnvironment to localEnv.
     8. Let code be the value of F’s [[Code]] internal property.
     9. Perform Declaration Binding Instantiation using the [function code]

 Declaration Binding Instantiation(标识符绑定)：
   1. let env be the variableEnvironment
   1. 函数形参标识符[[FromalParameters]]与实参绑定, 多于实参的会被赋予undefined 
        HasBinding -> argAleadyDeclared -> flase -> SetMutableBinding
        -> SetMutableBinding
   2. 处理内部函数声明标识符：
          fn be the  Identifier in FunctionDeclaration f.
          fo be the result of instantiating FunctionDeclaration f 
          HasBinding -> funcAlreadyDeclared -> false -> CreateMutableDeclared
          setMutableBinding(fn, fo, strict) 
   3. arguments 标识符.  strict Model 中， arguments was created to 
      immutableBinding。
        argumentAlreadyDeclared ：false
        if strict 
           createImmutableBinding  -> InitializeImmutableBinding
         else
           createMutableBinding -> SetMutableBinding
   4. var声明标识符  (判断位varAlreadyDeclared false才会生成标识符)
      a.let dn be the Identifier in d
      b. HasBinding -> varAlreadyDeclared -> false -> CreateMutableBinding
         -> SetMutableBinding

由上述步骤可知：【函数名】 和 【变量名】 重名， 由于函数名标识符已经存在，所以变量不
             会再被创建。 
函数中收集的标识符： 函数声明， arguments， var声明的标识符
     
     
        
```

## 对象

```javascript
名词解释：
  【constructor】： Function object that create and initalises objects
  【prototype】:  object that provides shared property for other objects
  【native object】：object in an ECMAScript implementation, whose 
                    semantic are fully defined by this specfifcation
                    rather than by the host environment.
  【built-in object】： this object must be the native object
  【host object】：object supplied by the host environment to complete the 
                  execution environment of ECMAScript
  【property】： association between a name and a value that is part of object
  【attribute】： interal value that defines some characteristic of property
  【built-in constructor】: Boolean、 String、 Number、 Function
  【built-in function】： built-in object that is Function
  【built-in method】： method that is a built-in Function

Type: 
    1. The ECMAScript language types:  Undefined, Null, Boolean, String, Number
                                       Object.
    2. specification types: Reference, List, Completion, Property Descriptor,
                            Property  Identifier, Lexical Environment ,
                            Environment Record.
                            
Object Type:
    1. An object is a collection of properties. Each property is either a named
       data property, a named accessor property , or an an internal property.
       ---[data property]: associates a name with ECMAScripts language value
                           and a set of Boolean attribute. 
       ---[accessor property]: associates a name with one or two accessor 
                               functions. accessor functions used to store
                               or retrieve an ECMAScript language value that
                               is associated with the property.
           two kinds of accseeor functions: get and put  
       ---[internal property]: no name and be not directly accseeible 
                               the purpose of exist purely for specification.
   对象存储三种数据： 基本数据类型， 操作前述基本数据类型的访问函数， 内部属性 
   
   2. Property Attribute
      ： define and explain the state of named properties
      [[Value]]:   the value of property        
      [[Writable]]:  if false attemp to change [[Value]] using [[Put]] will fail
      [[Enumerable]]: if false can’t use for...in to get  
      [[Configurable]]: if false , any attemption to change or delete this
                        property will be failed           
      [[Get]]:  The function’s [[Call]] internal method is called with an 
                empty arguments list to return the property value
      [[Set]]:  The function’s [[Call]] internal method  is called with an 
                arguments list containing the assigned value as its sole argument 
                each time.
      [[Get]]、[[Set]] if the value is object it must be a function.
      
      [[Value]]: undefined
      [[Writable]]: false
      [[Enumerable]]: false
      [[configurable]]: false

3. Internal Properties  
   : An implementation of ECMAScript must behave as if it produced and operated upon internal properties in the manner described here
   
   1.  list below are applicable for all ECMAScripts objects
   
   [[Property]]        Object or null
   [[Class]]           String
   [[Extensible]]      Boolean ： false, this object can't add additional property
   [[Get]]             SpecOp(propertyName) -> any
   [[GetOwnProperty]]  SpecOp(propertyName) -> undefined or Property Descriptor
   [[GetProperty]]     SpecOp(propertyName) -> undefined or Property Descriptor
   [[Put]]             SpecOp(property,any,Boolean)
   [[CanPut]]          SpecOp(property)->Boolean: indicats whether [[Put]] 
                                                   Operation can be perform 
   [[HasProperty]]     SpecOp(property)->Boolean
   [[Delete]]          SpecOp(property,Boolean)->Boolean
                     : Remove the own property, Boolean is the flag of handing 
                       failure
                                                    
   [[DefaultValue]] : SpecOp (Hint) → primitive. 
                    : Hint is a String. Returns a default value for the object.
   [[DefineOwnProperty]]: SpecOp(propertyName,propertyDescriptor,Boolean)
                                                                       ->Boolean
   [注]： Every object (including host objects) must implement all of the internal 
         properties listed up . However, the [[DefaultValue]] internal method , 
         for some objects, simply throw a TypeError exception.  对象共同实现的内部属
         属性： property for 继承 、 检测属性是否存在、 根据属性名获取属性值、 删除属性
         
         [[Extensible]]: once, its value was set to false, [[Property]] and
                         [[Class]] can’t be Modified. And its can't set to true
                         again.
         [[Class]]: only one way to asscess its value is by Object.property.toString
                    它的值可能是 "Arguments", "Array", "Boolean", "Date", "Error", 
                    "Function", "JSON", "Math", "Number", "Object", "RegExp",                           
                    "String"

   2. list below are only applicable for specfic objects
      [[PrimitiveVlaue]] primitive
      [[Construct]]      SpecOp(list of any) -> object
                         :Creates an object. Invoked via the new operator. The 
                          arguments to the SpecOp are the arguments passed to the 
                          new operator. Objects that implement this internal method 
                          are called constructors.
      [[Call]]           SpecOp(any,a list of any) ->any or Reference
                         : execute the code that associates with this Object
                         Invoked via a function call expression.Objects that 
                         implement this internal method are callable. Only callable 
                         objects that are host objects may return Reference values.
      [[HasInstance]]    SpecOp(any) -> Boolean
      [[Scope]]          Lexcial Environment
                        : define the lexical Environment that function is executed.
      [[FormalParameters]] List of String
                        : A possibly empty List containing the identifier Strings of 
                          a Function’s FormalParameterList.
      [[Code]]          ECMAScript code
      [[TargetFunction]]  Object
                       :the function was created by bind, recored its origi function
      [[BoundThis]]    any
                       : The pre-bound this value of a function Object created using 
                         the standard built-in Function.prototype.bind method
      [[BoundArguments]] List of any
                       : The pre-bound argument values of a function Object created 
                         using the standard built-in Function.prototype.bind method.
      [[Match]]
      [[ParameterMap]]

4. Reference Specification Type
   A Reference is a resolved name binding. A Reference consists of three components, the base value, the referenced name and the Boolean valued strict reference flag. The base value is either undefined, an Object, a Boolean, a String, a Number, or an environment record . A base value of undefined indicates that the reference could not be resolved to a binding（还未绑定）. The referenced name is a String.
   
5  ToObject
      Underfined: Throw TypeError Exception
      Null:  Throw TypeError Exception
      Boolean:  Create a new Boolean Object whose [[PrimitiveValue]] internal property 
                is set to the value of the argument
      Number:  same up
      String:  same up
      Object:  

6. Object
    1. new Object([value]):
    if Type(value) is Object  -> return value 
                      String  -> ToObject(value)
                      Boolean -> ToObject(value)
                      Number  -> ToObject(value)
    if argument value was not supplied or its type was Null or Undefined
       let obj be a native ECMAScript object
       Set [[prototype]] to the built-in Object Prototype
       Set [[Class]] to the "Object"
       Set [[Extensible]] to the true
       Set all the [internal methods] of obj as specified in 8.12
       return obj
    [internal methods]: [[Get]]、[[GetOwnProperty]]、[[Put]]、[[CanPut]]
                        [[defineOwnProperty]]、[[HasProperty]]、[[Delete]]
    
    2. ALL Object Methods
       1. Object.getPrototypeOf(O)
          if o is not object -> TypeError
          else return the value of the [[Prototype]] of O
       2. Object.getOwnPropertyDescriptor(O,P)
          if Type(O) is not object -> TypeErroe
          Let name be ToString(P)
          Let desc be the result of calling [[GetProperty]] of O with argument name 
          return FromPropertyDescriptor(desc)
       3. Object.getOwnPropertyNames(O)
          if Type(O) is not Object -> TypeError
          Let array be the result of  new Array()
          Let n be 0
          For each named own property P of O
              a. use [[DefineOwnProperty]] of array with arguments
                 ToStings(n), ProDesc: [[Value]]:name, [[Writable]]:true
                                       [[Configurable]]: true [[Enumerable]]:true
              b. Increment n by 1
          return array
        4. Object.create(O[,Properties])
           if o is not Object -> TypeError
           Let obj be the result of new object
           Set the [[Property]] of obj to O
           if Properties is present and not undefined, add own properties to obj
           as if by calling Object.defineProperties with arguments obj and Properties
           return obj
        5. Object.defineProperty(O,P,Attributes)
           if Type(O) is not Object -> TypeError
           Let name be the ToSting(P)
           Let desc be the result of calling ToPropertyDescriptor with Attributes
           Call the [[defineOwnProperty]] internal method of the O with arguments name
           desc,and ture
           Return O
        6. Object.defineProperties(O, Properties)
        7. Object.prototype.hasOwnProperty(V)
           Let P be ToString(V)
           Let O be the result of calling ToObject passing the this value as argument
           Let desc be the result of calling [[GetOwnProperty]] of O passing P as arg
           if desc is undefined return false
           Return true
        8. Object.prototype.isPrototypeOf(V)
        9. Object.prototype.valueOf()
          1.Let O be the result of calling ToObject passing the this value as the 
             argument.
          2.If O is the result of calling the Object constructor with a host object, 
            then Return either O or another value such as the host object originally 
            passed to the constructor. The specific result that is returned is 
            implementation-defined.
          3.Return O.
        10. Object.prototype.toString()
            Let O be the result of the calling ToObject pass this value as arg
            Let class be the result of the [[Class]] internal property of O
            return String value "[object, class]”
        11. Object.seal(O)                             不可删除和添加
            if O is not Object -> TypeError
            For each named own property name P of O
                a. set [[Configurable]] is false
            Set the [[Extensible]] internal property of O to false
            Return O
        12. Object.freeze(O)                          不可修改、删除、添加   
            if O is not Object -> TypeError
            For each named own property name P of O
                a. set [[Configurable]] to false
                b. set [[Writable]] to false
            Set the [[Extensible]] internal property of O to false
            Return O
        13. Object.preventExtensions(O)
            if O is not Object -> TypeError
            Set the [[Extensible]] internal property of O to false.
            Return O
        14. Object.isSealed(O)
        15. Object.isFrozen(O)
        16. Object.isExtensible(O)
        17. Object.keys(O)
            if O is not Object -> TypeError
            Let n be the number of own enumerable properties of O
            Create array by new Array()
            For each own enumerable property of O whose name String is P
               a. calling [[defineOwnProperty]] of array with arguments ToString(index)
               b. Increment index by 1
            Return array
         18. Object.prototype.propertyIsEnumerbale(V)
            
             

【原型】： 优雅的继承是子对象独立的获得父类属性模板，多个子类共用一套方法  

原型链式继承： prototyped-based inheritance

          function Parent(value){
               this.xxx = value
          }
          Parent.prototype.xxx = function (){};
          function Children(){}
          Children.prototype = new Parent(value);
缺点：无法多次继承

寄生式继承：
          function Parent(value){
               this.xxx = value；
               this.xxx = function(){}
          }
          function Children(){
               Parent.call(this, value);
          }
          var cc = new Children();   
缺点：  直接在源对象上创建继承属性

组合式继承：
          function Parent(value){
               this.xxx = value
          }
          Parent.prototype.xxx = function (){};
          function Children(){
               Parent.call(this, value);
          }
          Children.prototype = new Parent(value);
          Children.prototype.constructor = Children;
          var cc = new Children(); 
 缺点： cc的属性与Children.prototype属性出现重复
 
组合寄生式继承： 
          function Parent(value){
               this.xxx = value
          }
           function Children(){
               Parent.call(this, value);
          }
          Parent.prototype.xxx = function (){};
          (function(){
             function F() = {};
             F.prototype = Parent.prototype;
             Children.prototype = new F();
             Children.prototype.constructor = Children;
          }());
          var c = new Childern(value);

Object was created 的其中两种方式:
           1. literal  {}
           2. constructor  new Fun()
其中， 在 constructor 中 Object’s prototype has an implicit reference to the value of constructor's prototype

Effective JavaScript：
  1. C.prototype属性是 new C()创建对象的原型
  2. Object.getPrototypeOf(obj) ES5标准获取 obj 原型的方法
  3. obj.__proto__ ES5非标准获取 obj 原型的方法
  4. 类是由一个构造函数和一个关联的原型组成的一种设计模式
  5. 使用标准的 Object.getPrototypeOf(obj) 而不要使用 非标准的 obj.__proto__
  6. 在支持 obj.__proto__ 的非ES5标准环境中实现 Object.getPrototypeOf()
  7. 始终不要修改 obj.__proto__属性
     (对象的原型链通过一套确定的属性以及属性值来定义它的行为，修改其中一个原型链就像大脑移植，会交换对象的整个继承层次)
  8. 使用 Object.create(prototype) 给新对象创建自定义的原型
  9. 使构造函数与是否记起使用new无关
     function User(name, password){
         if(! this instanceof User){
             return new User(name, password);
         }
         this.name = name;
         this.password = password;
     }  缺点： 额外的函数调用， 难适应于可变参数
     function User(name, password){
         var self = this instanceof User
                    ?this : Object.create(User.prototype);
         self.name = name;
         self.password = password;
         return self
     }  new 生的对象会被self 覆盖，因此该方法可行。
   10. 将方法存储于原型中优于存储在实例对象中，方法一般是【无状态】可被所有实例共享
   11. 利用闭包的方法将局部变量作为私有数据实现对信息的隐藏
   12. 将可变的实例状态存放在实例对象中而不是原型对象中
   13. 不要在子类中重用父类的名字
 数组和字典： 
   【原型污染】： 在使用for..in.. 进行枚举时，在原型上出现了我们不期望的属性
                所有人不应该在Object.protytype上增加新的属性。
   14 使用对象字面量的方式实现一个轻量级字典(原型直接继承的是 Object.prototype)
   15. 轻量级字典应该是 Object.prototype的直接子类，以防止for...in 的污染
   16. 创建空原型的方式
       function c(){}  c.prototype = null  Object.getPrototypeOf(o) === null false
       var c = Object.create(null)    Object.getPrototypeOf(c) === null true
   17. 使用for...in...循环来枚举对象属性应该与顺序无关
   18. 使用数组而不是字典来存储有序集合
   19. 聚集操作运算字典中的程序，应该确保聚集操作与操作顺序无关
   20. 绝不要在Object.prototype中增加可枚举的属性 避免【原型污染】
   21. 若在Object.prototype中增加属性，使用Object.defineProperty(), 将属性的是否可枚举设置为false
   22. 当使用for..in..枚举对象的一个属性时，确保不要修改该对象
   23. 迭代一个对象时，若对象内容会在一个循环期改变，考虑使用while、for代替for..in.. 循环
   24. 迭代数组索引应该总是使用for循环，而不是for..in..循环， （for in -> 索引是字符）
   
```

## 地图

```
JS 四种对象：
    native object: ECMAScript 定义且独立实现与宿主环境无关。 
                              ： Object、 Function、Array、Date、 RegExp、 Number
                                 Boolean、 String、 Error、EvalError、RangeError、
                                 ReferenceError、 SyntaxError、 TypeError、 URIError
    built-in object: ECMAScript 定义且独立实现与宿主环境无关，程序运行时无须手动初始化。
    【Only ONE】： global 对象
                      value properties of global : NaN、Undefined、Infinite                                                              NUll
                      Function properties of global :
                                                   eval(x) 、 isNaN(number)、  
                                                   isFinite(number)、 URI相关方法
                                                   parseFloat(string)、
                                                   parseInt(stirng, radix)
                          encodeURI(uri), encodeURIComponent(URicomponent)
                          decodeURI(encodeURI), 
                          decodeComponentURI(encodedURIComponent)
                                                   
                         Constructor properties of global: native Object
    注：  eval(x)在执行时若 x 不是 string 直接返回x
        2. URI:Uniform Resource Identifiers, or URIs, are Strings that identify 
            resources (e.g. web pages or files) and transport protocols by which to 
            access them (e.g. HTTP or FTP) on the Internet. 用于标识资源和协议
        
           结构： scheme：First / Secone ; Third ? Fourth
        
          URL 和 URN 是URI的不同方案的实现，共同点是参照URI语法结构规定资源的查找方式
        3. 快速检测 NaN 的方式 x ！== X 
        
    host object： 提供执行 ECMAScript 代码的环境，浏览器是DOM、BOM。
    user object： 用户自定义。
    
拆箱与装箱： 基本数据类型与引用类型相互转换 ，针对 primitive Value 中的 Boolean、 String、   
           Number 
      装箱： 基本数据类型通过包装函数转化为引用类型。
             var name = “zzj”                     var name = new String(“zzj”) 显示
             var i = name.slice()   隐式
后台会自动创建基本类型对应的对象，当调用方法后该对象会被自动回收
      拆箱： 引用类型转换为基本类型值
      
      发生拆箱的场所： 对象参与进行运算， 需要得到对象的 primitive value
      
隐式类型转换：
      触发的场景： +-*/ 、 逻辑运算：
       转换目的： JS无变量声明， 规定不同类型数据参与运算如何【统一】和【协调】
       具体说明：
            -*/:   限于 Number 类型运算
              +：  字符串拼接 和 Number 运算
                   规则：
                     优先级MMax: 一侧是 String 类型，识别为字符串拼接，另一侧转换为字符串类型。
                     优先级 Max：一侧是 Number， 另外一侧是非对象类型，另一侧转换为Number。
                     优先级 last：一侧是 Number, 另一侧是对象类型，同时转为 String 进行拼接。
         +-*/: 涉及所有类型转 Number， 所有类型转 String
           
           逻辑运算: 所有类型转 Boolean  
                   ： undefined、NaN、0、‘’、null、false
                   ： ｛｝[]  都为 true
            
            ==  ： null/undefined/NaN  primitive value 之间   primitive value 与 引用
                 1. NaN == NaN  false
                 2. undefined == null true   未赋值和值为空JS认作一个意思
                 3. undefined/null == other  false
                 4. NaN == other false
                 5. String 与 number 类型比较， String 会转化为 number类型
                 6. Boolean 与 其他类型相比较， 会首先转化为 Number 类型
                 7. 基本类型 与 引用类型相比较， 引用类型首先使用 toPrimitive 获得基本类型值
                     [] == ![]  ->  true, 因为[]被转换成0， 而不是先转boolean逻辑为true。
                  [undefined] 调用valueOf() 返回对象， 再调用 toString() 返回“”
       toPrimitive 调用顺序： valueOf() --> toString(), 依然失败返回 TypeError
       
  对象类型转换为基本数据值：
                          Boolean   Number      String
    Object ： ｛｝           true      NaN      "[Object Object]” 15个字符
  Function: function(){}    true      NaN      "function(){}"
    Array:    []            true       0        ""
            ["123"]         true       123      "123"
            ["abc"]         true       NaN      "abc"
            
 总结： 基本数据类型都具备 valueOf()方法 、 toString()方法。 valueOf方法返回 primitive 值
      主要是在使用这些对象时方便获取基本值。 然后所有对象都拥有转换为字符串的方法。

1. 对象的属性类型： 数据类型、 访问器类型、  内部属性
2. 对象属性的Attribute： Value、 Writable、 Configurable、 Enumerable、 Get、 Set
3. 对象共有的内部属性： [[Property]] 、 [[Get]]、 [[Put]]、 [[GetOwnProperty]]
                    [[HasProperty]]、 [[Delete]]、 [[CanPut]]、 [[DefineOwnProperty]]
                    [[Class]]、 [[GetProperty]]、 [[Extensible]]
4. 特别对象的内部属性： [[Scope]]、 [[Code]]、 [[Constructor]] 、 [[PrimitiveValue]]
                    [[Call]]、  [[BoundThis]]、 [[TargetFunction]] [[HasInstance]] 
                    [[FormalParameters]]、 [[BoundArguments]]、 [[Match]]
                    [[ParameterMap]]
5. Object函数自身的方法： .getPrototypeOf(obj)                返回原型
                       .getOwnPropertyDescriptor(O, p)
                       .getOwnPropertyNames(O)
                       .create(O[, Properties])
                       .defineProperty(O, P, Attribute)
                       .defineProperties(O, Properties)
                       .seal(O)              // 返回o
                       .freeze(O)            // 返回0
                       .prevenExtensions(O)  // 返回O
                       .keys(O)   // 返回数组，获得对象自身所有可迭代的属性
                       .entries(O) // 返回数组，子元素同样是数组，[key, value]可迭代
                       .isSealed(o)
                       .isFrozen(o)
                       .isExtensible(o)
  Object函数原型链上的方法：.prototype.hasOwnProperty(P)
                        .prototype.toString()
                        .prototype.valueOf()
                        .prototype.isPrototypeOf(P)
                        .prototype.propertyIsEnumerable(V)
                        
6. Array函数的方法：
                    .isArray(arg)
                    .prototype.concat([],[])
                    .prototype.join(separator) // 返回字符串
                    .prototype.pop()          
                    .prototype.push([item1[,item2[,..]]])
                    .prototype.reverse()
                    .prototype.shift()  // 删除最后一个元素并返回
                    .prototype.slice(start, end)
                    .prototype.splice(start, delCount, xx1, xx2)
                    .prototype.unshift([item1[,item2[,...]]])
                    .prototype.indexOf(searchElement[,fromIndex])  内部用 === 判断NaN出错
                                       // 返回寻找到的第一个元素pos，无-1
                    .prototype.lastIndexOf(searchElement[,fromIndex])
                    .prototype.reduce(callback,inintalValue)
                    .prototype.sort(callback);  // 
                    .prototype.map(callback，this);
                    .prototype.some(callback，this);  // 返回一个true，只要有一个元素符合条件
                    .prototype.every(callback，this);  // 返回true， 所有元素都需要符合条件
                    .rpototype.filter(callback，this) // 返回一个符合条件的元素数组
          ES6新增    .prototype.find(callback)        // 返回第一个满足条件的元素，无undefined
                    .prototype.findIndex(callback)   // 返回第一个满足条件的元素，无undefined
                    .prototype.includes(xx)  // 返回 true /false
                    .fill(val)              // 按照数组长度填充val，已有元素会覆盖，长度为0不填充
                    .flat(num)              // 展品的层数， 默认为1， 可填入Infinity
                    .flatMap(callback)     // 先对数组内元素操作，再调用flat(1)
                    .entries()              // 返回迭代器， value：[索引， 键值]
                    .keys()                 // 返回迭代器， value:key
                    .values()               // 返回迭代器， value：value
                    .copywithin(target, start, end=this.length) // 复制元素到指定位置
                
                    
                    
                    
                    
```






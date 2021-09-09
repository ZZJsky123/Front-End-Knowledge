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
     4. else set ThisBinding -> thisArg                                            
     5. loalEnv = new DelcarativeEnvironment([[Scope]])            
     6. Set the LexicalEnvironment to localEnv.                                   
     7. Set the VariableEnvironment to localEnv.
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
           双重非运算符：  ！！arg    显示的将 arg 转化为 boolean ，true-->true  false -->false
            
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
            
   其他类型转为字符串：  null, undefined  --->  'null' 'undefined'
                     Boolean --->  'true/false'
                     Number ---->  'number'; 超出范围会用指数的方式
                     Object ---->  除非自行定义toString, 否则调用 Obejct.prototype.toString.call()
   其他类型转为数字：   undefined ---> NaN
                     null --->  0
                     Boolean --->  0/1
                     String   ---->   NaN/Number
                     Object 先转为相应的基本类型值，再按照上述规则
            
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
                    .Array.from(类数组/可迭代对象， mapFn， this)  将一个类数组或者可迭代对象转化为数组，浅拷贝。
                                                                mapFn是回调函数，输入值是数组成员：返回一个
                                                                新值替代旧值，this 是mapFn时的对象
```

## 基础

```
1. JavaScript 7个 基本类型：
   a. null              空值
   b. undefined         未定义
   c. number
   d. boolean
   e. string
   f. object
   g. symbol
   
   Symbol： 定义独一无二的值， 提出背景主要解决混入第三方对象名字冲突的问题， 使用 Symbol('descriptor')
            描述会创建一个独一无二的值， descriptor 是描述符， 即使多处创建描述符相同的 Symbol 他们的
            值也不会相同。 Symbol('descriptor') 生成的值一旦没有被变量捕捉，则无法被搜索到。
            
        a.  let s1 = Symbol()    Symbol 的创建形式， 不能使用 new 操作符。
            console.log(s1) // Symbol()
            s1.toString() // 'Symbol()’
        
        b.  let a = {[s1]: val }  Symbol 作为属性访问和赋值必须使用 []。
        
        c.  Symbol 不能进行 + - 运算
        
        d.  Symbol 作为属性不能被 for...of、 for...in 、 Obj.keys() 、
            Object.getOwnPropertyNames() , Json.Stringify() 返回
            使用 Object.getOwnPropertySymbols() 访问
        
        e.  Symbol.for('descriptor'):  在全局注册 Symbol 值，并将该值返回
            使用 Symbol.for() 会在全局(即使当前环境不是全局)检查是否有该 Symbol
            如果有则返回该值并赋值给变量， 若没有则注册该描述符。
            Symbol.keyFor(变量)  返回 Symbol 值的描述符。
        
        f. 单例模式：调用一个类， 任何时候返回的都是同一个实例。
        
2. 类型检测：
   a. typeof  可以检测出来： undefined、 number、 boolean、 string、 function、 object
   b. typeof 会将 null 检测成 object 因此识别 null 可以用 ===  
   c. instanceof 用于识别对象类型， 即左边对象的原型链中是否存在右边构造函数的原型
   d. Object.prototype.toString.call(obj) 返回："[object Native object]" 
   e. 检测 NaN 和 Finite 用全局方法： isNaN()、 isFinite()
   f. 检测数组除了使用 instanceof 也可以使用 isArray() 函数
   
  总结： typeof 用于检测7个基本数据类型， 其中 null 的检测要使用全等符号
        Object.prototype.toString.call 用于检测所有 native object
   
3. 类型转换
   
   a. + 中涉及到的类型转换：
       I： string + any 时， any会转换成string， 并发生字符串拼接。
       II. number + 非引用类型， 非引用类型会转换成 number
       III. number + 引用类型， 两边都转为 string
       IV.  若两边全是对象类型， 两边同时调用自己的 toString() 函数进行拼接。
   注： {}.toString()  [object Object]
       []. toString()  ""
       fun.toString()  "function(){}"

   b. == 中涉及的类型转换
      I. null 和 undefined    null == undefined：true, null/undefined == any: false
     II. NaN == any : false
     III. Number == String   String 会被转化成 Number
          boolean == any     boolean 会首先转化为 Number
          基本类型 == 引用类型  引用类型 会调用toPrimitive() 获取基本类型值
     Iv： 引用类型 == 引用类型  比较地址，若比较不同地址上的对象是否相等，需要人为自己定义
     
4. 原型：每个对象上都有一个内部属性 __proto__, 其值是一个对象，被称作对象的原型对象，原型对象
        上也具备 __proto__ 属性， 因此形成了一条原型链， 原型链的终点是 Object.prototype
        的内部属性 __proto__, 其值为 null。通过原型链实现继承。
        
   a. 对象的原型存储在 _proto_
   b. 函数的原型存储在 prototype
   c. 在原型对象上储存着 contructor 属性，其值：fun ，指出用于当前构造对象的构造函数。
   d. 可以通过 Object.getPrototypeOf(obj) 获取 obj 对象的原型
   e. 可以通过 Object.setPrototypeOf(obj, proto)  设置 obj 对象的原型。
   f. new Fun(): Fun 为构造函数， 其会生成一个空白对象obj， obj.__proto__ = Fun.prototype
      并将该对象作为 this 值传入函数， 若无其他引用类型返回，则返回该对象。
   g. Fun.__proto__ = Function.prototype  其类型是一个函数
      
5. 创建对象的三种方式：
        var obj = {};       // 创建一个空对象，obj.__proto__ = Object.prototype
        var obj = new Fun() // 创建 Fun 的实例对象， obj.__proto__ = Fun.prototype
        var obj = Object.create(原型对象， 新的对象属性描述) 
                           // 使用 Object.create 创建一个新对象，新对象的原型是函数的第一个参数
        e.g: var obj = Object.create(p, {'name':{value: xx
                                                 writable:xx
                                                },
                                          'age': {
                                             value:xx
                                             writable:xx
                                          }
                                         
                                         })
              var obj = Object.create(null)  //  obj.__proto = null;
              
        
6. 作用域： 执行当前函数会创建执行上下文， 并将当前函数压入到执行栈中， 开始执行时会调用  
           NewDeclativeEnvironoment([[scope]])， 该函数会创建一个词法环境， 该词法环境有两个属性： ER 和 outter
           outter 用于引用外部的作用域， 将传进的参数 [[scope]] 赋给 outter 使得当前作用域可以引用外部作用域。 
          
           该词法环境会被赋值给 作用域中 LexcialEnvironment 和 variableEnvironment， 在 ES5 中， 函数声明 和 变量声明
           都记录在 variableEnvironment 中， 而 ES6 中 variableEnvironment 只记录 var 变量。 闭包的核心是 内部函数的
           词法环境对外部作用域的引用，使得内部函数可以操作和使用外部函数的作用域和变量。
           

6. 宏任务 与 微任务
   
   a. 主线程执行完,会先访问微任务事件队列， 将微任务队列中的所有函数压入主线程中执行
      当所有微任务执行完后，会访问宏任务队列， 将一个宏任务压入主线程中执行， 执行完毕
      进入下一个周期。
      
   b. 常见的微任务：Promise   MutationObserver()
   
   c. 常见的宏任务： setTimeout()    setInterval()
   
   e. 执行流程：  主线程任务 -> 所有微任务 -> 从宏任务队列中读取一个宏任务。
   
7. get 和 set :  两种定义对象的方法

   a. 在对象中定义 get 和 set
      obj = {
         _num: 1
         
         get num(){            // obj.num = 调用 get 函数， 其值为 get 返回的一个值
            return this._num;
         },
         
         set num(val){       //  obj.num = xx , xx 会作为 set 的参数而立即调用
             this._num = val
         }
      }
   b. Object.defineProperty(obj, xx, {
      value:      值/函数
      writable：
      configurable:
      enumerable:
      
      get:function(){}   定义 get 不能定义 value 和 writable， 访问属性时决定返回值
      set:function(){}   定义 set 不能定义 value 和 writable， 为属性赋值时决定返回值
       
     //  set 和 get 可以不同时定义，将它们都理解成代理函数， get 是在获取值之前将值截取， 操作
     //  set 定义的属性不能期望它是一个函数， 它只有在被赋值时才会触发
     //  若属性是函数两种代理方法：  a. value 定义成函数   b. get 中返回一个函数
     //  不能在 get 中触发 get 会无限次递归直到栈溢出。      
   })
   
     如果使用 Object. defineProperty 定义某个属性的 get 和 set， 证明该属性是代理属性， 用于对某个
   属性进行代理， 所有要不代理全局变量，要不代理局部对象。 get 属性中不能存在对当前属性的访问， set 不能
   存在对当前属性的赋值。
      
      (function (){
          let inner = 0;
          
          Object.defineProperty(obj, 'xx', {
              get(){return inner};
              set(val) inner = val;
          })
      })
   
   
```

```javascript
let arr2 = [1,2,3];
let arrPro = Array.prototype;

Object.defineProperty(arr2, 'push', {
  configurable: true,
  enumerable:false,
    
  value:function mutation(...val){
     
     console.log('before:', arr2);
     let push = arrPro.push;
     push.call(arr2, ...val);
    
     console.log('after:', arr2);
   },
    
  get:function(){
    return function(...val){
     console.log('before:', arr2);
     let push = arrPro.push;
     push.call(arr2, ...val);
    
     console.log('after:', arr2);
    }
  },
})
```



## 重点

```javascript
1. 继承： 构造函数的方法置放在 prototype 属性上， 继承属性置放在传入的 this 对象上， 此时
         子类的实例对象共同拥有一份父类方法， 各自独立拥有一份父类属性。
   function Parent(){
      this.pro1 = 'xxx';
  }
   Parent.prototype.fun1 = function(){};
   function Child(){
       Parent.call(this);
   }
   child.prototype = function(){
     function F1(){};
     F1.prototype = Parent.prototype;
     return new F1();
   }();
   Child.prototype.constructor = Child;
   let kid = new Child();

2. 闭包原理：  内部函数使用了外部函数的变量时会创建一个闭包作用域， 不管该函数有没有返回到外部。 当外部函数中
             存在多个内部函数时，只要有一个内部函数使用外部变量都会创建一个闭包作用域。 外部函数执行完不被回收是
             因为将闭包函数返回， 只要外部作用域不会被回收掉， 闭包变量可达因此会一直保留。

4. 模块化：
      a. 模块化的核心： [量小]、[组织良好] 的代码比庞大的代码更具有理解性和可维护性，避免全局污染和提高
                      代码的重用性。
      
      b. 立即执行函数实现模块化：  
               function MouseClickCounts = function(btn){
                   const clickCount = 0;                           // 模块的私有变量
                   const handleclick = function(){ clickCount++ }; // 模块的私有函数
                   
                   return {                           // 返回对象，对象具有 clickControl 接口
                       clickControl: () => {
                           btn.addEventListener('click', handleclick);
                       }
                   }
               }();

           模块扩展：
                (function modle(model, btn){
                  const wheelCount = 0;
                  const handlewheel = function(){ wheelCount++ }
                  
                  model.controlWheel = () =>{
                      btn.addEventListener('wheel', handleWheel);
                  }
                })(MouseClickCounts)
           缺点： 模块依赖问题。
           
      c. AMD 解决方案： 设计理念明确基于浏览器  require.js 和 curl.js 实现 AMD 标准
             I. deine('模块名'， ['模块依赖列表']， 模块函数) 模块函数中的返回对象作为
                导入时使用的接口。
             
             II. 一个文件可以定义多个模块， 自动收集模块依赖， 依赖是异步加载不会阻塞之后的程序
             
             III.require(['模块名列表']， callback): 导入依赖模块，导入成功后触发回调。
             
             IV. require 加载模块列表默认是这些模块与当前文件在同一个文件夹下， 若不在
                 需要在当前文件顶部设置 ： require.config = {
                     
                                          baseUrl: '基路径'   Path 会在当前路径下查找    
                                          paths: {
                     
                                               '模块名'： （基路径/)lib/xx.js
                                           }
                                      }
             
      d. CommonJs： 同步加载模块 Node.js 使用人数最多
             I. 一个文件只能定义一个模块

             II. require('模块路径'): 导入依赖模块
             
             III. module.exports = 文件中需要导出的变量或者函数 

             IV.  服务器端可以使用同步加载模块， 因为模块都存储在本地，运行时可以先行读取
                  读取的快慢取决于硬盘速度， 而浏览器不能使用同步加载，因为其读取的快慢取
                  决于网络
             
             V. 例子：      const $ = require("jQuery");
                            let numClicks = 0;
                            const handleClick = () =>{
                                alert(++numClicks);
                            };

                            2. 定义公共接口
                            module.exports = {
                               countClicks: () => {
                                  $(document).on("click"， handleClick);
                               }
                            };

                            在另个一文件中：
                            const MouseCounterModule = require("MouseCounterModule.js")
                            MouseCounterModule.countClicks();

4. Promise：

   a. Promise 异步编程方案， 其提出背景是解决第三方异步函数不信任问题， 回调地狱写法复杂问题
      Promise 的特点是： 控制反转、 状态唯一、 链式调用。
      
   b. 新建 Promise 实例， 输入参数为一个执行器： new Promise( executor )
      执行器是一个函数，其接受两个参数 resolve 和 rejected， 其作用是执行异步
      事件逻辑， 当事件完成后，改变当前 Pending 状态， 并将事件结果送给 resolve
      或者 reject 函数 ， 触发事件的回调函数。
      
   c. 事件回调函数定义在 then 方法中， then((res) =>{
                         // 定义事件触发成功时执行逻辑
                   }, (err) =>{
                        // 定义事件失败时执行的逻辑
                   })
      then 方法一定会返回一个 Promise， 当回调函数返回一个 Pormise 则 then 方法将其返回
      若回调函数返回一个基本数据类型 then 方法将其包装成 Promise 并将 Promise 的值设定为
      当前值；若回调函数无返回值， 则自动调用 Promise.resolve() 新的 Promise 的值是undeined。
      
   d. then 方法中输入值若不是函数， 则会发生穿透，即将第一个有值的 Promise 传递给下一个 then 方法
   
   e.  等...完成， 我再...   （我再后面的内容一定是放入在 then 中的。
   
   f. 使用 Promise 注意：
       a. exuctor 中的 resolve 函数 如果接受到是一个 Promise 对象， 会等 Promise 对象决策
          完成后再触发 then 函数。
   g. catch 后的 then 依然会触发， 如果错误在 then 中处理了， 则不会再触发 catch
   
   l. Promise.prototype.Method:
          I. Promise.prototype.all: 函数输入一个 Promise Iterator， 返回一个 Promise ，Promise
                                    的值是一个数组(记录所有 Promise 的值)或者是一个 err 信息
                 
              Promise.prototype.all = function(arr){
                  
                  if(!arr[Symbol.iterator] && typeof arr[Symbol.iterator] != 'function'){
                      throw new Error('')
                  }
                  
                  let res=[], len=0;
                  return new Promise((resolve, reject) => {
                      for (let i of arr){
                          Promise.resolve(i).then((r) =>{
                              res[len++] = r;
                              if(len == arr.length ){
                                   resolve(res);       
                              }
                          }, (err) => {
                              reject(err);            // 任意一个出错立即返回
                          })
                      }
                  })
                  
              }

         II. Promise.prototype.race： 迭代器中只要任意一个 Promise 改变状态， 返回的 Promise 立即
                                      改变状态。
                Promise.prototype.race = function(arr){
                  
                 if(!arr[Symbol.iterator] && typeof arr[Symbol.iterator] != 'function'){
                      throw new Error('')
                  }
                  
                 return new Promise((resolve, reject) => {
                     
                     for(let i of arr){
                         Promise.resolve(i).then((res) => {
                             resolve(res)
                         }, (err) => {
                             reject(err);
                         })
                     }
                 })
                    
                }    

         III. Promise.prototype.any : 与 all 方法相反，如果迭代器中任意一个 Promise 状态改为
                                      fullfilled 返回的 Promise 对象状态改变。 若所有 Promise
                                      都拒绝，则将错误信息作为返回的 Promise 的值。
              Promise.prototype.any = function(arr){
                 if(!arr[Symbol.iterator] && typeof arr[Symbol.iterator] != 'function'){
                      throw new Error('')
                  }
                  
                  let res=[], len=0;
                  return new Promise((resolve, reject) => {
                      for (let i of arr){
                          Promise.resolve(i).then((r) =>{
                             resolve(r);       
                          }, (err) => {
                              res[len++] = err;
                              if(len == arr.length ){
                                   reject(res);       
                              }
                          })
                      }
                  })
              }

          IV. Promise.prototype.try: 输入参数是一个函数， 函数可以是同步函数也可以是异步函数。
                                     该函数会当 f 是同步函数时按照同步方式执行， 异步函数时
                                     按照异步方式执行。
              Promise.prototype.try = function(f){
                  f = typeof f == 'function' ? f : () => f;
                  
                  return new Promise((resolve, reject) => {
                     try{
                         resolve(f());
                     }catch(err){
                         reject(err);
                     }
                  })  
              }

5. Iterator 对象：
         a. 背景： 提供不同数据结构相同的遍历方法： for...of 、 ...[], 凡是实现了迭代器都可用上述
                  方式进行判定。 
            形式： Iterator 是一个对象，拥有 next 属性， 该属性是一个函数， 凡对象满足上述者被称为
            迭代器对象。
         
         b. 
          I. xx[Symbol.iterator] = fun , 凡是拥有 [Symbol.iterator] 属性， 且属性值是一个
             函数，则判断数据可以迭代。
         II. 函数返回一个 {next: next} 对象，其上有一个属性 next 函数类型，每次调用该函数返回： 
             函数又被称为 [迭代器生成函数] 
                              { valu：value  done：false/true }
         
         c. 实现 Iterator 的本地数据： Array、 Map 、 Set、 String 、 arguments
         
         d. for..of  、 ...Iterator  可以对迭代器进行遍历而不需要调用 next 方法
         
         
6. Generator： 
         
         a.  Generator 是状态函数， 该函数调用后会返回一个 Generator ， 用这个对象上的 next 方法
             去遍历函数的内部状态， 函数的内部状态定义在 yeid 后， 除去第一次遍历以外， 每次都是从
             yeid 开始，yeid 后的状态值会被返回， 向下执行，直到遇到下一个 yeid 为止。
             
         b. 形式：  function * f(){
                     let a = 1 + yeid 3
                     return a
                    }
                   let iter = f()
                   iter.next()    //  {value:3,  done:false}
                   iter.next()    //  {value:NaN, done:true}
            yeid 3 只告诉迭代器当前状态是 3， 但是 yeid 3 整体无返回值， 返回 undefined
            内部 return 返回的值作为最后的 value 值， 若无 return   value：undefined

        c. iter.next(value) : 向 next 送入 value 作为上一个 yeid staus 的返回值。
           
        d. yield 推送的状态如果用在另一个表达式之中， 必须放在圆括号里面
           function * demo(){
            console.log('Hello' + (yield));
            console.log('Hello' + (yield 123));
           }
                  
        e. Generator 返回一个 Generator 对象 ， 可以直接作为 [Symbol.iterator] 属性的值， 
           Generator 中的状态作为迭代器返回的结果。 fun.prototype 存放的是 Generator 对象
           即函数调用返回的 Generator 对象， let iter = fun.call(fun.prototype) 则 fun
           的 this 值设置成了 Generator 对象， 添加的属性都可以在 iter 中找到。
           
        f. Generator.prototype.throw: 在 Generator 函数体外抛错， 在 Generator 体内捕捉
                var g = function* () {
                      try {
                        yield;
                      } catch (e) {
                        console.log('内部捕获', e);
                      }
                    };

                    var i = g();
                    i.next();                  // 抛错之前必须使用一次 next 方法

                    try {
                      i.throw('a');
                      i.throw('b');
                    } catch (e) {
                      console.log('外部捕获', e);
                    }
         i.throw() 第一次调用时， 错误会被内部的 try-catch 捕捉， 捕捉完成后若之后有 yield
           继续运行执行下一次的 yield 后停止。 第二次再调用 i.throw()则错误只会在外部捕捉，即使
           函数中有第二个 try-catch 也不会捕捉。 
       
      g. Generator.prototype.return : Generator 遍历停止函数， 将 return 作为 终值
         done： false， 利用该函数可以在外部停止遍历器运行。
         
      f. yield *Generator() : 用于遍历内部的 Generator 函数， 不需要在内部手动调用 iterator 函数
         该语法相当于： 将该行替换成    for(let val of Generator()){
                                      yield val;
                                   } 
         因此外部调用相应次数的 next()， 每次都会读取 val。 但是这种语法只能在 Generator 内部使用。
         function * concat(iter1, iter2){
             yield * iter1
             yield * iter2
         }
         for(let val of concat('str1', 'str2')){
             res.push(val);
         }
         res:['s','t','r','1','s', 't', 'r', '2']
                        

7. Async: ES6 异步编程方案 : Generator 语法糖
   
     a. async 代替 * 声明  

     b. await 代替 yield， 执行后面 Promise 的同步部分，并阻塞后面执行， 直到 Promise 状态改变。
        其返回状态改变后的 Promise 的值， await 后如果没有跟 Promise/thenable 对象则直接将该值
        返回。一旦 await 后有一个 Promise 发生错误 ， Async 停止将该错误抛出，用外部 catch 捕捉。
        若不想停止执行，需要内部使用 try-catch 或者 Promise 后跟 catch 可以阻止全局停止。 书写时
        建议在内部捕获错误，从而保证函数执行完。
        
     c. 内置执行器， 不需要人为调用 next 执行， Async 会和普通方法一样，用一行执行。
     
     d. 返回一个 Promise， 其详细状态未知, 若函数有返回值则，Promise的返回值是函数的返回值
     
     e. 返回的 Promise 需要等内部 await 后的所有 Promise 状态改变才会发生状态改变。
        即使 await 后不是异步事件，也会阻塞后面的代码运行。
     
     f. async 的 return 返回的值，会作为返回的 Promise 值，传入到 then 的回调函数中。
     
     g. 注意事项：
         I.或者 Promise后跟 catch 可以阻止全局停止

                    async function main() {
                      try {
                        const val1 = await firstStep();
                        const val2 = await secondStep(val1);
                        const val3 = await thirdStep(val1, val2);

                        console.log('Final: ', val3);
                      }
                      catch (err) {
                        console.error(err);
                      }
                    }
         II. 若前后的 await 没有关系， 可以考虑将他们同时触发
                 写法一：  async function foo(){
                               const res = await Promise.all([p1, p2, p3])
                           }
        III. async 可以保存运行栈
            const a =async () => {
                await b();
                c()
            }
            解释： a 必须等 b 运行完才可以向下运行， 因此 b 运行完依然处于 a 的运行栈中。
    
8. ES6 类语法

       a.  class A {}            

       b.   xx = 1;                 // 实例属性开头顶格写
            xx = 2;

       c. 构造器函数： constructor(){             
                        thix.xx = a        // this 指针指向类实例。
                     }  

       d. 实例方法： Method1(){       // 不需要 function 变量， 方法都在类的 prototype 上
                                    //  且不可枚举
                   }

       c. 静态方法： statci Method3(){        // 静态方法
                       this.xx = a;         // this 指针指向类，而非实例
                   }

       d. 读取器和存储器： get name(){              // 获取器 getter
                        }
                        set name(){              // 存储器 setter 
                        }    
          等价于使用 Object.defineProperty(obj, pro, {..})

       e. 私有属性和方法： ES6 没有明确的私有属性和方法提案
                I. 约定俗称： 变量名和方法名在开头有一个 _ 则说明此只在内部使用，但是外部依然可以
                            访问到。
                II.  在 class 外部定义方法和变量名
                III. 方法和属性名使用 Symbol

       f. 
           I. 类名可以在当前类使用， 指代当前类。
          II. 类必须使用 new 运算符
          III. 可以采用表达式的方式定义方法 [argName](){}   argName 是 String 类型或者 Symbol
          
      类继承：
          
       g. class B extends A{        super 只有在构造器中可以作为函数使用， 且必须使用
               constructor(){
                   super()          // 子类的 super 在构造器中作为函数使用，该函数代表父类的构造函数
                   super.x = 3;
                   console.log(super.x); // undefined 相当于访问： A.prototype.x
                   console.log(this.x); //  3 
               }         
          }
          调用 super 返回的依然是 B 的实例对象， super = A.prototype.constructor.call(this)
          即 super 内部的 this 指向当前实例。
          
      
       h.  调用 super 作为对象时， super = A.prototype , 可以在继承的方法中使用 super 调用父类方法
           但父类的实例属性无法访问。
   
       l.  class A {}   class B extends A{}
           B.__proto__ = A                        // B 的原型是 A
           B.prototype.__proto__ = A.prototype    // B.prototype 的原型是 A.prototype 
           上述等价于 Object.setPrototypeOf(B, A)
                    Object.setPrototypeOf(B.prototype, A.prototype)

           class A{}    若 A 是基类，无继承
           A.__proto__ = Function.prototype      // A 是一个函数其原型是 Function.prototype
           A.prototype.__proto__ = Object.prototype;  
           注： Function.prototype 是一个函数。
           
9 模块化： 将 [复杂系统] 分解成多个模块方便编码， 模块化的职责：[避免全局变量污染]、[数据保护]、[相关联模块的依赖维护] 

       a. // index.html
            <script src="./mine.js"></script>
            <script src="./a.js"></script>
            <script src="./b.js"></script>
            // mine.js
            var name = 'morrain'
            var age = 18

            // a.js
            var name = 'lilei'
            var age = 15

            // b.js
            var name = 'hanmeimei'
            var age = 13
         最原始没有模块化， js 文件被引入到 html 网页中后，文件没有作用域， 三个文件中的变量都会存在于全局变量中
         
         开始使用命名空间解决不同文件变量名冲突的问题：
         // index.html
            <script src="./mine.js"></script>
            <script src="./a.js"></script>
            <script src="./b.js"></script>
            // mine.js
            app.mine = {}
            app.mine.name = 'morrain'
            app.mine.age = 18

            // a.js
            app.moduleA = {}
            app.moduleA.name = 'lilei'
            app.moduleA.age = 15

            // b.js
            app.moduleB = {}
            app.moduleB.name = 'hanmeimei'
            app.moduleB.age = 13
         使用变量名空间，减少了变量名冲突，但是命名空间所有的属性都会暴露给使用者，导致有修改风险 (js 中没有私有变量)
         
         开始使用立即函数，通过闭包的方式的创建私有作用域
         // index.html
            <script src="./mine.js"></script>
            <script src="./a.js"></script>
            <script src="./b.js"></script>
            // mine.js
            app.mine = (function(){
                var name = 'morrain'
                var age = 18
                return {
                    getName: function(){
                        return name
                    }
                }
            })()

            // a.js
            app.moduleA = (function(){
                var name = 'lilei'
                var age = 15
                return {
                    getName: function(){
                        return name
                    }
                }
            })()

            // b.js
            app.moduleB = (function(){
                var name = 'hanmeimei'
                var age = 13
                return {
                    getName: function(){
                        return name
                    }
                }
            })()
         不够优雅和完美，当项目变的逐渐大的时候，模块之间的依赖难以管理。
          
       a. jquery 库加载完毕后，它的 API 全放在了 window.$ 中，有命名空间冲突的危险
          比如相同库也把自己的 API 放在 window.$ 中。
       
          
       b. commonJS规范: 
               a. 每一个文件是一个模块，有自己的[作用域], 文件里定义的变量、函数、类都是私有的对外不可见
               b. 每一个模块都有两个变量可以用： require / module, require 用于导入模块， module 是
                  当前模块对象，其上有一个属性 exports 我们将需要导出的变量、函数、类放在 exports 中
               c. exports = module.exports, 相当于其别名， 主要不能直接将变量赋给 exports， 这样
                  只会改变 exports 中的指向。 
               d. 若模块对外导出只是一个单一的值， 直接对 module.exports = xxx 赋值
               e. require 基本的执行方式是加载一个模块：[执行文件] 后返回这个模块的 exports 对象
               f. require 的是被导出的值的拷贝。也就是说，一旦导出一个值，模块内部的变化就影响不到这个值 。
                  require 是浅拷贝。
               g. 加载的模块要具备缓存
         ES6 module 和 CommonJS 的区别： commonJS 中的 require 是运行时才能够知道导出的内容
                                       import 是 在编译时已经能够确定导出的内容，因此他有一个提升效果。
```

## 设计模式

```javascript
代理：
    a. 代理对象/方法
    b. 唯一的工厂：代理的发生场所
    c. 返回一个新的对象/方法
  
   1. 单例模式： 保证全局只有一个对象， 当新建新对象时返回的是已经创建的对象
      
    function Person(name){
        this.name = name;
    }
    Person.prototype.getName =  function(){ console.log(this.name)};
    
    let singlePerson =  function () {       // 单例加工工厂
        let instance = null;                 // 唯一一位员工
        
        return (name) => {
            if(instance){
               return instance;
            }else{
               return new Person(name);
            }
        }
    }()
    let singlePerson = new singlePerson('zzj');

   function singleFactory(obj){           // 真正意义上制造各种单例的工厂
       
       let factory  = function (obj){    // 制造单例的产品线
       let instance = null;   
           
        return (...args) => {
            if(instance){
               return instance;
            }else{
               return new Person(...args);
            }
        }
       }()
       factory.name = obj.name + 'Factory';
       
       return factory；
   }
```

## 问题与理解

```
1. JS 几种类型值的内存图
  a. 基本类型的值保持在栈中；复杂类型的值保持在堆中，通过栈中保存对应指针来获取堆中的值。

2. 堆和栈的区别和联系
  a. 在数据结构中栈存放数据的方式是先进后出， 堆是一个优先队列按照优先级进行排序。
     在操作系统中，栈用于存放函数的参数值，局部变量，大小固定，[查询效率高]，其占用的内存由编译器自动分配释放。而堆区内存一般由
     程序员自己分配和释放，或者交由垃圾内存回收机制。

3. 内部属性[[class]]是什么
   a. typeof 的结果是 object 的对象， 其都有一个内部属性 [[class]] 无法直接被访问，可以通过 
      Object.prototype.toString.call(obj) 访问。 内部[[class]] 的值一般和它原生的内建构
      造函数相对应。  null 和 undefined 不是对象

4. JS 的内置对象
   a. 在 ES5 标准中，一共定义了四种对象： built-in object、 native object、 host object、 user object
      built-in object 是独立于环境，运行时自动初始化，我们称为全局对象，它有以下几个属性：
      值属性： null， undefined， infinite， nan
      函数属性： isNaN， eval， parseFloat， parseInt()
      构造器属性： Function， Data， Number 所有的 native object 

19  闭包怎么实现的
    js 的作用域链：js 以函数作为基本的执行单元， 执行函数时，会创建词法环境，词法环境有两个属性： ER用于记录函数内部的
                 的变量， outter： 用于记录所在执行上下文的词法环境，其值就是内部属性[[scope]] 的值，正在执行函数中
                 的内部变量对象称为 AO， 其作用域链上的对象称为 VO， 作用域链： A0 + scope chain， 即AO+VO
    闭包的实质是内部函数引用与它外部函数上的变量或者函数时，会创建一个闭包，闭包函数对象包含一条作用域链，当它被返回且被外部变量
    对象接受，只有外部作用域不退出， 这条作用域链就不会被垃圾清除。

5. null 和 undefined 的区别  (基础)
   a. null: 基本数据类型，其值的意义是一个空对象
   b. undefined： 基本数据类型，其值的意义代表变量未定义， undefined 不是保留关键字，可以用作变量名
   c. null == undefined 为 true
   d. 变量值为 null 会被垃圾回收掉

6. undefined 和 undeclared 的区别

7 如何获取安全的 undefined 值
  a. void 0 来获取安全的 undefined， 保证 undefined 不是一个变量名

8. js 整数的安全范围是多少
   a. 安全范围值
      上限： Number.MAX_SAFE_INTEGER
      下限： Number.MIN_SAFE_INTEGER
   b. 超过安全范围，会返回 Infinite， 可以用 isFinite 进行检验

9. isNaN 和 Number.isNaN 函数的区别
   a. isNaN 接受参数后会将这个参数转换为数字， 任何不能转为数字的的值都会返回 true
   b. Number.isNaN, 接受参数后会判断这个是否是数字，是的话再判断是否为 NAN， 更加准确。
--------------------------------------------------------------------------
22 Ajax 解决浏览器缓存问题 (题号：57)
   若请求资源时不希望读取缓存：
   ajaxObj.setRequestHeader('if-modified-since','0');
   ajaxObj.setRequestHeader('Cache-control', 'no-cache');    // 浏览器不会再读缓存

10. {} 和 [] 的 valueof 和 toString 的结果
    {}   valueof: {}    toString: [object object]
    []            []                 ""

11. 假值对象
    a. 对象值不为 null 做 boolean 判断返回 false ， 例如 document.all 返回一个类数组对象，存储页面所有的值。

12. parseInt、parseFloat、 Number() 的区别
   a. 
    parseInt、parseFloat 称为解析字符串
    Number 称为强制转换
   b.
     Number 转换为数字时：丢弃前导0 过滤字符串的前后空白字符， 若字符串不是纯数字返回 NaN， ''返回0
     parseInt(数字， 进制):  若第一个非空字符不是数字，会返回 NaN。 前导0会被作为8进制解析， 小数会只保留整数
     parseFloat(小数): 同上，没有进制转换，只有10进制，因此会忽略前导0。
    
18  ['1', '2', '3'].map(parseInt)返回什么
    答案： [1, NaN,NaN]  因为 parseInt 接收两个参数(arg, 进制)
    因此运行过程 parseInt('1', 0)
               parseInt('2', 1)  NaN
               parseInt('3', 2)  NaN
    map 内部定义的函数接受三个参数: value index arr ， 它会将这三个参数全部送入到 parseInt 中
    parseInt 只会使用前两个数值。
    
15. javascript 创建对象的几种方式  (题号：34)

17 三种事件模型， 如何阻止冒泡(题号：42/43)
       事件： 用户与页面发生交互
    事件代理： 目标元素发生事件后，将事件向上传播，上交给父元素，在父元素处做统一的处理。
             事件代理出现的背景是我们在业务中涉及到对大量元素绑定函数，事件代理可以降低内存消耗   
    三种事件模型： 
               a. 在目标元素上监听事件，无事件冒泡
               b. IE 事件模型， 事件处理阶段 + 事件冒泡阶段
               c. DOM LEVE2 事件捕获 + 事件处理阶段 + 事件冒泡阶段 (冒泡阶段是将事件送入到父元素，兄弟元素不会在冒泡阶段触 
                                                              发相同事件)
    事件监听函数： ele.addEventListener('eventName', cb, true/false)  true: 在事件捕获时处理
                      1.  可以定义多个同类型事件不同的回调函数，依次执行。
                      2.  在一个节点上可以定义不同类型事件的回调函数。
                      3.  event.stopPropagation() 阻止当前事件的向上或者向下冒泡或者捕获，当前事件回调依然会执行
                      4.  event.stopImmediatePropagation() 阻止当前及之后同类型事件的冒泡或者捕获，并且该事件绑定的
                                                           所有回调函数都不会被执行。
    事件对象：  event.target event.currentTarge、event.type、 event.bubble、 event.phase
              event.preventDefault();  事件发生的默认动作不会被执行，事件依然会向上传递
                                       默认动作是浏览器自身定义的。
----------------------------------------------------------------------------
16 写一个通用的事件侦听器函数 (题号：41 js代码)  [完成]

20  使用 use strict 的区别是啥  (题号： 47)
     . use strict 是 ES5 添加的严格运行模式 
     . 声明了 'use Strict' : 1. 变量不能重名， 2.this 不能绑定 window  3.禁止使用 with 语句

21 对于 json 的理解  (js 悟道)
   背景： 需要一种浏览器与服务器进行数据交换的方式
         XML： 向服务器发送查询请求， 服务器返回 XML 文档，需要写一个 XML 文档查询的逻辑
   为什么程序不能直接处理服务器返回的数据?
         道格拉斯认为 [对象字面量] 是一个好的选择, 在 json 中属性和属性名采用单引号的方式
         没有注释。
    在 javascript 中 json 的操作方式：  JSON.parse(text, reviver)
                                     JSON.stringify(value, replacer, space)
         
23 JS 模块加载器的实现  (题号：68)
     
  
24 document.write 和 innerHtml 的区别  (题号: 70)
   DOM操作： 怎样添加、移除、移动、复制、创建、查找
   innerHTML 和 outerHTML 区别
   
25 [,,,] 长度  (题号：77)
   a. 数组的长度就是逗号的数量
------------------------------------------------------------------------------
26. JS 中哪些操作会造成内存泄漏 (题号81)
    内存泄露： 不用的内存没有得到及时的回收，称作内存泄露。
    1. 意外的全局变量， 变量未声明就使用，会被加入到全局对象中；fun的this，在无上下文调用的情况下指向 window
    2. 遗忘的计时器
    3. DOM 引用
    4. 闭包
    垃圾回收机制： 创建一个root 列表， root列表存放全局变量引用。 在JS中root是window对象
                检查它和它的全局子对象是否存在。

31. Object.is() 与 原来的比较操作符 === 、== 的区别
    Object.is(obj1, obj2) : 与 === 判断机制一样不会作类型转换，但是修正了 两个NaN 不相同， +0/-0相同问题

28. 移动端的点击事件的有延迟吗，时间是多久，为什么会有，怎么解决？
    a. 有一个 300ms 的延迟， 因为移动端有双击缩放的效果。因此第一次点击后会等待 300ms 
       在 300ms 内点击证明是双击。
      解决方法： 在 meta 标签下禁用网页的缩放标签
              <meta name="viewport" content="width=device-width,   适合各种屏幕分辨率
                                     initial-scale=1.0,            初始化时不缩放
                                     maximum-scale=1.0, 
                                     user-scalable=no">            禁止缩放
        在 PC 端响应点击事件： mousedown -> mouseup -> click
         在移动端响应点击事件： touchstart --> touchend --> click,  touchend 会有 300ms 延迟
                            300ms 之后触发 click。 
                  点击穿透： 

29 检测浏览器版本有哪些方式 (DOM 操作)
   a. window.navigator.userAgent :  不可靠因为浏览器可以自己改写
   b. 功能检测  浏览器特有的功能 window.attachEvent
----------------------------------------------------------------------------------
30.使用 JS 实现获取文件扩展名
    function (fileName){
       if( typeof fileName == 'string'){
            let pos = fileName.indexOf('.');
            return fileName.substring(pos+1);
       }
    }

32. Unicode 和 UTF-8 之间的关系
    Unicode 是一种字符集合，可以容纳100万个字符，解决各国为各自的文字制定字符集不统一的问题。
             它为容纳的字符制定了编号，但是没有决定采用哪种编码方式
    UTF-8 是 unicode 的编码方式， 利用开头的标志位实现变长编码，若是单字节则只用一个字节，因此
          向下兼容 ASCII 。
               
35 asyn 使用时有什么问题
   a. await 会阻塞之后的的代码运行， 若之后的执行逻辑不依赖之前的代码会造成时间上的浪费
   b. 解决方法： 同时使用多个 async 函数
               可以并行的操作使用 await Promise.all()
               不使用 await 而改用 Promise.then()
        
----------------------------------------------------------------------------------
33. 为什么 0.1+0.2 !=0.3, 如何解决这个问题
    浮点类型：IEEE 754
    十进制转化为二进制： 整数部分除以二，取余数， 留尚继续除以2， 直到商为1
                     小数部分不断乘以2，取整数位，留小数位继续乘以2 直到为0
                  9.0 --->  1001.0   ---> 指数表示 1.001*2^3
    浮点数表示方式： 32 位：  符号位1  8位指数位   23位有效数字
                  64 位：  符合位1  11位指数位  52位有效数字
            8位指数位：  0-255 因为需要表示指数，因此将 0-127 表示成指数， 127-255 表示成正数
                       因此指数位的值 -127 是真实的十进制的值， 表示的范围 -127 - 127
            11位指数位： 0-2048 因为需要表示指数，因此将 0-1023 表示成负指数，1023-2048 表示成正指数
                       因此指数位的值 -1027 是真实的十进制的值
            有效数字为小数部分，其正数部分默认是1， 即1.xxxx
            当指数位全为0，则整数部分默认是0。
            当指数位全为1，有效数字部分全是0，则数字默认为1，表示无穷大； 有效部分不全为0， 表示为 NaN
                
    0.1 、0.2 在十进制转为二进制时，由于是无限循环因此有摄入误差。 在相加时由于需要阶数统一
    记住： 永远不要比较两个浮点的大小 0.1 + 0.2 === 0.3
   
37. 为什么使用 setTimeout 实现 setInterval 怎么模拟  (题号126)


36 图片的懒加载和预先加载 (题号：123)


27 需求： 实现一个页面操作不会整页刷新的网站，并且能在浏览器前进、后退时正确响应。 给出技术方案


34. WEB 安全知识：1. 什么是 xss 如何防范， 2. 什么是 csp 3， 什么是 CSRF 攻击如何防范 CSRF攻击
                 4. 什么是点击劫持，如何防范点击劫持 5 什么是 SQL注入攻击 (102-106)

13. 正则表达式： 浮点数左边的数每三位添加一个逗号  12000000.11  --> 12,000,000.11
    function format(number){
       return number && number.replace(/(?!^)(?=\d{3}+\.)/g, ',');
    }

14. 如何实现数组的随机排序  (JS 代码)
    function randomSort(a, b){
        return Math.random() > 0.5 ?-1 :1
    }


```


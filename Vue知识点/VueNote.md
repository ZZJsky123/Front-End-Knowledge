## webpack

```
  使用JS语言，依赖node环境的前端项目打包工具。其核心是将项目中的各个资源当作一个模块，通过构建各个资源的依赖关系管理整个项目，最后将资源转化成合适的格式后打包成bundle发布。
  四个核心：Entry，outPut，loader，plugin。Entry定义入口文件，webpack将从该文件开始构建资源之间的逻辑。output是将资源打包后的输出位置，默认是./dist
  loader帮助webpack处理非JS文件，对loader配置时常用两个属性 test，use。test指定哪些后缀文件应该被处理，use文件指定test类型的文件应该使用哪个loader，比如css-loader，style-loader，babel，使用loader后webpack就可以处理非Js文件
  Plugins(插件)需要使用npm包管理器进行安装，在配置文件引入，实例化后传递给plugins数组属性，主要作用是扩展webpack功能
  
```

## 前端工程化

```
工程化：
  工程的5个方面： 研究设计、分工、复用、优化-折中
  目的：工程效率和工程质量
  
前端的工程化： 模块化、组件化、规范化、自动化
```

## Vue

```
MVC 与 MVVM的区别
  Mvc: 软件分为三部分：数据、视图、业务逻辑。以数据的流动角度去理解MVC即：数据的管理，数据的调用，数据的展示。MVC常用的通信方式：视图向业务逻辑请求数据，数据传递给视图，比如登录界面用户信息的核对。2.用户直接使用Controll，control将请求传递给数据，数据渲染待视图上。
  主要缺点：数据返回给View的过程中涉及大量的DOM操作，使页面渲染性能减低加载速度变慢。
   第二点：数据频繁变化时，开发者需要主动更新到View
  
  MVVM：也包含三部分，Model，View，ViewModel。其中ViewModel取代了原先的Controller，View ViewModel model之间双向绑定，model变化会反映在ViewModel，ViewModel变化反映在View上，反过来V层的变化也会影响到M。这种双向的数据绑定，使数据的变化直接进行展示而不需要通过前端操作DOM进行改变，减少了大量的DOM操作。
  同时MVVM实现了Model和View的解耦，即后端只需要生成数据，前端只需要关心如何处理数据。


Vue的响应式原理：
   Vue的核心思想是数据驱动。Vue中对视图的修改不直接操作DOM，而是通过修改数据。在没有Vue或者其他前端框架前，将数据渲染到Html上需要对DOM节点设置监听事件，比如操作表单数据并返回显示，需要监听表单输入框并将数数据渲染到相应的选择器上。
   Vue数据响应核心三部分： 数据劫持，依赖收集，发布订阅
  概述：核心是观察者模式，每个Vue component(组件)都有一个Watcher实例即作为观察者，而Vue的data上的属性被添加getter和setter，当组件调用render函数时，data会被touch即被读，getter方法被调用，属性会记录所有依赖它的对象同时对象也会记录他的所有依赖，这一过程又可以被称为依赖收集。data被改动时，setter被调用即重新设置，而这种变化会传给他的观察者Watcher，这些Watcher重新调用render去渲染数据
  详细： Vue在init阶段，使用defineReactive函数将data属性reactive化，该函数会创建Dep对象，和调用Object.defineProperty为当前data添加get 和 set
  Vue在mount阶段，调用mountcomponent方法，创建Watcher对象，watcher对象创建的同时，执行了vue的render函数，该函数触发reactive化属性的getter方法：调用dep.depend()该函数会与该数据有关的所有组件加入subs数组。当可观测者某一属性被修改时，调用setter，在setter调用Dep.notify(),该函数会通过遍历所有组观察者并调用他们的updata方法，完成通知的目的。
  
  Tip：使用Object.defineProperty()无法拦截某些属性操作，比如通过数组下标修改值给对象增添属性，Vue3,0改用Proxy.
  
56
Vue的生命周期函数：  Vue实例创建过程、模板挂载过程、 数据更新过程
beforecreated ：实例开始初始化，执行一些默认事件，当前阶段data和method都未被初始化。
created：实例创建完后立即调用，此时data和method都完成初始化，但还未挂载
beforeMount：挂载之前被调用，reder函数首次被调用，执行到此内存已经编译好模板但没有挂载到页面
Mounted：实例被挂载后调用，el被vm.el替换，此时组件已经初始化完成进入到运行阶段，此时可以操作文档中的DOM节点
beforeUpdate: 当前钩子，数据已经更新但是页面中的数据还是旧的未更新
updated: 此时页面中的数据已经与最新数据保持同步
beforeDestory: 进入销毁，但是数据方法都还可以
destory：所有data和methods都不可用，组件已经被销毁

Vue中父子组件的生命周期
当组件中注册了其他组件则，在父组件和子组件的生命周期会和单一的组件生命周期过程不太相同：
父beforecreated->父created->父beforeMount->子beforecreated->子created->子beforeMounted->子Mounted->父Mounted
更新：
父beforeUpdate->子beforeUpdate->子Update->父Update

Vue的Vue-router：
  路由： 一种映射关系： 源地址 -> 目的地址的映射
  后端渲染：后端通过JSP将JS+CSS+HTML整合成页面发给浏览器
  前端渲染：前端通过JS将数据渲染到页面
  网站的三个阶段：后端渲染阶段：浏览器通过url向服务器请求资源(路由)，后端通过
               JSP将数据htmlcssJS整合成页面返回，前后端分离：后端只负责生产数据，而前端向服务器请求url对应的HTML+CSS+JS资源文件后，由前端渲染。SPA
单页面富应用：浏览器初始时将所有资源请求下来，通过前端路由建立url和页面的映射关系，在不需要刷新页面的前提下更新页面内容。而改变url且不刷新页面的方式有两种，hash模式和history模式
vue.$route: 当前激活的路由对象，可获得当前路由的path，name，params，query
vue.$router: 全局的router对象，在安装路由的过程向根组件的protype属性中注入
从而每个子组件都可以调用该属性，可调用该属性的push，go，replace方法

Vue-router中的懒加载： SPA在初始化时由于一次性请求所有资源文件，当打包文件十分大时影响页面初始化时间，利用懒加载的方式根据路由将资源分割成多个打包文件，当路由被访问时才会加载相应的打包文件


v-if 和 v-show的区别：
V-if: 通过操作DOM节点来达成显示特定条件的土元素
v-show:：通过修改元素的display:none/block 来控制显示或者隐藏

Vue组件中国的data必须是函数：
因为组件有可能会被多次调用，若data不是返回数据对象的函数，则多个组件将共享相同的数据对象。声明成返回数据对象的函数每次使用组件都会返回一个新的数据对象

SPA单页面理解
  SPA:单页面复应用，仅在web页面初始化时加载HTML/CSS/JS,加载完成后SPA不会因为用户的操作进行页面的重新加载和跳转，而是使用前端路由机制实现HTML内容的变换
  缺点：不利于SEO因为所有文件都集中在一个页面。

Vue.use: 在全局进行插件注册, 如果参数是对象则需要含有install方法，若是一个函数则会被当作install方法
         一旦完成注册可以在所有Vue文件中使用该组件
         
 keep-alive： Vue内置的抽象组件，不会渲染一个DOM，也不会出现在父组件链中。被该组件包裹的组件其状态将会被缓存起来，下次渲染时不会执行created、mounted等钩子函数。但是我们很多实际业务场景都是希望在我们被缓存的组件再次被渲染的时候做一些事情。
所以Vue 针对被keep-alive包裹的组件提供了 activated和deactivated钩子函数。

页面第一次进入，钩子的触发顺序created-> mounted-> activated，退出时触发deactivated。当再次进入（前进或者后退）时，只触发activated


```



## 问题

```
如何实现组件水平垂直居中？

JS 事件委托原理？

常见的CSS hack方式？

Vue的双向数据绑定？

Promise 和 async/await的区别

Webpack如何配置babel？
```


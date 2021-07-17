## Vue

### Vue特性

```
1.  transition       https://vuejs.org/v2/guide/transitions.html
2.  component system
  注： 
     1. The component system is another important concept in Vue, because it’s an abstraction that allows us to build large-scale applications composed of [small](小型), self-contained(自包含), and often reusable(可重用)components.
     2. a component is essentially a Vue instance with pre-defined options
          (组件本质是 带有预先选项的Vue 实例)
3. Declarative Rendering 命令式渲染
4. reacticity system
5. data binding
7. Vue provide more (gengeric way) ？ to observer and react to data changes   
   on a Vue instance.
        data 、 computed、 wacther、 v-bind、 v-model
8. Component Registration
9. Vue-x 命令直接作用于Html标签，影响Html标签属性，和操作 Html 标签本身。


```



### Vue-x

```vue
v-xx： [directive] They are special attributes provided by Vue

1.v-text: updates the element’s textContent. If you need to update the part 
         of textContent, you should use {{ Mustache }} interpolations.
<span v-text="msg"></span>
<!-- same as -->
<span>{{msg}}</span>   
其中 msg 是变量， v-test相当于使用vue中的差值语法 {{ Mustache }}

2.v-html: Updates the element’s innerHTML,the contents are inserted as plain 
          HTML
3.v-show:Toggles the element’s display CSS property based on the truthy-ness 
          of the expression value.  根据表达式的真实性切换 display的值。
<h1 v-show="ok">Hello!</h1>
注： the elements with v-show will always be rendered and remain in the DOM.
    不可用于 <template> 标签

4.v-if: Conditionally render the element based on the truthy-ness of the 
        expression value. The element and its contained directives /  
        components are destroyed and re-constructed during toggles.
      注： 可以用于template 标签

与其连用  <v-else-if> <v-if>
<h1 v-if="awesome">Vue is awesome!</h1>
<h1 v-else>Oh no 😢</h1>     只有一个分支会被渲染

v-if vs v-for
  v-if has higher toggle costs while v-show has higher initial render costs. So prefer v-show if you need to toggle something very often, and prefer v-if if the condition is unlikely to change at runtime.
   (v-show有较高的初始渲染消耗， 而当我门选择的比较平凡时 v-if 消耗的比较高)

v-if with  v-for
v-for has a higher priority than v-if
    
5. v-for: Render the element or template block [multiple times] based on the 
          source data.
     <div v-for="item in items" :key="item.id">
      {{ item.text }}
    </div>
  使用 key 值：
    The default behavior of v-for will try to patch the elements in-place without moving them. To force it to reorder elements, you need to provide an ordering hint with the key special attribute:
    
 [In 2.2.0+, when using v-for with a component, a key is now required].


6. v-on: Attaches an event listener to the element.  监听指令
<!-- method handler -->                   监听自定义函数
<button v-on:click="doThis"></button>

<!-- dynamic event (2.6.0+) -->           
<button v-on:[event]="doThis"></button>

<!-- inline statement -->
<button v-on:click="doThat('hello', $event)"></button>

<!-- shorthand -->                       @简写符号
<button @click="doThis"></button>

<!-- shorthand dynamic event (2.6.0+) -->
<button @[event]="doThis"></button>
    
<!-- object syntax (2.4.0+) -->         绑定多次事件
<button v-on="{ mousedown: doThis, mouseup: doThat }"></button>

<!-- native event on component -->      使用HTML原生监听事件
<my-component @click.native="onClick"></my-component>
    
7. v-bind： Dynamically bind one or more attributes, or a component prop to an expression.
    
 <!-- bind an attribute -->
<img v-bind:src="imageSrc">

<!-- dynamic attribute name (2.6.0+) -->
<button v-bind:[key]="value"></button>

<!-- shorthand -->
<img :src="imageSrc">

<!-- shorthand dynamic attribute name (2.6.0+) -->
<button :[key]="value"></button>

 8. v-on： varies based on value of form inputs element or output of 
           components
    
 9 v-slot： Skip compilation for this element and all its children. You can 
            use this for displaying raw mustache tags.
    <span v-pre>{{ this will not be compiled }}</span>
    
10. v-cloak: This directive will remain on the element until the associated 
             Vue instance finishes compilation. Combined with CSS rules such              as [v-cloak] { display: none }, this directive can be used to  
             hide un-compiled mustache bindings until the Vue instance is 
             ready.
            [v-cloak] {
                      display: none;
                    }
                  <div v-cloak>    
                   {{ message }}
                  </div>
    
11. v-once : Render the element and component once only. 即使数据后来发生改变
             其值也不会发生更新。
    <!-- single element -->
    <span v-once>This will never change: {{msg}}</span>
    <!-- the element have children -->
    <div v-once>
      <h1>comment</h1>
      <p>{{msg}}</p>
    </div>
    <!-- component -->
    <my-component v-once :comment="msg"></my-component>
    <!-- `v-for` directive -->
    <ul>
      <li v-for="i in list" v-once>{{i}}</li>
    </ul>
```

### Class & Style binding

```css
Html 标签可以设置class属性， 同时可以依附内联属性。 因此 vue-bind 也可用于绑定 class 用于动态改变 标签 样式。

Object Syntax 传递 Object 值给class
1. <div v-bind:class="{ active: isActive }"></div>

        data: {
            isActive: true,
                hasError: false
        }

        <div class="active"></div>

2. 可在大括号内同时设置多个 class，除此之外也可以设置 plain class ， 其会与值为 true 的
   class 一同作为 class 的属性。

   <div  class="static" v-bind:class="{ active: isActive, 'text-danger':   
         hasError }"> </div>

3. 使用 computed 属性， 决定 class 的状态值。

   <div v-bind:class="classObject"></div>
        data: {
          isActive: true,
          error: null
        },
    computed: {
          classObject: function () {
            return {
              active: this.isActive && !this.error,
              'text-danger': this.error && this.error.type === 'fatal'
            }
          }
        }
 
 4. Array Snytax ： 输入一组类名
      <div v-bind:class="[activeClass, errorClass]"></div>
        data: {
          activeClass: 'active',
          errorClass: 'text-danger'
        }
     <div v-bind:class="[isActive ? activeClass : '', errorClass]"></div>
     <div v-bind:class="[{ active: isActive }, errorClass]"></div>

5. 在自定义的组件下 声明 v-bin：class=‘’， class 会被放进组件的根元素下。
Vue.component('my-component', {
  template: '<p class="foo bar">Hi</p>'
})
<my-component class="baz boo"></my-component>
<p class="foo bar baz boo">Hi</p>

6. Binding Inline Styles 绑定内联样式

  Object Synatx：
      <div v-bind:style="{color:activeColor, fontSize:fintSize + 'px'}">

 Array Synatx:
      <div v-bind:style="[color:red, fontSize:fintSize + 'px']">

 Multiple Values:
     Starting in 2.3.0+ you can provide an array of multiple (prefixed) values to a style property, for example:
<div v-bind:style="{ display: ['-webkit-box', '-ms-flexbox', 'flex'] }"></div>

  

```



### Vue instance

```vue
实例化： 
var vm = new Vue({
  // options
})
  When you create a Vue instance,  pass in an [options object]。 these options achieve our desiered behavior.


1. no longer have to interact with the HTML directly
2. A Vue app attaches itself to a single DOM element (#app in our case) then 
   fully controls it
3. HTML is our entry point
4. Everything else happens within the newly created Vue instance.
```

### Options

```css
Options: 
   1. data : Vue instances adds all the properties in its [data Object] to
              the Vue's [reacticity system]
      注; Vue 实例可直接访问到 data 中的属性， 且 vue 访问的数据与 data 中的属性是双向绑定的， 任意一方修改都会引起另一方的改变。但是通过 vue 实例增添新的属性不会引起 data 的改变。
      
  2.  Vue instances expose a number of useful instance properties and methods. These are prefixed with $ to differentiate them from user-defined properties. For example:
            vm.$data === data;
            vm.$el === document.getElementById('example');

 3. computed:
       解决 {{value}}, value是表达式时语义不够简约直观。其上存放函数但在挂载区又可以直接
    以函数名的方式直接调用。 计算结果会存储在缓冲区，任何地方调用可以直接从缓冲区拿到结果。
       注： the computed properties are cached based on their reactive dependencies. 这句话指的是computed 有使用到 data中的属性 message 时， message 发生改变，computed 也会发生改变。 因为 message 是它的 reactive dependencies， Vue 可以检测到 message 的改变， 因此computed 中也会跟着改变。
          var vm = new Vue({
              el: '#example',
              data: {
                message: 'Hello'
              },
              computed: {
                // a computed getter
                reversedMessage: function () {
                  // `this` points to the vm instance
                  return this.message.split('').reverse().join('')
                }
              }
            })
 4. watch：  为 date 中的属性声明同名的检测函数,，一旦 data 发生改变，同名函数运行。
```

### Template

```vue
1. All Vue.js templates are 【valid HTML】 that can be parsed by spec-compliant 【browsers】 and 【HTML parsers】.  Template allows you to declaratively bind the rendered DOM to the underlying Vue instance.

2. under the hood, Vue compiles the templates into Virtual DOM render functions.
         Vue compilers --->  template ----> VDOM render functions
         
3. Combined with the reactivity system, Vue is able to intelligently figure out the 【minimal number of components】 to 【re-render】 and apply the minimal amount of DOM manipulations when the app state changes.

4. the type of the Vue's template engine ?

总结：


Interpolations
   1. Text:  Mustache 语法 {{ }}
       e.g <span>Message: {{ msg }}</span>
      注： a. most basic form of data binding is text interpolation using 
                            "Mustache" syntax
               data binding: mustache tag be replace with the value of msg
                             updated when the data Object's msg changes
          b.  can prevent data update by using v-once
   2. Raw Html
          e.g: <span v-html="rawHtml"></span></p>
          a. The contents of the span will be replaced with the value of the 
             rawHtml property.
          b. Cannot use v-html to compose template partials, because Vue                  is not a string-based templating engine
   3. Attributes 
         1. Mustaches cannot be used inside HTML attributes used a v-bind 
      directive.    Mustaches 不能被用于内部的 HTML 属性中。，此时需要使用 v-bind
          <div v-bind:id="dynamicId"></div>
               v-bind:arguments = 'value'
         2. Using JavaScript Expression 
           e.g: {{ number + 1 }}
                {{ message.split('').reverse().join('') }}
                <div v-bind:id="'list-' + id"></div>
           注： one restriction is each binding can only contain one single
               expression
               e.g： {{ var a=1}}   这是声明
                    {{if (ok) {return message} }} 
        3. Dynamic Arguments  since Vue 2.6.0++
              v-bind:[argumentName]='value'
        注; a. Here attributeName will be dynamically evaluated as a   
               JavaScript expression,its evaluated value will be used as the 
               final value for the argument.
            b. Dynamic argument expressions have some syntax constraints   
               because certain characters, such as spaces and quotes, are   
               invalid inside HTML attribute names.
Directives

Shorthands
```

### Component Registration

```
全局注册：
  1. Vue.component('my-component-name', {...})
  
组件命名：  strongly recommend following the W3C rules. 
   链接：https://html.spec.whatwg.org/multipage/custom-elements.html#valid-custom-element-name
   
   两种命名风格：   
            a. 串羊肉串 ，   kebab-case
               Vue.component('my-component-name', {...})
            b. PascaLCase
               Vue.component('MyComponentName', { /* ... */ })
   
   2. 创建的组件可以被根组件实例使用 
            new Vue({
                el:#app,
                component:{
                  'my-componentA': {} 
                }
                
            })
            
    3. if you’re using ES2015 modules
           import ComponentA from './ComponentA.vue'
            export default {
              components: {
                ComponentA
              },
              // ...
            }
            
   4. Local Registration:  建立 Component Directory， 用模块语法在全局导入
       在 ComponentB 文件夹
            import ComponentA from './ComponentA'
            import ComponentC from './ComponentC'

            export default {
              components: {
                ComponentA,
                ComponentC
              },
              // ...
            }
      
      
   注： Remember that global registration must take place before the root Vue instance is created
```





## Vue 项目

### Node & Vue-cli

```
  node 只用于 Vue 的开发阶段， webpack/npm这些打包工具和包管理工具都需要依赖 node.js环境，因此 vue 一旦利用这些工具就需要安装 node环境。 vue-cli 就需要依赖 node。
vue 的大量轮子都可以依托 node.js 来获得更高的开发效率。

现代的前端开发环境需要的典型服务包括且不限于：
      a. lint服务（eslint tslint）
      b. 代码打包和编译服务（webpack babel）
      c. 前端mock服务（mockjs）
      d. 代码格式化服务（prettier）
      e. 代理服务（node proxy）
  这些服务需要运行在前端开发环境中，至少需要一种runtime来运行这些服务，那么和前端同构且跨平台的nodejs就成了首选。其实也可以完全不使用这些东西，用最原始的方法script引入vue，然后用记事本写代码，就不再需要nodejs了，当然也不能用jsx、typescript等等需要编译的语法拓展

官网下载 node： 包含 npm webpack ， 安装过程中会自动将路径加载到环境中。

在 cmd 终端 使用 npm -v / node -v 查看有无成功。

Install Vue-cli

  a. npm install -g vue-cli   全局安装 vue-cli 脚手架
  b. vue --version   查看是否安装成功
```

### Init vue-project

```
1. 初始化 Vue2.x 项目
  
   a. 在任意文件夹下打开 cmd 终端， 或者在编辑器的终端
      init webpack project-name
      
   b. 初始化完毕。
   
2. Vcode 打开项目
    a. 将终端入口调整成项目所在文件
    b. code project-name
    c. npm run dev              // 运行项目
    
3. 项目文件
    a. main.js   入口文件， 在这个文件下生成Vue实例包含：挂载区域el、 App组件、 路由作为根
    b. index.html  挂载区域 el 指向的便是 该文件下的某个 id 区域。webpack
                   工具将会把编译好的视图模板挂载到这个区域上。
    c. App.vue
    d. 

```

### Express 搭建后端

```
1. npm install -g express-generator         安装 Express 脚手架

2. express --version                        express 版本号

3. express vue-online-shop-backend          创建项目

4. code vue-online-shop-backend             用 vscode 打开

5. 文件结构：
    a. app.js: Express 应用文件
    b. bin/www: 用来开启服务器的脚本
    c. routes/index.js : 路由主文件
    d. views/index.ejs: 主页的模板文件
    

```

### 项目结构梳理

```vue
1. 初始项目页面结构：   
      a. src/main.js 作为项目 vue应用的入口， 其内容：
           i. 导入必要的依赖项
                   import  Vue  from 'vue'   // 从 node_modules 中导入    如何查找 vue ？
                   import  App  from './APP' 
                   import  router from './router'   // router 是一个文件名？
                   
           ii. 创建根实例 new Vue {
                 el: '#app' ，            // html 挂载的 ID 区域
                 router,                 // 这一步目的是什么？
                 components: {App},
                 template:  '<App/>'     // 子组件必须声明才可以在模板中使用吗？ 
           }
                           <App/>
       总结：     main.js  ------->  index.html   最终前端代码全部被融合进 <App/> 中进行Html替换

     b. webpack 根据入口文件的 src/main.js 里面的声明的 el 属性，将编译好的 <template> 模板挂载到
        index.html 中 id 为 app 的 DOM 节点上。
                       i.  webpack 依赖管理？
                       ii. <template> 中的内容挂载到特定节点之下？
     
     c. src/App.vue                      ： 承担项目功能布局  
              a. App 给出了组件的通用模板
                   i.   <template>       
                   ii.  <style scoped>  
                   iii. <script>         
              总结： 组件在整个页面上作为[html 标签]的方式进行呈现，进行呈现的必须具备两个条件
              
                    (1)  模板，<template> 包裹的 div 会将原标签替换。 标签的属性在替换时怎么处理?
                    (2)  内部数据， template 使用的数据必须从它内部的 <script> 得到, 如何识别
                         需要的数据在内部存在?。
              
             b. <router-view/> : 这是一个全局标签， 其在哪个过程｛导入，注册，附属｝被注册成为全标签？
                 i.  此标签是前端路由跳转后内容显示区域占位符 
              
             c.  App.vue 的导航栏 
                 <nav>
                   <div class = 'conatiner'>
                        <ul>
                             <li>
                               <router-link to='/'>Home</router-link>
                             </li>
                             <li>
                               <router-link to='/admin'>Admin</router-link>
                             </li>
                             <li>
                               <router-link to='/cart'>Cart</router-link>
                             </li>

                        </ul>
                   </div>
                </nav>
               <router-view/>
             总结：   一张页面，在导航栏向用户展示可操作内容： 主页 -- 用户中心 -- 购物车
                     <nav> 之下是内容展示区域， 具体的展示内容由当前的 <router-link> 决定，展示
                     位置由 <router-view/> 决定。
             前端路由： 模板位置存储在前端，路由发生改变不需要向后端请求，而是在前端完成资源的跳转。
             
            d. src/router/index.js      :前端统一管理路由文件
                    import Vue from 'vue';                       
                    import Router from 'vue-router';
                    import Home from '@/components/Home';       // 组件导入
                    import Admin from '@/pages/Admin';

                    // Admin components
                    import Index from '@/pages/admin/Index';
                    import New from '@/pages/admin/New';
                    
                     Vue.use(Router)                          // 注册之后发生了什么 ？       

                    export default new Router({               // 路由映射管理
                      routes: [
                        {
                          path: '/',
                          name: 'Home',
                          component: Home,
                        },
                        {
                          path:'/admin',
                          name:'Admin',
                          component: Index,
                          children: [                         // 子路由
                            {
                              path: 'new',
                              name: 'New',
                              component: New
                            },
                          ]
                        },
                      ],
                      mode: 'history'
                    })
               总结： 路由管理， 是生成一个 router 实例， 该实例在生成过程中接收一个对象， 该对象有一个
                     routes 是一个数组记录了前端路由映射：  path ---> component
                
                 ii.   嵌套路由？
                       动态路由？  /edit/:id
                       <router-link> 的属性
                       this.$router ?
                       this.$route ? 
                           
               总结： App 页面搭建好页面结构后， 我们可以专心于每一个组件的开发，前端路由管理的资源正是
                     组件， 为保证 App 结构清晰， 将属于每个组件的功能封装在每个组件之内，使其不溢出
                     在 App 中。
                       
                           
    2. 组件开发：
           a. Home 组件  ： 承担商品信息展示
              <template>
                  <div>
                      <div class = "title">
                           <h1> In Stock </h1>
                      </div>
                      <product-list></product-list>       组件文件 和 组件标签的命名方式 ？
                  </div
             </template>
             ii. <product-list> ---> <product-item> ----> <product-button>  
                 <product-list> : 所有需要展示的商品的信息
                 <product-item>: 商品信息的标准模板： 名称、介绍、价格、生产商
                 <product-button>: 商品旁边的按钮。
                     
             总结： 组件开发时，第一个核心思想是对展示内容分类，内容是一个抽象的集合体， 对内容进行分类划分
                   成更小的单元分别维护， 这是组件复用的基础。
          
           b. 组件间信息传递：
                 i. 父组件向子组件传递信息： props
             New.vue 组件：     子组件：product-form
                 <template>
                    <product-form
                        @save-product="addProduct"        // 子组件传出来的事件，父组件增加响应
                        :model="model"                    // 传入mode参数，参数值来源于父组件下                                                              的 data， 若 computed 中有重名
                                                             该怎么处理？ data、props、
                                                             computed 数据是否可以重名 ？
                        :manufacturers="manufacturers"
                    >
                    </product-form>
                 </template>
                 <script>
                    import ProductForm from '@/components/products/ProductForm';
                    export default {
                      data() {
                        return {
                          model: {},
                          manufacturers: [
                            {
                              _id: 'sam',
                              name: 'Samsung',
                            },
                            {
                              _id: 'apple',
                              name: 'Apple',
                            },
                          ],
                        };
                      },
                      methods: {
                        addProduct(model) {
                          console.log('model', model);
                        },
                      },
                      components: {
                        'product-form': ProductForm
                      }
                    }
</script>
                     
       c. 数据值绑定 v-x命令
                data:{}   {{}}        插值语法将逻辑层数据展示在视图层
                v-on: 事件             通过视图层操作逻辑层中的数据
                v-bind: 标签属性值      动态绑定属性值
                v-model: 数据的双向绑定  逻辑层和数据层任意发生变化都会相互反映
                method：
                computed
                     
    3. Vuex 状态管理：  state、 mutations、 actions     
                
     
```


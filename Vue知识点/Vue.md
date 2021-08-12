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
9. Vue-x 命令直接作用于 Html 标签，影响 Html 标签属性，和操作 Html 标签本身。
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

v-if vs v-show
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
       解决 {{value}}, value 是表达式时语义不够简约直观。其上存放函数但在挂载区又可以直接
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
   
  5. 组件中的 data 必须是一个函数，否则相同组件标签会共享数据
     Vue.component('my-componentA', {
         data:function(){
                 return {
                     count:0
                    }
              }
     })
     
  6. 向组件传递信息：props。
     props 是一个字符串数组，它存放着可以从外部接受的信息，这些信息将被内部调用。
     Vue.component('my-componentA', {
          props: ['A', 'B']
          template: '<p>{{ A }} </p>'
      })
      
      v-bind: 命令置于组件之上，帮助组件动态的接受信息.
      
  7. 组件的 template 模板下只能有一个根元素
  
  8. 子组件向父组件传递事件
  子组件：blog-post
     Vue.component('blog-post', {
      props: ['post'],
      template: `
        <div class="blog-post">
          <h3>{{ post.title }}</h3>
          <button>
            Enlarge text
          </button>
          <div v-html="post.content"></div>
        </div> `
    })
       
   子组件抛出事件： <button v-on:click='$emit('enevtName')'>
   子组件抛出事件+值： <button v-on:click='$emit('eventName', 0.1)'>
              值可以通过 $event 进行访问
  
  父组件下： <blog-post v-on:enevtName="xxx">
           <blog-post v-on:enevtName="xxx + $event">
 
 9. 动态组件切换
 
    <component v-bind:is="currentTapComponent"></component>
    currentTapComponent: 组件名字
                           or
                         组件的选项对象
     
```

### Data Driven

```javascript
数据驱动： 以往进行视图层上的数据修改时，不仅考虑修改的数据逻辑， 同时关注如何操纵DOM，我理解
         的数据驱动核心关注：[数据的改变对视图层的影响]，而不需要考虑如何操作 DOM 达成这一行为。 
         DOM 操作已经被框架定义在内部， 采取统一的 DOM 渲染流程。例如，使用 vUE 我们关注
         组件的 data computed methods的属性，子组件的Props被送进去什么数据，他们发生改变时会
         在视图层反映。 因此数据驱动根本上是让我们在构建 [复杂的视图交互] 时关注视图显示的逻辑， 
         而不需要关心最后的渲染操作。
                           背景 -- 思想 -- 例子  -- 提升
                           
   (Tip: 数据驱动类似于将原先的应用题变成了填空题， 使用者只关心填什么答案，而不关心如何得到
         这个答案)
         
响应式： 当前主流的框架是响应式的， 响应指的是状态发生变化后，视图层会自动更新。 VUE 采用双向绑定
        的策略， 逻辑层会影响到视图层， 视图层会影响到逻辑层。 VUE 完成响应式的方案是采用： 
                       1. 数据响应化  2. 依赖收集  3. 消息派发
   每个Vue都有个 _uid
 1.new Vue --> 2. 执行Vue._init()函数 ---> 3. 在 _init() 函数中执行一系列初始化操作
                          initLifecycle(vm)
                          initEvents(vm)
                          initRender(vm)
                          callHook(vm, 'beforeCreate')  // 生命周期 beforeCreated
                          initInjections(vm) 
                          initState(vm)                // 数据响应化
                          initProvide(vm)              
                          callHook(vm, 'created')     //  生命周期 created
                          
  initState(Vm) 是执行数据响应化的关键性操作，其内部分别初始化： 
                props、 Methods、 Data、 Computed、 Watcher    (顺序从左至右)
          
           1. 创建顺序从左到右，避免在这四个对象中定义相同的变量名，他们内部会从
               vm.$options.xx 获取已经创建的对象来识别是否有相同变量名。
           2. props 调用 defineReactive 函数在一个for循环中对其属性进行响应化
              使用 Proxy(vm, '_props', key) 将_props 的属性让 Vm 代理。
              这里 VUE 将 initprops(vm, opts.props) 定义了props = vm._props = {}
              最后调用 definictive(props, key, value);
           3. Data 调用 observer(data, true/*asRoot*/);
              使用 Proxy(vm, '_data', key) 将_data 的属性让 Vm 代理。
           4. watch 是一个对象， 键是需要监听的表达式，值是变化时调用的回调函数、Methods定义的
              方法名， {function(){}, deep:true}, {function(){}, immediate:true}(建立侦听后立即调用)，  watch 可以定义与 data 相同属性名， 从而为 data 上的属性增添新的监听回调函数。
           5. computed 是计算属性， 具有缓存的作用。 其最大作用是将其键当作某个值在模板中直接使用。
           
 数据响应化的核心是 definictive(obj, key ,val)：
     1. 函数内部会首先获得 obj 的 prototype 若其不是对象则直接返回。 
     2. 获得 prototype 的get和set，用于为传进 val 时调用obj[key].
     3.在将(obj, key, val)送入到 defineProperty 中之前，首先调用 observer(val),
       若 val 是对象/数组返回一个 observer 实例， 并且在函数内部调用 new Observer(val) 
       对子属性是对象/数组进行进一步响应化：
     4. Observer 对属性是对象和数组添加 __ob__ 属性， 并且添加 dep 数组(主要用于函数的方法监听)， 
        若是数组则为其添加 arrayMethods 属性覆盖数组的 prototype。
     5. 在 defineProperty 为侦测属性定义 get 和 set， get 进行依赖收集 会调用 dep.depend()
        和 childOb.dep.depend()，其内部会调用dep.tatrget.addDep(this) 进行双向收集。
        在 set 中进行消息派发 dep.notify(), 其内部会调用dep[i].update();  
    注： Dep 和 watch 都具备一个 _uid
    
 在 _init 结尾处进行 DOM 渲染和模板挂载。
    if(Vm.$options.el){
        vm.$mount(vm.$options.el); 
    }
 在 Vue.$mount 内部调用 mountComponent(this, el, hydrating);
 
 在 mountComponent 内部调用：  
                 callHook(vm, 'beforeMount');
                 vm._update(vm._render(), hydrating);
                 callHook(vm, 'Mount');
                 
 1. 在 beforeMount 进行完后：
          会进行模板渲染成 vndoe 通过 vm._render()
          vm._update(vnode, hydrating) 会在其内部调用 __patch__() 方法    ： diff
          此时 DOM 生成并且挂载到了 vm.$el 中。
          
 2. 在 DOM 生成并挂载完成后 vm._update(vm._render(), hydrating)后会返回 updateComponent
    其会被用于 new Watcher(vm, updateComponent, noop, {
                             before() {
                                 if(vm._isMounted && !vm._isDestroyed){
                                    callHook(vm, 'beforeUpdate')
                                 }
                             } 
                           }, true/* isRenderWatcher */)  建立一个渲染时的 watcher
    updateComponent 相当于 expOrFn参数 ， new Watch 内部会调用 this.get() 触发依赖收集。
  
    Watch 内部的 有几个重要参数： deps newdeps depIds  newDepIds， 其内部的 update 方法
    会对 lazy watcher 、 this.sync watcher 、 普通 watcher 作不同的操作，其中普通的 watcher
    会调用 queueWatcher(this) ： 将其加入到 queue 队列中， 在下一个 nextTick 进行更新。
    
 3. 建立完成后调用 callHook(vm, 'mounted'); 
         if (vm.$vnode == null) {
            vm._isMounted = true
            callHook(vm, 'mounted')
          }
  
                  
```

### 下一步问题：

```
1. render函数  diff 算法 
2. nextTick
```

```javascript
VNODE: 
  a.  vndoe 是 js 对象， 用 vndoe 去创建相应的 DOM 树。
  
  b.  利用 vndoe 记录状态， 当某一状态发生变化， 通过比较生成的新旧 vnode 对相应节点进行更新。
  
  c.  vue 中的 vnode 借鉴了 snabbdom 中的 dom
      I. snabbdom: 
             VNode{
                 sel: 选择器
                 data:
                 text: 文本
                 childen:
                 elm: dom 元素 
                 key: 键
             }
      II. vue： 元素类型、 文本类型、 注释类型、 组件类型、 克隆类型、 函数类型
             VNode｛
                 tag:
                 data:
                 children:
                 text:
                  elm:
                  key:
                  parent:
                  ns:
                  context:
                  functionalContext:
                  functionalOptions:
                  functionalScopeId:
                  ComponentOptions:
                  ComponentInstance:
                  isStatic:
                  isInserted:
                  isOnce:
                  isComment:
                  isCloned
               ｝
               
   d. 元素节点介绍： 不需要的属性设置为 undefined/false
           I.   注释节点： text、 isComment：true
           
           II.  文本节点： text
           
           III. 元素节点:  tag; 节点名称 
                         data： 节点属性
                         content:上下文， 当前组件的 Vue.js实例
                         children
           
            IV： 克隆节点： 用于优化静态节点和插槽节点
                   . 静态节点在新的 newVNode 不需要创建直接克隆
                   
             V. 组件式节点： 与元素节点相似， 拥有两个独有属性
                   . componentOptions： 组件节点的选项参数
                   . componentInstance: 组件实例 vue.js 实例
                   
             VI. 函数式节点： 与元素节点相似， 拥有两个独有的属性
                    . functionalOptions:{..}
                    . functionalContext:{..}
```



```javascript
diff 算法：
   a. 核心理念： 在修改 DOM 树时往往是对该节点的内容进行修改，因此采用同层比较差异，减少比较次数。
   
   b. 四个索引指针： oldVNodeStart/oldVNodeEnd  newNodeStart/newVNodeEnd
             意义： 指向当前未处理的节点
   
   c. isSameNode(old, new): 比较旧的 VN 和 新的 VN 是否相同
        I. 比较方式： 比较二者的选择器 sel 和 键 key 是否相同
        
       
        II. function sameVnode(vnode1: VNode, vnode2: VNode): boolean {
              const isSameKey = vnode1.key === vnode2.key;
              const isSameIs = vnode1.data?.is === vnode2.data?.is;
              const isSameSel = vnode1.sel === vnode2.sel;

              return isSameSel && isSameKey && isSameIs;
             }
      
   d. if(isSameNode(oldVNode[oldVNodeStart],newVNode[newVNodeStart]){
          // 更新内容
          oldVNodeStart++;
          newVNodeStart++;
      }else if(isSameNode(oldVNode[oldVNodeEnd],newVNode[newVNodeEnd]){
          // 更新内容
          oldVNodeStart--;
          newVNodeEnd--;
      }else if(isSameNode(oldVNode[oldVNodeStart],newVNode[newVNodeEnd]){
          // 更新内容， 旧节点移动到最右边已经未处理节点之后
           oldVNodeStart++;
           newVNodeEnd--;
      }else if(isSameNode(oldVNode[oldVNodeEnd],newVNode[newVNodeStart]){
          // 更新内容， 旧节点移动到最左边未处理节点之前
           oldVNodeStart--;
           newVNodeEnd++;
      }else{
           
           
           newVNodeStart++;
      }
      
      II. (oldVNodeStart > oldVNodeEnd) || (newVNodeStart > newVNodeEnd)循环截止
           若 oldVNode 有剩余则是无用节点进行 [删除节点] 操作
           若 newVNode 有剩余则是新增节点进行 [新增节点] 操作
```


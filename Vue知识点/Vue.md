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


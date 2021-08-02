### Vue 源码

#### Vue 构建工具

```
Flow ：   Facebook 出品， 静态类型检查

Rollup： Vue.js 源码基于 Rollup 构建， 构建相关配置在 scripts 目录下

```



#### Vue 源码位置

```
src：  source code all in the src  
├── compiler        # 编译相关 
├── core            # 核心代码 
├── platforms       # 不同平台的支持
├── server          # 服务端渲染
├── sfc             # .vue 文件解析
├── shared          # 共享代码
```

#### Vue 源码构建

```
1. package.json:
  
   scripts 字段： build.js 构建入口
```

#### Vue 入口

```javascript
1. src/platforms/web/runtime/index.js

    import Vue from 'core/index'   Vue 初始化的地方
    
2. src/core/index.js

    import Vue from './instance/index'
    import { initGlobalAPI } from './global-api/index'
    import { isServerRendering } from 'core/util/env'
    import { FunctionalRenderContext } from         
    'core/vdom/create-functional-component'

    initGlobalAPI(Vue)

    Object.defineProperty(Vue.prototype, '$isServer', {
      get: isServerRendering
    })

    Object.defineProperty(Vue.prototype, '$ssrContext', {
      get () {
        /* istanbul ignore next */
        return this.$vnode && this.$vnode.ssrContext
      }
    })

    // expose FunctionalRenderContext for ssr runtime helper installation
    Object.defineProperty(Vue, 'FunctionalRenderContext', {
      value: FunctionalRenderContext
    })

    Vue.version = '__VERSION__'

    export default Vue

3. Vue 是一个函数
```

#### Vue 数据驱动

```
数据驱动定义：

    官方定义： 所谓数据驱动，是指视图是由数据驱动生成的，我们对视图的修改，不会直接操作 DOM，而是通过修改数据。
```

```javascript
案例1：
   <div id='app'>
      {{ message }}
   <div>
       
   var app = new Vue({
     el: '#app',
     data: {
       message: 'Hello Vue!'
      }     
    })
       
1. Vue 的初始化： build.js 导入 Vue 函数， 其定义在 src/core/index.js
    function Vue(options ?: object){
      if (process.env.NODE_ENV !== 'production' && !(this instanceof Vue)
      {
        warn('Vue is a constructor and should be called with the `new` keyword')
      }
      this._init(options)
   }
      initMixin(Vue)   :  Vue._init = function(){}
      stateMixin(Vue)  :  Vue.$data、 Vue.$propsDef、 Vue.$set、 Vue.$watcher、 Vue.$delete
      eventsMixin(Vue) :  Vue.$on、 Vue.$once、 Vue.$off、 Vue.$emit
      lifecycleMixin(Vue)
      renderMixin(Vue
     
      export default {Vue};
        
b. _init(options)函数 ： 包含了生命周期初始化、 事件初始化、 渲染初始化
                  initLifecycle(vm)
                  initEvents(vm)
                  initRender(vm)
                  callHook(vm, 'beforeCreate')
                  initInjections(vm) // resolve injections before data/props
                  initState(vm)
                  initProvide(vm) // resolve provide after data/props
                  callHook(vm, 'created')

2. vm.$mount() 实例方法去挂载模板
   
   a. 该方法与平台有关， 在不同文件中都对函数进行定义
          i.src/platform/web/entry-runtime-with-compiler.js
         ii.src/platform/web/runtime/index.js
        iii.src/platform/weex/runtime/index.js
      
       

3. vm._upadte & vm._
```


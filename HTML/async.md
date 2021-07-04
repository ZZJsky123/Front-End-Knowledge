## <script> 标签下的 ascyn 和 defer 属性的区别

```
1. <script>执行时会阻塞页面后续的内容（包括页面的渲染、其它资源的下载）。原因：因为浏览器需要一个稳定的DOM树结构，而JS中很有可能有 代码直接改变了DOM树结构

2. async和defer只能在script 标签连接外部资源时起作用，实现JS资源的异步加载
   async 实现资源的异步加载，并在加载完后立即执行
   defer 实现资源的异步加载，并在HTML所有元素解析完成之后，DOMContentLoaded 事件触发之前按照<script>的放置顺序按顺序执行
   
   

```

![preview](http://segmentfault.com/img/bVcQV0)

## 页面的生命周期

```
1. document的DOMContentLoaded: 该事件发生后，HTML已经加载和解析完成生成了DOM树，但是此时CSSOM树可能还未加载完成，该事件必须在<script>标签运行之后再触发，因为JS有可能操作DOM。但是声明async的脚本不会阻塞DOMContentLoaded。外部样式表不会影响DOM，但是当<link>标签后紧跟<script>标签，<script>标签必须等待<link>标签加载完成，因为有可能涉及对css样式的操作

2. window的load: 外部资源已经加载完毕，样式已经被应用，图片大小也已知了

3. window的beforeunload: 用户正在离开

3. window的unload： 用户几乎已经离开，此时可以调用navigator.sendBeacan(url, data)将有关用户的统计数据保存下来：鼠标，滚动，浏览区域，在后台发送离开后也不会停下来
```

在某些情况下，我们不确定文档是否已经准备就绪。我们希望DOMcontentLoad事件在 DOM 加载完成时执行，无论现在还是以后，可以查看文档状态：document.readyState

`document.readyState` 是文档的当前状态，可以在 `readystatechange` 事件中跟踪状态更改：

- `loading` —— 文档正在被加载。   

- `interactive` —— 文档已被解析完成，与 `DOMContentLoaded` 几乎同时发生，但是在 `DOMContentLoaded` 之前发生。

- `complete` —— 文档和资源均已加载完成，与 `window.onload` 几乎同时发生，但是在 `window.onload` 之前发生。

  

其实现代浏览器为了更好的用户体验,渲染引擎将尝试尽快在屏幕上显示的内容。它不会等到所有HTML解析之前开始构建和布局渲染树。部分的内容将被解析并显示。也就是说浏览器能够渲染不完整的dom树和cssom，尽快的减少白屏的时间。假如我们将js放在header，js将阻塞解析dom，dom的内容会影响到First Paint，导致First Paint延后。所以说我们会将js放在后面，以减少First Paint的时间
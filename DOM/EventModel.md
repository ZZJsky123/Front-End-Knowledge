## Event Model

```
1.Event接口表示在DOM中出现的事件。

2. interface Event{
    // PhaseType
      const unsigned short      CAPTURING_PHASE                = 1;
      const unsigned short      AT_TARGET                      = 2;  // 正在执行
      const unsigned short      BUBBLING_PHASE                 = 3;

      readonly attribute DOMString        type;            // 事件名称
      readonly attribute EventTarget      target;          // 哪个元素触发的事件(多米诺的起始)
      readonly attribute EventTarget      currentTarget;   // 当前哪个元素的事件处理器正在运行
      readonly attribute unsigned short   eventPhase;      // 事件处理的阶段
      readonly attribute boolean          bubbles;         // 事件是否可以冒泡
      readonly attribute boolean          cancelable;      // 事件是否可以被取消
      readonly attribute DOMTimeStamp     timeStamp;      
      void               stopPropagation();
      void               preventDefault();
      void               initEvent(in DOMString eventTypeArg,   // 初始化事件：事件名称
                                   in boolean canBubbleArg,                  是否可以冒泡
                                   in boolean cancelableArg);                是否可以被取消
   }
   
  事件是DOM中重要的元素属性，它的引入主要是为了描述HTML与使用者交互时的行为。它被DOM称为Event，DOM定义了专门的接口去描述。Event有三个重要的属性，target、cutrentarget、bubble，eventPhase(捕获1，运行2，冒泡3)。这四个属性的背后说明了Event一种重要的机制：捕获和冒泡，它们是事件委托的重要原理。
  基本事件： 首先确定HTML5中是否有相应的事件名称 -> 注册事件(为事件设置回调函数) -> 元素监听事件

3. 事件的捕获和冒泡
  当事件被点击时：当前事件传播的三个阶段  捕获 -> 运行 -> 冒泡
  触发事件后，首先进入到捕获阶段，事件从window出发 -> document -> <html> -><body>-> <父元素>
                             -> <子元素>
  如何针对捕获函数写回调： element.addeventListener(type,listener，true)，将addeventListener中的第三个参数captuer设为true，表明捕获进入到该元素时触发。
  当抵达使用者触发的元素标签时，运行程序。
  运行完后从子元素出发(event.target)向上冒泡，执行父元素上的相同事件的回调函数
 如何停止冒泡事件：event.stopPropagation()，在事件回调结尾添加该事件，该函数只能停止当前事件上的一个回调
  
4. 基于HTML已有事件注册和监听的方式
  (1). 将事件当作属性写进HTML中
      <button onclick="回调函数" ></button>
     不推荐： 行为与结构没有分开
  (2). 获取到相应元素节点，为节点添加事件回调
     document,getElementxxx获取节点
     element.onclik=function(){}   // 设置事件回调
  (3). 使用addEventListener
     element.addEventListener(type(‘事件名称’)，listener(回调)，captch)
     
 

interface DocumentEvent {
  Event              createEvent(in DOMString eventType)
                                       raises(DOMException);
};



interface EventTarget {
  void               addEventListener(in DOMString type, 
                                      in EventListener listener, 
                                      in boolean useCapture);
  void               removeEventListener(in DOMString type, 
                                         in EventListener listener, 
                                         in boolean useCapture);
  boolean            dispatchEvent(in Event evt)
                                        raises(EventException);
};

4. 用户自定义事件的方式
    除了HTML规定的事件以外，DOM允许用户自己定义事件，需要经过创造事件 -> 事件初始化 -> element.addEventListener事件注册 -> element.dispatchEvent(evt) (使用dispatchEvent触发该事件)
  
   let evt = document.createElement('Event')    // 创建事件，一个参数：事件名称，不可以随便定义
   evt.initEvent('',isbubble,cacleable)    // 创建事件：事件名称(可自定义)、是否冒泡、是否可取消
   element.dispatchEvent(in Event evt)     
 自定义事件如何被触发：自定义事件是通过dispatchEvent被触发的。
 

```



## HTML事件

Window 事件

```
onafterprint	script	在打印文档之后运行脚本    HTML5
onbeforeprint	script	在文档打印之前运行脚本    HTML5
onbeforeonload	script	在文档加载之前运行脚本    HTML5
onblur	        script	当窗口失去焦点时运行脚本
onerror	        script	当错误发生时运行脚本      HTML5
onfocus	        script	当窗口获得焦点时运行脚本
onhaschange	    script	当文档改变时运行脚本
onload	        script	当文档加载时运行脚本
onmessage	    script	当触发消息时运行脚本      HTML5
onoffline	    script	当文档离线时运行脚本      HTML5
ononline	    script	当文档上线时运行脚本      HTML5
onpagehide	    script	当窗口隐藏时运行脚本      HTML5
onpageshow	    script	当窗口可见时运行脚本      HTML5
onpopstate   	script	当窗口历史记录改变时运行脚本  HTML5
onredo	        script	当文档执行再执行操作（redo）时运行脚本
onresize	    script	当调整窗口大小时运行脚本   HTML5
onstorage	    script	当文档加载加载时运行脚本   HTML5
onundo	        script	当 Web Storage 区域更新时（存储空间中的数据发生变化时）
onunload	    script	当用户离开文档时运行脚本   HTML5
```

表单事件

```
onblur	        script	当元素失去焦点时运行脚本
onchange	    script	当元素改变时运行脚本 
oncontextmenu	script	当触发上下文菜单时运行脚本     HTML5
onfocus     	script	当元素获得焦点时运行脚本    
onformchange	script	当表单改变时运行脚本      
onforminput	    script	当表单获得用户输入时运行脚本   HTML5
oninput      	script	当元素获得用户输入时运行脚本   HTML5
oninvalid    	script	当元素无效时运行脚本          HTML5
onreset	        script	当表单重置时运行脚本。HTML 5 不支持。
onselect	    script	当选取元素时运行脚本
onsubmit	    script	当提交表单时运行脚本
```

鼠标事件

```
onclick	        script	当单击鼠标时运行脚本
ondblclick	    script	当双击鼠标时运行脚本  
ondrag	        script	当拖动元素时运行脚本                    HTML5
ondragend	    script	当拖动操作结束时运行脚本                 HTML5
ondragenter	    script	当元素被拖动至有效的拖放目标时运行脚本     HTML5
ondragleave	    script	当元素离开有效拖放目标时运行脚本          HTML5
ondragover	    script	当元素被拖动至有效拖放目标上方时运行脚本   HTML5
ondragstart	    script	当拖动操作开始时运行脚本                HTML5     
ondrop   	    script	当被拖动元素正在被拖放时运行脚本         HTML5
onmousedown	    script	当按下鼠标按钮时运行脚本
onmousemove	    script	当鼠标指针移动时运行脚本
onmouseout	    script	当鼠标指针移出元素时运行脚本
onmouseover  	script	当鼠标指针移至元素之上时运行脚本
onmouseup	    script	当松开鼠标按钮时运行脚本
onmousewheel	script	当转动鼠标滚轮时运行脚本
onscroll	    script	当滚动元素滚动元素的滚动条时运行脚本
```

媒介事件： audio、embed、img、object 以及 video）中最常用

```
onabort	            script	当发生中止事件时运行脚本
oncanplay	        script	当媒介能够开始播放但可能因缓冲而需要停止时运行脚本
oncanplaythrough	script	当媒介能够无需因缓冲而停止即可播放至结尾时运行脚本
ondurationchange	script	当媒介长度改变时运行脚本
onemptied	        script	当媒介资源元素突然为空时（网络错误、加载错误等）运行脚本
onended	            script	当媒介已抵达结尾时运行脚本
onerror	            script	当在元素加载期间发生错误时运行脚本
onloadeddata	    script	当加载媒介数据时运行脚本
onloadedmetadata	script	当媒介元素的持续时间以及其他媒介数据已加载时运行脚本
onloadstart	        script	当浏览器开始加载媒介数据时运行脚本
onpause	            script	当媒介数据暂停时运行脚本
onplay	            script	当媒介数据将要开始播放时运行脚本
onplaying	        script	当媒介数据已开始播放时运行脚本
onprogress	        script	当浏览器正在取媒介数据时运行脚本
onratechange	    script	当媒介数据的播放速率改变时运行脚本
onreadystatechange	script	当就绪状态（ready-state）改变时运行脚本
onseeked	        script	当媒介元素的定位属性 [1] 不再为真且定位已结束时运行脚本
onseeking	        script	当媒介元素的定位属性为真且定位已开始时运行脚本
onstalled	        script	当取回媒介数据过程中（延迟）存在错误时运行脚本
onsuspend	        script	当浏览器已在取媒介数据但在取回整个媒介文件之前停止时运行脚本
ontimeupdate	    script	当媒介改变其播放位置时运行脚本
onvolumechange	    script	当媒介改变音量亦或当音量被设置为静音时运行脚本
onwaiting	        script	当媒介已停止播放但打算继续播放时运行脚本xxxxxxxxxx onabort script  当发生中止事件时运行脚本

```


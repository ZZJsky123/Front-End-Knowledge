

HTML5包含10个大类别标准：

​      离线offine 、存储storage、连接connectivity、文件访问file assess、语义semantics、音频和视频audio/vid、3D和图形3D/graphics、展示、性能、其他



## Repaint & Reflow

[resource](https://www.phpied.com/rendering-repaint-reflowrelayout-restyle/)

```javascript
1. Repaint : 重绘只发生表面的变化： 元素的可视性， 背景。 不发生布局的改变。

2. Reflow:  重排发生位置和元素的几何尺寸的变化

3. What triggers a reflow or a repaint: 哪些操作会导致 Repaint 和 Reflow
   a. adding, removing, updating DOM nodes
   
   b. Hiding a DOM node 隐藏一个DOM节点， display:none 会发生 reflow 和 repaint
      visibility:hidden (repaint only no geomerty)
   
   c. Moving, animating a DOM node on the  page
   
   d. adding stylesheet.
   
   f. resize window , changeing font size, scrolling : reflow 、repaint
   
 浏览器拥有自己的优化回流的机制， 它会为回流建立一个队列， 当到达一定数量或者时间，批量操作回流， 多个
 回流会合并，最终计算出一个回流。 但是有时 script 操作会阻止浏览器优化， 当它请求一个 node 的样式信息时
  broswer 不得不执行 reflow 从而返回真实的样式信息。
   
4. Minimizing Repaint & Reflow
     a. 核心思想： have fewer repaints & reflows
                 fewer request for style information, broswer can optimize reflow.
                 
     b. 如果是静态页面： 不要直接修改节点的样式， 而是通过修改类名。 如果是动态页面， css 属性需要
                      动态计算， 则通过 cssText 进行修改， 而不是直接修改 node 的 style
                      // bad
                        var left = 10,
                            top = 10;
                        el.style.left = left + "px";
                        el.style.top  = top  + "px";

                        // better 
                        el.className += " theclassname";

                        // or when top and left are calculated dynamically...

                       // better
                       el.style.cssText += "; left: " + left + "px; top: " + top + "px;"

        II. Batch （批量） DOM 改变，并且离线执行。离线指的是不要在当前的 DOM 树上操作。(vnode 树思想)
              . use documentFragment to hold temp change （临时储存 temp 改变）
              
              . clone the node you're able to updata.先对 clone 节点操作， 再将与原先节点
                交换。
                
              .hide the element with display: none (1 reflow, repaint), add 100 changes,                restore the display (another reflow, repaint). This way you trade 2                      reflows for potentially a hundred. 将元素 display：none 添加改变， 然后再
               display：visiable.
               
              . 不要过度计算样式属性， 如果有需要，将他们保存在本地变量中，如下：
                        // no-no!
                        for(big; loop; here) {
                            el.style.left = el.offsetLeft + 10 + "px";
                            el.style.top  = el.offsetTop  + 10 + "px";
                        }

                        // better
                        var left = el.offsetLeft,
                            top  = el.offsetTop
                            esty = el.style;
                        for(big; loop; here) {
                            left += 10;
                            top  += 10;
                            esty.left = left + "px";
                            esty.top  = top  + "px";
                        }
              
            优化的核心思想： 尽可能将多次样式改变放置在1次回流中。 样式重新计算消耗时间。
  
            
 tools： SpeedTracer    for google         
         DynaTrace Ajax for IE

 5. 在 chrome 中修改样式而不计算样式要能快2.5倍， 不触及样式计算要能快4.5倍在修改样式和布局中。
    在 IE 浏览器中没有这样的影响， 即样式修改和样式更新交替 || 样式修改、样式更新无时间差别。
```


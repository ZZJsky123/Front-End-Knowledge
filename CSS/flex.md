## flex



```
Flex 弹性布局，它用于规定父容器和子容器之间的布局关系的，当父元素display设置为flex，此时父元素成为一个弹性伸缩盒
其子元素默认成为flex项，所有子元素“占有”并且“瓜分”父容器的空间

剩余空间：子容器在父容器的“主轴”上还有多少空间可以“瓜分”，这个可以被“瓜分”的空间就叫做剩余空间。


flex-grow：  子容器的瓜分剩余空间的比例(剩余空间 = 父元素宽度 - 子元素宽度综合)，O不伸缩
flex shrink: 如果子容器宽度超过父容器宽度，即使是设置了 flex-grow，但是由于没有剩余空间，就分配不到剩余空间了。这时候有两个办法：换行和压缩。由于 flex 默认不换行，此时就需要用到 flex-shrink 属性进行压缩。
            1.    三个flex item元素的width: w1, w2, w3
            2.    三个flex item元素的flex-shrink：a, b, c
            3.    计算总压缩权重：
            4.    sum = a * w1 + b * w2 + c * w3
            5.    计算每个元素压缩率：
            6.    S1 = a * w1 / sum，S2 =b * w2 / sum，S3 =c * w3 / sum
                  计算每个元素宽度：width - 压缩率 * 溢出空间
         (当子元素宽度未超过父元素高度，该属性不起作用)
flex-basic ： 规定子元素在父元素的起始宽度。

如果有剩余空间，如果设置 flex-grow，子容器的实际宽度跟 flex-grow 的设置相关。如果没有设置flex-grow，则按照 flex-basis 展示实际宽度

```



```
弹性伸缩盒模型
.父元素{
   display: flex       // 父元素会成为一个弹性伸缩盒的容器，所有子元素都会默认成为flex项
   flex-direction：row(默认)/row-reserve/column/column-reserve  // 设置排列方向
   // flex-wrap 定义弹性容器是一个多行容器还是单行容器    
   flex-wrap：wrap(多行)/nowrap(单行)   
   flex-flow：row wrap                //  其是flex-direction 和 flex-wrap的缩写   
}
.子元素{
  flex-grow：   子容器的瓜分剩余空间的比例(剩余空间 = 父元素宽度 - 子元素宽度综合)，默认为1，0不瓜分(无伸缩效果)
  flex-shrink： 默认为1 规定元素宽度超过父元素宽度收缩大小，只能是数字不为负
  flex-basic：  默认为0  指定了 flex 元素在主轴方向上的初始大小
  flex：auto    元素会根据自身宽高设置属性，会缩短适应flex，但不会伸长   0 1 auto
        inital  元素根据自身宽高设置属性，会自动适应flex容器放大或者缩小 1 1 auto
        none:  元素无弹性，根据自身宽高设置属性，不会自动适应flex容器 0 0 auto
}
```

## 图片

![![img](https://user-gold-cdn.xitu.io/2018/6/11/163ecc5c454fb340?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)]

```
四个属性设置弹性盒元素的对齐(alignment)和位置(positioning)

1. justify-content： 只对主轴作用
2. align-*  三个align系列是对交叉轴

align-item：需要施加在弹性盒,规定交叉轴对齐方式
align-self：施加在弹性盒中元素上，声明该属性的弹性元素会屏蔽掉align-item，规定交叉轴对齐方式

六个值： stretch： 拉满整个父元素
       flex-start：从父元素第一行起始 ，即元素向纵轴起点对齐
       flex-end：  从父元素最后一行， 即元素向纵轴终点对齐
       baseline
       center：    从父元素中间高度， 即元素在纵轴中点对齐
       inital
 align-content： 只在多行中起作用，规定多行在容器中排列方式
       flex-start
       flex-end
       space-between
       space-ground
       center
       stretch
```


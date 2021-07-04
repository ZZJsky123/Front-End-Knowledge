## Block

```
1. 可以设置宽度和高度的元素被称为块级元素，默认高度为0，宽度为浏览器宽度
2. 块级元素独自占有一行
3. 常用的块级元素：<div> <h1-h6> <table> <ul> <li> <p> <form> 
4. 块级元素的盒模型：margin border padding width/height
   因为margin是公共区域，所以相邻元素的margin不会叠加而是会重合
   当margin和padding设为百分比时，其计算是相对与父元素的宽度来说的
margin：
   两个值： 上下  左右
   三个值： 上 左右 下
   四个值： 上 右 下 左        同理 padding
```



## inline

```
1. 行内元素只能包含行内元素和数据，创建不会另起一行
2. 行内元素的盒模型：width无效，height无效(改用line-height)
                  margin上下无效 padding上下无效
```



## 块级元素和行内元素的转换

```
display：block/inline/inline-block

inline-block: 会设置元素在行内表现为块级元素，即可设置width/height
   (注：换行符，空格符，制表符合并为空白符，因此inline-block的元素之间
       会存在间隙)
```

BFC

```
【名称】： 块级格式上下文 ，是一个渲染区域，在区域中规定了块级元素的布局方式

【内容】：BFC内的元素与外部元素不相互影响
        BFC内的元素从上到下垂直排列，上下元素垂直方向Margin重叠
        
        
【创建BFC方式】： body元素内部
               float不为none
               display为：flex，block，incline-block
               overflow不为visiable，例如hidden、scroll
               POSITION : FIXED, absolute
               
 【作用】：处理父元素中浮动元素高度塌陷问题， 父元素overflow：hidden
         处理子元素垂直方向Margin重叠问题。
         BFC 可以阻止元素被浮动元素覆盖 (第一个元素是float， 第二个元素设置overflow：hidden)
```



## IE 盒模型 和 标准盒模型的区别

```
两者最大的区别是
 IE盒模型的content:   包括border 和 padding
 标准盒模型的content:  标准盒模型的contnet只包括width和height
```


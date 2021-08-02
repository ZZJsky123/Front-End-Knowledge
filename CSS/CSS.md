 

### 特性

```css
CSS 本身注重的是特性间的【相互联系】和【具象】能力， 对于逻辑要求较低。

【属性】 CSS 是魔法师， 【标签】即 HTML 是魔法石. 【操作系统】是它们所在的世界。【平行世界】： Windows世界、OSX 世界，移动端的 ios 世界 和Andriod 世界。

HTML 标签提供文档元素： 文字、 图片、 列表、 表格、 按钮，内容布局。 标签具备基本的 HTML 属性。 布局依靠标签自身的块级和内联级性质。  魔法石基体是标签名， 内容是石头刻的内容。
 
CSS 标签提供文档元素样式， [通过向便签提供选择器]，将样式添加到对应的内容上。 其中 CSS 中的伪类
和伪元素可以分别对选择器添加样式、 生成相应的元素。

1. 魔法石遵循的世界基本规则：流
2. 魔法石自身是： margin border padding 内容 带有宽度的空心四个盒子
3. 魔法石自身内容是： em框、 内容区、 行内框、 行框、符号盒子。 由字体大小/行间距决定的四个盒子 
4. css 提供： 操控魔法石盒子尺寸、 操控内容盒子尺寸 、 提供块级格式化上下文、 提供层叠上下文
             操控内容样式 其它样式： 定位样式、 结构布局、 动画、 隐藏。
5. css 眼中的魔法石种类： 块级、 内联级(替换 和 非替换)
6. 块级元素嵌套块级元素、 块级元素嵌套内联元素、 块级元素嵌套定位元素：
       问题1; 父元素的流体特性什么时候会被破坏
       问题2： 


《CSS 世界》 中规定
     元素尺寸： border box尺寸      原生的DOM API写作： offsetHeight/offsetWidth
     元素内部尺寸： padding box尺寸  原生的DOM API写作： clientWidth/clientHeight
     元素外部尺寸： margin box尺寸   没有相应的DOM API 

CSS 眼中：  选择器 、 css 属性、  HTML 元素、 流
流： 容器内部的初始环境， 其包括布局方式：元素位置+尺度大小、 方向(从左向右)
    通过对流的破坏获得更丰富的布局方式
```

### 历史

```css
CSS 全称是 Cascading Style Sheets ， 【层叠】的思想是指的的样式的继承， 下层可继承上层元素的样式，同时下层自己定义的样式同时可以覆盖上层。 它的诞生目的是为了更好的展示图文信息，1996年被提出，当时的信息只限于两种： [图片] 和 [文字]。 

CSS2.x: 图文样式语言
CSS3.x: 实现更丰富和更复杂的网页
```

### 流

```
【流】是CSS中的核心机制， 它模仿物理世界的中的水流的特性：
                     1. 水流自动铺满整个容器 
                     2. 放入水流中的木头会依次排列。
    
    CSS中的流： 引导元素排列和定位的一条看不见的“水流”
                     1.  div 在水平流上会铺满整个容器
                     2.  图片和文字按照宽度进行摆放。
                     
【流体布局】： 利用元素‘流’的特性实现的各类布局效果。
```

### 术语

```css
1. 属性; HTML的样式， CSS世界中的魔法师

2. 值： 
    类别：
       a. 整数值          <integer> <number>
       b. 数值： 小数     <number>
       c. 百分比值： 50%
       d. 长度值： 99px
       e. 颜色值： #999

3. 关键字： 关键字是 CSS 中的某一个【英文单词】， 比如属性的名称， 属性值的名称。

4. 长度单位： <number> + 长度单位 = <length>
     应用： 字体长宽、 视区长宽
     a. 绝对长度：  px， pt， cm， mm, pc 实用性不高
     b. 相对长度：  em、 ex CSS3 中的 rem 和 ch

5. 功能符
     定义： 属性值以函数的形式显示， rgb(0,0,0)、 hsla()、 url('css-world.png')

6. 属性值
     定义： 属性冒号后面的值统一称为属性值。

8. 声明
     形式 ： 
             属性名：属性值

9. 声明块：
      定义： 声明块是花括号｛｝包裹的一些列声明

10. 规则或者规则集
      定义： 选择器 + 声明块

11. 选择器种类
      
       a. 类选择器：  以 ‘.’ 号开头，元素之间可以共用同一个类选择器
       b. ID选择器：  以 ‘#’ 号开头， 每个元素需要有唯一的 ID 号。
       c. 属性选择器： 以 '[]' , 如[title]{}, [title="css-world"]{}
                    [title ~= "css-world"], [title ^= "css-word"]{}
       d. 伪类选择器： 前面有一个英文冒号(:), 如：first-child, :last-child
       e. 伪元素选择器：连续两个冒号的选择器， 如::first-line, ::first-letter
    
    关系选择器： 空格、 >、 ~、 +
        后代选择器： 选择所有合乎规则的后代元素。 空格连接
        相邻后代选择器： 仅仅选择合乎规则的儿子元素， 孙子、重孙忽略。 > 连接
        兄弟选择器： 选择当前元素后面的所有符合规则兄弟元素。 ~连接
        相邻兄弟选择器： 仅仅选择当前元素相邻的那个合乎规则的兄弟元素。+连接 IE7以上


注：1.  伪类用于额外规定选择器的行为， :after  | 选择器处于另一个选择器之后会发生的行为。
                                :hover  | 用户指针挪移到元素上时会被激活。
                                :focus  | 用户使用键盘控制，选定元素时则被激活。
   2.  伪元素用于额外规定选择器对应的值的行为。
                      p::first-line{
                                       bold:xx
                                    }
       此时段落包裹的文字的对应的文字值的第一行粗度都会发生改变。对于 ID 选择器和 class
       选择器对应的值是此两种选择器 ➕ 在元素标签上对应的值。
  

未定义行为：
     相同的 CSS 语言， 在不同浏览器具有不同表现时， 具体原因浏览器未定义这种行为，导致在
  一种浏览器中行为按照预计期望， 另一种未发生此种行为。

12 两端对齐

13 右对齐

14 垂直对齐： 垂直表明方向， 即元素在垂直方向上基于什么进行摆放。
    a. 垂直居中对齐： 元素上下留白相同，位居于父元素容器中心。 
 
15.等高布局
```

### Block & inline

#### 概念

```css
块级元素： Block-level element  
内联元素： inline-level element

工作内容： 
       块级盒子： 负责结构
       内联盒子： 负责内容

特性：
       块级盒子： 占用一行， 多个块级盒子换行摆放
       内联盒子： 

HTML 标签在 CSS 眼中分为两类： 块级元素、 内联级元素


CSS 盒子扩展：
               块级盒子     内联盒子
                 |           |
                 |           |
                   marker box    A    存放符号
                       |
                       |
                   块级容器盒子    B    元素宽高

A： display：list-item 由于需要存放项目符号，因此又产生一个附加的盒子。
B： display: inline-block, 要求元素既可以控制宽高，又可以进行一行的对此展示。

inline-block:  内联盒子 - 块级容器盒子 - 元素， 元素可以依靠内联盒子对外实现并排
               摆放， 又可以依靠块级容器盒子控制长宽显示。

总述： 块级盒子占用一行， 控制文档结构布局
      块级容器盒子承载元素， 用于控制元素长宽的对外显示。
      内联盒子简单存放元素，按照元素宽度进行水平[流]摆放
```

#### width/height

```css
width/height 基本特点

1、 width 和 height 不能应用到[行内非替换]元素上。
2、 width：   <length> | <percentage> | 无继承
                       auto(初始值)
                     百分数是相当于包含块
3、 height：  <length> | <percentage> | 无继承
                       auto(初始值)，默认是0
                     百分数是相当于包含块
```

```
width/height 的具体作用细节：

width：auto 下的四种宽度表现：
     1. 充分利用可用空间： 在<div>、 <p> 元素下宽度默认是100%于父级容器   [fill-avaliable]
     2. 收缩与包裹： 元素设置为浮动、 绝对定位、 inline-block 元素或者 table 元素
                   自动将元素宽度收缩为合适                  [shrink-to-fit]
        (紧包性)
     3. 收缩到最小: table-layout:auto, 表格的列元素设置成宽度最小
                                                        [min-content]
     4. 超出容器限制: 内联元素设置成 wihte-space:nowrap.
     
尺寸：
     1. Instrinsic Sizing： 内部尺寸， 元素尺寸由内部元素决定，并非外部的容器
     2. Extrinsic Sizing：  外部尺寸

外部尺寸与流：  流未遭受破坏
    
    1. 正常流宽度 ： 正常流带来的外部尺寸自动分配
    2. 格式化宽度 ： 定位元素，其空间大小由最近的定位父元素宽度决定。(position 有这样的特性)
    
   上述的四种宽度表现，第一种 [fill-avaliable] 下的尺寸是外部表现， 具体是 <div> 元素标签放入到水平流中时自动铺满整个水平流。

格式化宽度： 格式化宽度仅出现在 '绝对定位模型' 中， position: absolute / fixed 元素中。 默认情况下， 绝对定位元素的宽度表现是包裹性的， 宽度由内部尺寸决定。 但是， 当left/right ,或者 top/bottom 同时出现时[其宽度大小相对于最近的父元素，其 position 属性值不为 static ]

内部尺寸与流： 流遭受了破坏 (浮动元素、 position 元素、 inline-block 元素)
    1. 紧包性(包裹性): 自适应内容宽度， 不破坏布局
    2. 首选最小宽度： 内容样式大于布局， 会有最小宽度
    3. 最大宽度
    
   内部尺寸：元素尺寸由内部元素决定。 元素没有内容时，宽度为0。

   包裹性： 元素尺寸由内部元素决定， 但永远小于包含块的属性。即当元素设置为incline-block,不论元素的内容有多少，都不会超过容器。
   📦性的意义： 智能宽度选择。按钮是典型的incline-block元素， 文字边长宽度加大超过240px,自动换行。
   
   首选最小宽度： width = 0；文字和图片的权重远大于布局，因此不会被设置0，而是采用最小宽度。东亚文字的最宽度： 每个汉字的宽度； 西方文字：最小宽度为连续的英文字符， 遇见非英文字符会将其换行。
   最小宽度的意义：
   

最大宽度：
    1.  "最大宽度"实际等同于“包裹性”元素 white-space:nowrap
    
    最大宽度的意义： 实现平滑的滚动， 滚动到底的时候才帧的到底。
              
```

#### 盒尺寸

```css
元素种类：
      1. 按照结构： 块级元素、 行内元素、 浮动元素、 定位元素    (不同的盒模型)
      2. 按照可替换性： 替换元素、 非替换元素
  
  元素布局方式特性：
                                --·水平格式化       margin  padding
       结构元素 + 内容可替换元素 ->                       border
                                --·垂直格式化        width  height
   
  1. 原则1： 所有元素都生成元素框
  2. 原则2： 文档流的默认方向是水平方向即从左到右，(空间的占用方向)
  3. 原则3： 块级元素水平部分总和是父元素的 width
  4. 原则4： 元素使用空间的方式： 占用(默认的水平流)、 折叠(负边距)、 覆盖(脱离文档流)     
```

```css
1. 所有文档元素都生成一个矩形框称为元素框
2. 只有 width 和 margin 可以设置成 auto ，其余宽度是：0 / 具体值
3. 元素框在元素之间只提供很少的空间，一般元素之间的空白是由3种方式产生
    a. 增加内边距  b. 增加外边距  c. 增加内边距和外边距

margin:  <length> | <percentage>
           初始值与元素浏览器有关
               应用所有元素
                无继承性
            百分值相当于包含块的 width
   1. margin-left、 margin-right、 width 的值不能全是固定值，否则 margin-auto 会被 
      自动设置 成 auto
   2. margin-top、 margin-right、 margin-bottom、 margin-left 初始值为 0。
   3. 负外边距： 空间折叠
   4. 行内元素的外边距： 非替换元素不受 marghin-top 和 margin-bottom 的影响，只受
                      margin-left 、 margin-right 的影响。 若边距是负的则，左
                      负边距会让元素向左移动，右负边距使得其后元素向左移动。
                      替换元素设置外边距，会影响到行高。

border： 宽度、 样式 、 颜色  (顺序不重要)
         1. 元素背景： 内容、内边距、边框
         2. border-style:  none | hidden | dotted | dashed | solid |double
                                | groove | ridge  | inset  | outset| inherit
                           未定义 (初始值)
                           应用所有元素
                           无继承性
            border-style: 上 右 下 左
         3. 单边属性： border-top-style、 border-right-style、 boder-bottom-
                     style、border-bottom-style、 border-left-style 初始值为 
                     none，单边属性需要写在 border-style 之后才可以起到覆盖的作用。
         4. border-width： thin|medium|thick|<length>|inhert
                               未定义 (初始值)
                               应用所有元素
                               无继承性
         5. 单边属性： border-bottom-width、 border-top-width、 border-left-
                     width、 border-right-width. 初始值为 none
         6. 边框样式为 0 的边框不存在。
         7. border-color ： <color> | transparent
                                 未定义初始值
         8. border-top-color、 border-right-color、 border-bottom-color
            border-left-color,元素的颜色(初始值）
         9. 单边框属性设置: border-left、 border-right、 border-top、 
            border-bottom
         10.行内元素： 不论为行内元素的边框指定怎样的宽度， 元素的行高都不会改变。

padding： <length> | <percentage>   (内边距绝对不能为负)
                未定义(初始值)
                应用于所有元素
                百分数相对于包含块的width
         
          1. 默认元素没有内边距， 段落之间的间隔传统一般只由外边距保证，没有内边距
             元素的边框会与元素本身内容接近，因此在元素上放边框时，可同时增加内边距。
          2. 单边 padding 设置， padding-top、 padding-bottom、 padding-left
                               padding-right。
          3. 行内非替换元素， padding 设置 left 和 right 会像外边距一样占用额外空间
                           设置 top 和 left时当有背景色的情况下，会显示背景色的延展
                           因为 margin 和 padding 设置 top 和 bottom 其实是会
                           发生作用，只不过不是空间占用，而是空间重叠， 由于margin 
                           没有背景色因此无法被观察到。
           4. 行内替换元素， 内边距会影响替换元素所占用的空间。	
```

```css
块级容器盒子是由 4 个盒子构成

    1. content box
    2. padding box
    3. border box
    4. margin box

这四个盒子在CSS中还有具体的属性名称与之对应：
     
     1. content-box
     2. padding-box
     3. border-box
     4. margin, margin box 没有具体的盒子，其背景永远是透明的。

content box 环绕着 width/height 给定的的矩形。 width 尺寸作用在content box上。

CSS 流体布局下宽度分离原则：
   1. CSS 中的 width 属性不与影响宽度的 padding/border/margin 属性共存
   
   2. width 属性独占一层标签， 而 padding、border、margin利用流动性在内部自动
      自适应。
      
  宽度分离原则提出的两个基本前提：
        1. width 是作用在内在盒子的 contnt box之上， 因此将 width 与 padding
           /border 放在一起， 最终元素的宽度大于所设定的 width 的宽度。
         
        2. 利用[流]式布局的方式，而并非[砖块]式布局。 块级元素的默认 width：auto
           因此固定好父类的 width 后， 子类只需要控制 margin/border/padding，
           元素会自动完成布局。
           
 box-sizing: 改变 width 和  height 的作用细节
    width 作用于content box 一直被视为与现实感官不符合，设置 width=xx, 自然
  希望元素整体呈现 width 的宽度，而并非仅仅是 width 的内容。 box-sizing 的出现
  使得开发者可以修改 width 作用域的方式。
              .box1{box-sizing: content-box;}  /* 默认 */
              .box1{box-sizing: padding-box;}
              .box1{box-sizing: border-box;}  /* 全支持 */ 
              .box1{box-sizing: margin-box;}  /* 未支持过 */

 box-sizing: 最大作用是解决替换元素的宽度自适应问题。 替换元素的特性尺寸由内部元素决定
             例如 <textarea>, 即使设置其 display:block, 发生替换时不会自适应容器
             宽度。通过设置 width：100%； box-sizing：border-box, 可以使其自适应
             布局。 在未出现 box-sizing 之前， 通过在外部嵌套<div> 标签设置固定的
             border/padding, <textarea> 只设置 width:100%, 其余为0

简单而单纯的 Height
  在 CSS 中默认的文档流方向是水平， 宽度有限因此有较复杂的分配机制， 高度资源充足分配机制相对简单。
  
height：100%问题
 在 css 中， width在父元素设置成 auto， 其在子元素中依然可以设置 width 值为百分比。对于 height 来说， 父元素设置 height:auto, 则子元素下的 height 值会被忽略。即在普通文档
流中的元素其父元素如果要生效，则其父元素必须有一个可以生效的高度值。
                            html, body{
                                height:100%
                            }
规范说明：
  1. 如果包含块的高度没有显示指定(即由内容决定)， 并且元素非绝对定位，则计算值为auto
     因此 'auto' * 100/100 = NaN
  2. 如果包含块的宽度没有显示指定，并且元素并非绝对定位，则产生的布局在CSS2.1中属于未定义
     由浏览器自行决定如何计算。

元素支持 height：100%效果
  1. 设定显示高度值
                  html, body{
                               height:100%
                            }
  2. 使用绝对定位
        非绝对定位下，元素的高度是相当于 content-box 计算
        绝对定位下， 元素的高度是相当于padding box计算， 即将padding 的大小值计算在
        内。
```

#### 内联元素

```css
文字、 图片、 按钮、 表单控件都是内联元素

内联元素的外在盒子都是内联盒子。  并且内联元素中的内联指的是外在盒子， 与display：inline
是不同的。 内联元素的 display的默认值都为incline

内联盒模型
     <p> where is the goal ,where I will go </ p>
      1                  2
1. 内容区域: 元素自身，即文本中的背景色区域    2
2. 内联盒子：元素的外在盒子与其并列的块级盒子，其决定不让元素按块布局而是排成一行 2
3. 行框盒子： 每一行都是一个行框盒子， 每行上的一个个内联盒子组成了行框盒子      2
4. 包含盒子：<p>标签就是一个包含盒子， 此盒子由一行一行的行框盒子组成。         1

幽灵空白节点：HTML5 的所有内联元素的解析和渲染表现的像其之前有一个空白节点。
行框盒子的高度由内部最大的内联和子高度决定。
```

### 块级元素列表

```html
<address> 联系方式信息

<article> 文章内容

<aside> 伴随内容

<blockquote> 块引用

<dd> 定义列表中定义条目描述

<div> 文档分区

<dl> 定义列表

<fieldset> 表单元素分组

<figcaption> 图文信息标题

<figure> 图文信息组

<footer> 区段尾或者页尾

<form> 表单

<h1-6> 标题级别

<header> 区段头或者页头

<hgroup> 标题组

<hr> 水平分割线

<noscript> 不支持脚本或者禁用脚本时显示的内容

<ol> 有序列表

<output> 表单输出

<p> 行

<pre> 预格式文本

<section> 页面区段

<table> 表格

<tfoot>脚注

<ul> 无序列表
```



### 内联元素列表

```html
<canvas> 绘制图形
<aduio> 音频播放
<video> 视频 
<b></b> ： 强调文字
<big></big> : 已经废弃， 加大字体一号
<i></i> ： 斜体展示文字
<small></small>： 文本字体变小一号
<tt></tt>： 已废弃
<abbr>： 强调字母单词缩写，斜体➕下划线
<acronym></acronym> ： 已废弃
<cite></cite> ： 标记著作名/书/歌
<code></code> ：呈现一段计算机代码. 默认情况下, 它以浏览器的默认等宽字体显示.
<dfn></dfn>： 标记术语的定义实例
<em></em> ： 强调或者重读
<kbd></kbd> ：表示用户输入，它将产生一个行内元素，以浏览器的默认monospace字体显示
<strong></strong> ： 文本重要性
<samp></samp>：标识计算机程序输出，通常使用浏览器缺省的 monotype 字体
<var></var>：表示数学表达式或编程上下文中的变量名称， 通常以斜体表示
<a></a> ： href 属性创建通向网页、文件、电子邮件地址或任何其他 URL 的超链接
<bdo></bdo> 
<br> ：文本中生成一个换行（回车）符号
<img> : 图片
<map></map>： 与 <area> 属性一起使用来定义一个图像映射(一个可点击的链接区域).
<object></object> ：[HTML 嵌入对象元素] 表示引入一个外部资源，这个资源可能是一张图片，一个嵌入的浏览上下文，亦或是一个插件所使用的资源
<q></q> 封闭的并且是短的行内引用的文本. 这个标签是用来引用短的文本，不要引入换行符
<script></script> 
<span></span> :短语内容的通用行内容器，并没有任何特殊语义。
<sub></sub> :定义了一个文本区域，出于排版的原因，与主要的文本相比，应该展示得更低并且更小[下标]
<sup></sup>:定义了一个文本区域，出于排版的原因，与主要的文本相比，应该展示得更高并且更小。 [上标]
<button></button>
<input>： 基于Web的表单创建交互式控件
<label></label> ：元素（标签）表示用户界面中某个元素的说明。可和 <input> 连用
<select> ：表示一个提供选项菜单的控件
<textarea>：示一个多行纯文本编辑控件，当你希望用户输入一段相当长的、不限格式的文本，例如评论或反馈表单中的一段意见
<iframe></iframeiframe>
    
MDN： https://developer.mozilla.org/zh-CN/docs/Web/HTML/Inline_elements
```

### 盒尺寸深入

#### content

```css
替换元素： 内容可通过属性更改， 即标签的值是与属性有关的。
    e.g: <img>、 <cavans>、 <video>、 <audio,>

替换元素的特性：
      a. 内容可更改， 但外观不可更改。
      b. 一般有自己的尺寸。<cavans>、 <video>、 <iframe>  默认是 300*150 
         <img>默认是0。
      c. 所有替换元素都为内联元素
      d. 将内联元素 display 设置成 block，尺寸计算规则与替换元素下计算规则一致。
      e. img 在不同浏览器下生成的默认尺度不一样
      f. fireFox 下忽略 img 元素的src属性，其会变为内联非替换元素，此时设置宽、高
         无效
      g. 替换元素的固有尺寸无法被修改， html 中的 width/height 修改图片是因为修改了图片          的填充区域
         object-fit: fill    填充   
         object-fit: none    不受影响
         object-fit: contain  受影响但是按照固定比例

替换元素与非替换元素的差距：
         a. 替换元素具有 src 属性， fileFox 下 img 元素缺少 src 会变成行内非替换
            chrome 浏览器下缺少 src 和 alt="" 同样会发生上述变换
         b. 替换元素和非替换元素之间只隔了一个 CSS content 属性！
            i. chrome 浏览器下， 所有元素都支持 content 属性，当非替换元素声明content
               属性会被置换为替换元素。
            ii. 点击图片更换为另一张图片，可使用：hover 声明content属性即可完成替换，但
                是当点击图片下载时依然是原始图片
                <img src="laugh.png">
                img:hover { 
                   content: url(laugh-tear.png); 
                 }
            iii. 官网的标志往往都会使用<h1>标签, 包含使用名称和背景图
                      <h1>《CSS 世界》</h1> 
                            h1 { 
                             width: 180px; 
                             height: 36px; 
                             background: url(logo.png); 
                             /* 隐藏文字 */ 
                             text-indent: -999px; 
                           }
                     修改：  h1{content: url(logo.png)} 文字内容将被图片替换但是
             SEO 抓取的依然是文本信息。
            

注： css 世界建议 img{display：inline-block}

替换元素尺寸：
      a. 固有尺寸
        ：替换内容固有的宽高

      b. HTML尺寸
        : 替换元素标签原生的尺寸操作，img 中的 width/height、 input中的size、 
          texarea中的cols/rows

      c. CSS尺寸
        : CSS 尺寸特指可以通过 CSS 的 width 和 height 或者 max-width/min-width 和
          max-height/min-height 设置的尺寸，对应盒尺寸中的 content box。
 
Content 与 替换元素的关系
     a. content 属性生成的内容都是替换元素，称为匿名替换元素
     b. content 生成的文本无法选中和复制，无法被SEO 只有视觉上的效果。
     c. content 动态生成值无法获取，content：counter(icecream)。

content 内容生成技术：
    : 在实际项目中，content 属性几乎都是用在::before/::after 这两个伪元素中.
    a. content 辅助元素生成， 用于清除浮动 / 实现垂直居中/上下边缘对齐
       清除浮动： .clear::after{
                     content:''
                     display:block;  （也可是table）
                     clear: both
                  }
       自动等宽布局且底部对齐的柱状图：
      .box { 
             width: 256px; height: 256px; 
             /* 两端对齐关键 */ 
             text-align: justify; 
            } 
            .box:before { 
             content: ""; 
             display: inline-block; 
             height: 100%; 
            } 
            .box:after { 
             content: ""; 
             display: inline-block; 
             width: 100%; 
            } 
            .bar { 
             display: inline-block; 
             width: 20px; 
            } 
            对应的 HTML 代码如下：
            <div class="box"><i class="bar"></i> 
             <i class="bar"></i> 
             <i class="bar"></i> 
             <i class="bar"></i> 
            </div>
      b. content 字符内容生成
         
          换行符：\A、 \F  LF:将光标垂直移动到下一行  CD： 光标从下一行开头开始
          利用换行符实现: 正在加载... three dot 动态移动
        正在加载中<dot>...</dot> 
        dot { 
            display: inline-block; 
            height: 1em; 
            line-height: 1; 
            text-align: left; 
            vertical-align: -.25em; 
            overflow: hidden; 
        } 
        dot::before { 
            display: block; 
            content: '...\A..\A.'; 
            white-space: pre-wrap; 
            animation: dot 3s infinite step-start both; 
        } 
        @keyframes dot { 
            33% { transform: translateY(-2em); } 
            66% { transform: translateY(-1em); } 
        }
         
         

      c. content 图片内容生成： 直接用 url 显示图片

      d. content attr 属性值内容生成
           img::after { 
             /* 生成 alt 信息 */ 
             content: attr(alt); 
             /* 其他 CSS 略 */ 
           }
          attr 中属性值得内容不用加引号
      
      e. content计数器  重中之重           
```

  #### padding

```css
1. 内联元素 padding 只会影响水平方向， 不会影响垂直方向：
      a. 因为内联元素没有可视宽度和可视高度的说法 clientHeight、 clientWidth 永远是0， 垂直方向行为完全受 line-height 和 vertical-align 影响。
      b. 《css 世界》将这种行为称为叠加。 css 中一共两种叠加，一种是纯视觉层叠， 不影响外部尺寸； 另一种会影响外部尺寸。
      c. incline 元素的 padding 层叠属于后者，证明方式是 overflow:
auto, 是否会超出层叠区。

   padding 无负值， 其宽度相当于元素宽度计算。

2. padding的作用： 利用层叠效果我们可以增加按钮的区域， 不改变布局但区域得到有效增加

3. 标签元素内置的 padding  
     a. ul 默认padding-left：40px (chrome 浏览器中)
        当 font-size很小项目符号就会距离左边距很远， font-size很大会距离超出 ul、ol
         ol, ul { 
         padding-left: 22px;   当文字大小是12px、 14px下较好的设置值。
        }
    b. 表单元素大多都具备内置 padding
       <button> /  <input> / <texterea> / <select>
      <button> 元素下的 padding：
           i: chrome 浏览器使用 button：{padding:0},可消除按钮留白
              fieFox浏览器使用 button::-moz-focus-inner { padding: 0; }
           ii: IE7浏览器 button 文字变多按钮padding会逐渐扩大
               button{ overflow: visiable} 消除 padding 增长

4. padding 与 background-clip 实现 css 图行绘制

 双层圆点效果：
           .icon-dot { 
                 display: inline-block; 
                 width: 100px; height: 100px; 
                 padding: 10px; 
                 border: 10px solid; 
                 border-radius: 50%; 
                 background-color: currentColor; 
                 background-clip: content-box; 
          }
```

  #### margin

```css
1. margin 与元素的内部可视尺寸
   margin 对尺寸没有影响， 只有元素是“充分利用可用空间”， margin 才可以改变元素的可视尺 
   寸。
           <div class="father"> 
           <div class="son"></div> 
           </div> 
           .father { width: 300px; } 
           .son { margin: 0 -20px; }
   此时 .son 元素所在的标签采用“充分利用可用空间” width 的长度会被加长

2. 利用 margin 实现左侧定宽的两栏自适应布局
   .box{ overflow:hidden;}
   .box > img {float:left}
   .box > p {margin-left: 140px}
    <div class="box"> 
     <img src="1.jpg"> 
     <p>文字内容...</p>
    </div>
 文字内容就会根据.box 盒子的宽度变化而自动排列，形成自适应布局效果.

3. margin 利用改变元素尺寸的特性来实现两端对齐布局效果。
    ul { 
       margin-right: -20px; 
     } 
    ul > li { 
     float: left; 
     width: 100px; 
     margin-right: 20px; 
    }

4. 滚动容器底部留白使用 margin-bootom 可在各样浏览器下完成功能。

5. margin 合并
   1. 相邻兄弟元素发生合并
   2. 父子元素发生合并： 外套 div 不会影响到原来的布局
   3. 空级元素的 margin 合并

   ： 块级元素的上外表距与下外边距有时会合并为单个外边距
   特点： 只发生在块级元素， 不包括浮动和绝对定位元素(他们也可以让元素块状化)
   发生场景： 
       a. 相邻兄弟元素 margin 合并
       b. 父级和第一个/最后一个子元素
   
   针对 b 解决办法：
     针对 margin-top 合并
       i.  父元素设置为块状格式上下文元素
       ii. 父元素设置border-top值
       iii. 父元素设置 padding-top 值
       iiii. 父元素和第一个子元素之间添加内联元素进行分割
     针对 margin-bottom 合并
         i. 父元素设置为块状格式上下文元素
        ii. 父元素设置border-bottom值
        iii. 父元素设置 padding-bottom 值
        iiii. 父元素和最后一个子元素之间添加内联元素
     
     margin 合并原则： 正正取最大值 正负取相加 负负取最负 

margin：auto ： 可替代  float 实现元素的向左向右对齐
     1. 一侧固定值， 一侧 auto 则 auto 自动填充剩余空间
     2. 两侧是 auto 平分剩余空间
     3. 触发 margin:auto  无法垂直居中的原因， 是子元素的高度不是自动填充，即使父元素&子元素都设置了 
        height 剩余高度空间也不是差值， 因此margin：auto 计算值也为0. 解决办法可以使用 position 设置 
        top&bottom&left&right=0 子容器空间高度被自动填满， 此时 margin:auto 可以起作用

margin 无效：
     1. display 计算值 inline 的非替换元素的垂直 margin 是无效的，对于内联替换元素，
        垂直 margin 有效，并且没有 margin 合并的问题，所以图片永远不会发生 margin 合并。
     2. 鞭长莫及导致的 margin 无效：  需要深入理解 float 和 overflow
     3. 内联特性导致的 margin 无效：  需要对 vertical-align 和 内联盒模型 有深入的理解
```

#### border

```
border：1px solid red
border-top
border-bottom:
border-left;
border-right;

border-style：
border-color:


```



### 内联元素和流

#### 内联元素

```
内联元素的基本术语                  from --权威指南
 引导： <<CSS 世界>> 中内联元素涉及到的属性多， 并且这些属性大多具有继承作用，是CSS世界中最重要的。

匿名文本： 指未包含在行内元素中的字符串
   <p> I'm <em>so</em> happy! </p>  I'm  happy|都是

em 框： em 框针对的是字体， font-size的值确定各个 em 框高度
       又称为字符框

内容框： 非替换元素内容框是由行内字体元素的 em 框串起来的，替换元素
       中内容区就是元素的固有高度➕可能的外边距、内边距、边框。
《CSS 世界》： 背景色所在的区域为内容区

行间距：(font-size - line-height)值, 该值一分为2， 一部分用于上边， 一部分用于下边。

行内框： 非替换元素行内框的高度正好等于 line-height 的值。
        替换元素行内框的高度正好等于 内容区

行框： 该行中出现的行内框的最高点和最低点的最小框。

a. 行内元素背景应用于内容器及所有的内边距。
b. 行内元素的边框要包围内容区及所有内边距和边框。
c. 非替换元素的内边距、边框、外边距不会影响元素行内框高度。
d. line-height 值等于 内容区+上下边界

```

```css
1. 英文字母x--- 决定基线
  
  基线 (baseline) 应用于垂直方向的排版或者对齐。 
       a. line-height 行高定义为两基线的间距。
       b. vertical-align 默认值是基线
       c. 内联元素默认是基线对齐
  
  基线被定义为字母 x 的下边缘
  
  x-height: 小写字母x的高度
       vertical-align： middle，元素垂直对齐的方式是基线+1/2x-height高度。
  
  ex: 指的是小写字母x的高度， 数值上等于 x-height， 应用价值在于实现垂直居中对齐
     icon-arrow { 
         display: inline-block; 
         width: 20px; 
         height: 1ex;   // 利用内联元素默认是基线对齐这一特性
         background: url(arrow.png) no-repeat center; 
     }

2. 内联元素的基石line-height

   1. <div> 的高度由哪个css决定 是font-size 还是 line-height？
            答案： line-height
   2. 在内联元素中， 非替换元素的可视高度完全由 line-hegiht 决定。
   3. 内联元素的高度由固定高度和不固定高度组成： 文字高度 + 行距
   4. 宋体的 em-box 和 内容区域是等同的。
   5. 替换元素的尺寸不受行高影响，行高只能影响替换元素生成行框盒子时前面的空白幽灵节点
      的高度。
            .box { 
                 line-height: 256px; 
                } 
            <div class="box"> 
            <img src="1.jpg" height="128"> 
            </div>
      虽然div的高度是256， 但是图片的高度依然是设置的128， 256是作用在了前面的幽灵空白节点上。
   6. 对于图片和文本混合的行， line-hieght 只能决定最小高度。
   7. 对于块级元素， line-height没有作用， 在平常开发块级区域发生视觉变化是因为内联元素的高度改变从而实现的。
   8. line-height 实现近似的垂直居中： 主要是利用行距上下等分的原则，近似是由于文字字形的垂直中线位置要比生成的真正的行框盒子中线位置低， 但是由于一般字体大小较小误差在1px左右因此肉眼看不出来
         .title { 
             line-height: 24px; 
            }
       多行文同时需要借助 vertical-align改变默认的基于基线的对齐方式.
        <div class="box"> 
             <div class="content">基于行高实现的...</div> 
        </div>
       .box { 
         line-height: 120px; 
         background-color: #f0f3f9; 
        } 
        .content { 
         display: inline-block; 
         line-height: 20px; 
         margin: 0 20px; 
         vertical-align: middle; 
        } 
     注释: content 选择器将div标签转化成 incline-block 这样设置line-height 可通过影响幽灵空白节点高度而决定子元素的行高. 

   9. line-height 的各种值：
        a. 数值： line-height：1.5  终值是和当前 font-size 值相乘后的值。
        b. 百分比： line-height：150% 终值是和当前 font-szie 值相乘后的值
        c. 长度值： line-height： 21px / line-height: 1.5em
  
   子元素在发生继承的时候， 对于b/c继承的是终值计算之后的值， 因此若子元素的字体过大则会排版混乱
但是对于a 来说继承的是line-height：1.5 因此可自适应子元素字体大小。
   在实际开发中我们也可以使用：
        * {
            line-height:150%   // 也可以实现 数值的效果
         }
    为什么在body下使用数值的line-height， 因为很多替换元素有自己的默认值，而继承是最弱的权重，因此通过通配符的方式重置默认属性。 
    或者使用下述方式：
                 body { 
                     line-height: 1.5;
                  }
                button，input{
                    line-height:inherit;
                }

     10. line-height 的大值特性
                     .box { 
                         line-height: 96px; 
                        } 
                      .box span { 
                         line-height: 20px; 
                       }

                       .box { 
                         line-height: 20px; 
                        } 
                        .box span { 
                         line-height: 96px; 
                       }
                  两个 box 的高度分别是多少：  全都是96px！
        结论： 无论内联元素的 line-height 如何设置最终父级元素是由数值较大的 line-height 
              决定。
        原因： <span>是一个内联元素， 自身是一个内联盒子， 内联盒子外被包裹一层行框盒子， 行框
              盒子前有一个宽度为 0 的空白节点。行框盒子的高度由最大的内联盒子高度决定。因 
              此.box的高度都为96px。
   
3. line-height 的同伴 vertical-align
       ：凡是 line-height 起作用的地方 vertical-align 也一定起作用。
   问题A
        <div class="box"> 
         <span>文字</span> 
        </div>
       .box { line-height: 32px; } 
       .box > span { font-size: 24px; } 
      问题： box 的高度是多少？   答案： >32px 因为有 vertical-align 起作用
 
    1. vertical-align 家族
       a. 线类： baseline、 top、 middle、 bottom
       b. 文本类： text-top、 text-bottom
       c. 上标下标类： sub、 super
       d. 数值百分比类： 20px、 2em、 20%
    i. vertical-align 的计算值是正值则往上偏移， 如果是负值则往下偏移。
   ii. 使用 vertical-align 的数值计算有很好的浏览器兼容性。
  iii. vertical-align 的数值相对于 line-height 计算
  
   2. vertical-align 只能作用于display:incline、incline-block
      incline-table table-cell
    注： 在table-cell中设置的 vertical-align 其内部子元素会完成垂直居中，但是它作用的
         不是子元素而是其自身， 因此其内部是块级元素同样可以有垂直对齐效果。

4. 分析问题A的原因， 由于line-height 声明的是32 因此子元素行高确实是32，但是由于前置
   的幽灵空白符号字体大小和子元素字体大小不匹配， 子元素字体大于幽灵空白符字体因此在实现
   基线对齐时，大字符的基线更靠下，幽灵字符需要向下移动，从而超过了行高。
                          解决方式在.box中声明相同字体大小。

   产生间隙的三大原因： 空白字符的产生、 vertical-align基线对齐、 line-height 产生间距。
                    在发生对齐的过程中产生了间隙。
     图片底部空白间隙问题：  
                       .box { 
                         width: 280px; 
                         outline: 1px solid #aaa; 
                         text-align: center; 
                        } 
                        .box > img { 
                         height: 96px; 
                        }
    解决：  图片块状化 ： 消灭空白字符
           line-height：0   消除间距
           vertical-align 换用其他对齐方式
           font-szie=0；  基线和中线会重合到一起。
    
    margin 失效问题： 图片不会完全移出容器
            <div class="box"> 
                 <img src="mm1.jpg"> 
            </div> 
                .box > img { 
                 height: 96px;  
                 margin-top: -200px; 
              }
    原因： 同样是幽灵空白节点的问题， 内联元素如果不是主动触发位移不会跑到计算容器之外
          空白字符通过基线对齐方式将图片的下边缘限制在底部。

5 深入理解 vertical-align 线性类属性 
   
  1). inline-block 与 baseline
    a. vertical-align 属性的默认值 baseline 
       i.  文本之类的内联元素那里就是字符 x 的下边缘.
      ii.  替换元素则是替换元素的下边缘。
      iii. inline-block 元素：一个 inline-block 元素，如果里面没有内联元素，或者                  overflow 不是 visible，则该元素的基线就是其 margin 底边缘；否则其基线就是元 
         素里面最后一行内联元素的基线。
    
```

### 流的破坏和保护

#### float

```css
前言：
    float 属性的原本作用“只是为了实现文字环绕效果”

作者观点： 无宽度， 无浮动

float 属性： 
      a. 包裹性 ：自动将浮动元素宽度收缩为合适的子元素宽度大小。
      b. 块状化并格式化上下文： float值不为none display 值是 block 或者 table
      c. 破坏文档流： 父元素高度塌陷，正是 float 实现环绕的核心机制
      d. 没有任何 margin 合并
不要指望使用 text-align 属性控制浮动元素的左右对齐，因为 text-align 对块级元素是无效的。
      
float 发生环绕作用机制
      a. 高度塌陷： 父元素在未设置高度时，子元素为 float 其高度不会计算入父元素高度中。
      b. 行框盒子和浮动元素的不可重叠性。即使margin-left：-100 也不可以改变。
   高度塌陷： 父元素在不设置高度的前提下， 子元素为float时，该子元素的高度不计入
            父元素高度下。
 
float 发射环绕作用机制两个细节：
      a. 浮动锚点： float 元素所在流中的一个点，该点本身不浮动。表现而言像
                  一个没有margin、 border、 padding 的空白元素，当 float 元素前后都是块元素，则
                 浮动锚点相当于行框，帮助对齐。
      b. 浮动参考:  浮动元素对齐参考的实体。 其参考实体是行框盒子。因此在两行的文本中， 其后的float 元素
                   会跟在第二行而并非是第一行
      
float 元素脱离文档流， margin-left 不会以上一个 float 的 margin 为起始点进行定位
float 实现两栏布局： 核心在于第二栏设置 marigin-left

   两栏： .animal 元素没有浮动，也没有设置宽度，因此，流动性保持得很好
        <div class="father"> 
         <img src="me.jpg"> 
         <p class="animal">小猫 1，小猫 2，...</p> 
        </div> 
        .father { 
         overflow: hidden; 
        } 
        .father > img { 
         width: 60px; height: 64px; 
         float: left; 
        } 
        .animal { 
         margin-left: 70px;  相当于窗口边缘， 需要保证长度大于图片长度， 从而不发生文字环绕
        }
  三栏：
      .prev { 
         float: left; 
       } 
      .next { 
         float: right; 
       } 
      .title { 
         margin: 0 70px; 
         text-align: center; 
       }

clear ： none | left | right | both

clear 属性的解释是：“元素盒子的边不能和前面的浮动元素相邻，clear 属性对“后面的”浮动元素是不闻不问的。
      clear 并不是设置到浮动元素上，而是设置到抗浮动的元素上

clear ： 只能作用在块级盒子上， 因此使用:after生成伪元素默认是内联，要设置display：block 属性
                    .clear:after { 
                     content: ''; 
                     display: table; // 也可以是'block'，或者是'list-item' 
                     clear: both; 
                    }

clear:both 的作用本质是让自己不和 float 元素在一行显示，并不是真正意义上的清除浮动。
    1. 如果 clear:both 元素前面的元素就是 float 元素，则 margin-top 负值即使设成-9999px，也不见任何 
       效果。按照设想应该是向上平移，但是由于 clear:both阻止与浮动元素同行，因此无法移动。
    2. clear:both 后面的元素依旧可能会发生文字环绕的现象， 当用于生成的抗浮动伪元素无宽高。

总： clear:both 只能在一定程度上消除浮动的影响，要想完美地去除浮动元素的需要使用： overflow

```

#### BFC

```
block formatting context： 块级格式化上下文

特性： 
       1. 一个元素具有 BFC 内部子元素不会影响外部元素， 外部元素不会影响到内部。
 
作用： 
       1. 实现健壮、 智能的自适应布局。自动填满容器
       2. 
    
    延伸： 根据第一条，BFC 元素不
          会发生 margin 重叠， 重叠是会影响外部元素的。
       2. BFC 可以清楚子元素浮动， 因为父元素一旦高度塌陷则会影响到后面的
          布局。
触发 BFC：
       1. <html> 根元素
       2. float 值不为 none
       3. overflow 的值为 auto、scroll或 hidden
       4. display 的值为table-cell、table-caption 和 inline-block 中的任何一个
       5. position 的值不为 relative 和 static。
       

float 不为none：float 元素本身的破坏性格包裹性，使元素自身失去了流动性无法用于实现自动填满容器的自适应布局。
position：absolute， 脱离文档流严重， 无实现自动的填满容器自适应布局。
overflow：hidden， 其本身是普通元素，块状元素流体性保持完善。
display：inline-block 会让元素尺寸包裹收缩， 同样失去流动性。

两栏自动布局
                        <div class="father"> 
                         <img src="me.jpg"> 
                         <p class="animal">小猫 1，小猫 2，...</p> 
                        </div> 
                        img { float: left; }
                        .animal{
                           overflow: hidden;
                        }
    文字在 BFC 中为了不被浮动元素影响，同时不影响浮动元素， 文字会自动沿着float 元素的右边排列。

即具有 BFC 也保留流的自动适应特性：
    a. overflow: auto/hidden 适应于IE7
    b. display:inline-block  适用于IE6和IE7
    c. display:table-cell    IE8及以上浏览器
```

#### overflow

```css
彻底清除浮动影响的最佳元素。

overflow: hidden,彻底清除浮动， 本质上是利用 overflow元素的 BFC 特需特性。

overflow：hidden 的本职工作是剪裁。当声明 overflow 的元素具备 padding 和 border， 子元素超出范围， 剪裁到border box 内边界进行。

overflow-x: visible（默认） | hidden | scroll | auto

overflow-y: visible（默认） | hidden | scroll | auto

如果 overflow-x 和 overflow-y 属性中的一个值设置为 visible 而另
外一个设置为 scroll、auto 或 hidden，则 visible 的样式表现会如同 auto。


overflow 与 滚动条：
   a.IE7 浏览器 html 标签 和 body 标签 默认有滚动条
   b.IE8 浏览器 html 标签 和 body 标签 默认是 auto
     有如下规则： 在 PC 端，无论是什么浏览器，默认滚动条均来自<html>，而不是<body>标签。
      去除页面默认滚动条使用： overflow：hidden
   c. 滚动条会占用容器的可用宽度或高度, IE7 及以上版本 IE、Chrome、   
      Firefox浏览器滚动栏所占据的宽度均是17px.
 
滚动条的宽度产生的糟糕效果：
      1. float 布局若宽度定死， 产生滚动条后会发生错位。
      2. 滚动栏占据宽度的特性最大的问题就是页面加载的时候水平居中的布局可能 
         会产生晃动，因为窗体默认是没有滚动条的，而 HTML 内容是自上而下加 
         载的，就会发生一开始没有滚动条，后来突然出现滚动条的情况，此时页面 
         的可用宽度发生变化，水平居中重新计算，导致页面发生晃动。
    简单的做法是：
                html { 
                   overflow-y: scroll; 
                  }
    第二种做法：
                html { 
                 overflow-y: scroll; /* for IE8 */ 
                } 
                :root { 
                 overflow-y: auto; 
                 overflow-x: hidden; 
                } 
                :root body { 
                 position: absolute; 
                } 
                body { 
                 width: 100vw; 
                 overflow: hidden; 
                }
  
  
依赖overflow的样式： 该样式的成立需要依赖 overflow 的声明
    单行文字溢出打点显示：
                 .ell { 
                     text-overflow: ellipsis; 
                     white-space: nowrap; 
                     overflow: hidden; 
                  }
    上述三条声明缺一不可
    

overflow 与锚点定位
      a. <a href="#1">发展历程></a>    利用 href 属性和 name 属性
         <a name="1"></a>
      b. <a href="#1">发展历程></a> 
         <h2 id="1">发展历程</h2>      利用 href 属性和 id 属性
         
 两种触发锚点定位行为的发生：
  （1）URL 地址中的锚链与锚点元素对应并有交互行为；
  （2）可 focus 的锚点元素处于 focus 状态。
   (3) 锚链值是非隐藏状态。
   (4) 链接中会加入 #xxx ,可通过 location.hash 自动获取。
   (5) 只发生在有滚动条的页面中
               
   <a href="#">返回顶部></a>
   
   “focus 锚点定位”指的是类似链接或者按钮、输入框等可以被 focus 的元素在被 focus时发生的页面重定位现象。
   
 focus 和 url 定位的差异：
    “URL 地址锚链定位”是让元素定位在浏览器窗体的上边缘，而“focus 锚点定位”是让元素在浏览器窗体范围内显示即可，不一定是在上边缘。
    
  锚点定位作用的本质：锚点定位本质上是改变了 scrollTop 或scrollLeft 值
  
    a. 改变[容器]的滚动高度和滚动宽度实现，定位行为是由内而外。  (是容器并非是浏览器)
    b. “由内而外”指的是，普通元素和窗体同时可滚动的时候，会由内而外触发所有可滚动窗体的锚点定位行为. 容器元素 - 浏览器
    c. overflow:hidden 也可以触发滚动条高度变化， 即没有滚动条但是可以
       发生锚点定位。    利用 c 可以实现 选项卡切换。
             <div class="box">                   // 锚点
             <div class="list" id="one">1</div> 
             <div class="list" id="two">2</div> 
             <div class="list" id="three">3</div> 
             <div class="list" id="four">4</div> 
            </div> 
            <div class="link">                  // 锚链
             <a href="#one">1</a> 
             <a href="#two">2</a> 
             <a href="#three">3</a> 
             <a href="#four">4</a> 
            </div> 
            .box { 
             height: 10em; 
             border: 1px solid #ddd; 
             overflow: hidden; 
            } 
            .list { 
             line-height: 10em; 
             background: #ddd; 
            } 
      缺点1：  容器需要实现固定高度
      缺点2：  “由内而外”导致浏览器也会跟着发生震动

针对缺点2： 利用 focus 
         <div class="box"> 
         <div class="list"><input id="one">1</div> 
         <div class="list"><input id="two">2</div> 
         <div class="list"><input id="three">3</div> 
         <div class="list"><input id="four">4</div> 
        </div> 
        <div class="link"> 
         <label class="click" for="one">1</label> 
         <label class="click" for="two">2</label> 
         <label class="click" for="three">3</label> 
         <label class="click" for="four">4</label> 
        </div> 
        .box { 
         height: 10em; 
         border: 1px solid #ddd; 
         overflow: hidden; 
        } 
        .list { 
         height: 100%; 
         background: #ddd; 
         position: relative; 
        } 
        .list > input { 
         position: absolute; top:0; 
         height: 100%; width: 1px; 
         border:0; padding: 0; margin: 0; 
         clip: rect(0 0 0 0); 
        }
```

#### position:absolute

```css
absolute： 包裹性、 块状性、 破坏性

1. absolute 和 float 同时存在的时候，float属性无任何效果的

2. 元素一旦 position 属性值为 absolute 或 fixed，其display 计算值就是 block 或者 table

3. 
   a. 包含块： 元素用于计算自身宽度和高度的参考块，普通元素的包含块是其父元素的 content box。
   b: 元素的包含块由其 position 定义
     i: 根元素（很多场景下可以看成是<html>）被称为“初始包含块”，其尺寸等同于浏览器可视窗口的大小。
     ii: 如果该元素的 position 是 relative 或者 static，则“包含块”
         由其最近的块容器祖先盒的 content box 边界形成。
     iii:如果元素 position:fixed，则“包含块”是“初始包含块”。
     IV:如果元素 position:absolute，则“包含块”由最近的 position 不为 static的祖先元素建立，边界是 padding box 具体方式如下:     (position 的包含块有可能是一个内联元素)
       (1) 假设给内联元素的前后各生成一个宽度为 0 的内联盒子（inline box），则这两个内联盒子的 padding box 外面的包围盒就是内联元素的“包含块”；
       (2) 如果该内联元素被跨行分割了，那么“包含块”是未定义的，也就是 CSS2.1规范并没有明确定义，浏览器自行发挥。
       否则，“包含块”由该祖先的 padding box 内边界形成。
           
     V：如果没有符合条件的祖先元素，则“包含块”是“初始包含块”。
    
     内联元素的“包含块”是由“生成的”前后内联盒子决定的，与里面的内联盒子细节没有任何关系。
 
绝对定位元素设置 height:100% &  height:inheriet 是不同的， height:100% 是相对于最近的定位祖先元素
height:inherit 是纯粹的祖先元素。

4. 绝对定位元素的包裹性是相对于包含块来表现的。
     .container { 
         width: 200px; 
         border: 1px solid; 
         position: relative; 
        } 
     .box { position: absolute; }
   a. box 的最大宽度默认为其父元素宽度， 文字超过了会发生换行。这是包裹性带来的宽度自适应性。
   b. .container 高度塌陷是因为 absolute 破坏了正常的 CSS 流，此乃“破坏性”
 
5. 为何绝对定位的定位要相对于 padding box 呢？
   a. 与 padding box 解耦， 当在边框右上角放上小的图标， 改变 padding 值不会使图标发生移动， 而若基于 content box 定位改变 paddong 图标下移
。

6. 具有相对特性的无依赖 absolute 定位
   a. 当元素 position：absolute 时， 元素是相对定位，即当前位置是其position: static 位置。(在不设置top/left/right/bottom)下
      注意：  这是css初始化 absolute 规则，即当父元素没有声明 relative
时， 子元素仅仅是一个 absolute top的初始值是： 浏览器下编缘长度 至 父元素padding下边缘长度，行为表现跟相对定位一样。 当父元素设置 relative 此时 top初始化为 padding box 的长度。  

   b. 不占据 css 尺寸空间， 即后面跟着内联元素会与其重叠。

7 absolute 与 text-align
  a. text-align 只对内联元素起作用。

  b. 父元素设置 text-align 可以对子元素是内联元素position:absolute
     产生效果， 因为其本质上是对前面的幽灵空白符号产生作用。 此时子元素
     设置 margin-left:-50% 即可完成居中效果

8 absoliut 与 overflow
  a.  如果 overflow 不是定位元素，同时绝对定位元素和 overflow 容器之间也没有定位元素，则 overflow 无法对 absolute 元素进行剪裁。 
  b.  a 原则下overflow 元素父级是定位元素也不会剪裁 。
  c.  如果 overflow 元素和绝对定位元素之间有定位元素，会被剪裁.即将绝对定位元素限制在了overflow 所在的区域中。
  d. 如果 overflow 的属性值不是 hidden 而是 auto 或者 scroll，即使绝对定位元素高宽比 overflow 元素高宽还要大，也都不会出现滚动条。
      当绝对定位和非绝对定位混合在一起时特殊现象：即当容器滚动的时候，绝对定位元素纹丝不动，不跟着滚动，表现类似 fixed 固定定位。  该特性可应用于文字的背景图片。
   e. 由于 position:fixed 固定定位元素的包含块是根元素，因此，除非是窗体滚动，否则上面讨论的所有 overflow 剪裁规则对固定定位都不适用。

  e. css3 世界带来某些规则的改变， transform 属性有不完全的定位属性
     i overflow 元素自身 transform：
       • IE9 及以上版本浏览器、            
       • Firefox 和 Safari（OS X、iOS）剪裁；
       • Chrome 和 Opera 不剪裁。
  
    ii. overflow 子元素 transform： 
        •  IE9 及以上版本浏览器、     
        •  Firefox 和 Safari（OS X、iOS）剪裁；
        •  Chrome 和 Opera 剪裁。
  

9. absolute 与 clip
   前言：CSS 世界有些属性或者特性必须和其他属性一起使用在有效。 clip 是裁剪属性. clip 是专门实现脱离文档流的剪裁。
   a. clip 属性要想起作用，元素必须是绝对定位或者固定定位.
   b. clip: rect(top right bottom left)
   c. 两种场景 clip 的不可替代性：
      i. fixed 固定定位的剪裁。 overflow 无法进行裁剪。

      ii. 最佳可访问性： 肉眼看不见，但是其他辅助设备却能够进行识别
和访问的隐藏。
    e.g: 很多网站左上角都有包含自己网站名称的标识（logo），而这些标识一般都是图片，为了更好地 SEO 以及无障碍识别，我们一般会使用<h1>标签写上网站的名称。
        下策：display:none 或者 visibility:hidden 隐藏屏幕阅读 
             设备会忽略这里的文字。
        中策：text-indent 缩进是中策，但文字如果缩进过大，大到屏幕之
             外，屏幕阅读设备也是不会读取的。
        上策： color:transparent 是移动端上策，但却是桌面端中策，因为原生 IE8 浏览器并不支持它。color:transparent 声明，很难用简单的方式阻止文本被框选
        最佳隐藏策略：clip 剪裁隐藏既满足视觉上的隐藏，屏幕阅读设备等辅助设备也支持得很好。
                    .clip { 
                         position: absolute; 
                         clip: rect(0 0 0 0); 
                     }
  clip 隐藏仅仅是决定了哪部分是可见的，非可见部分无法响应点击事件
等；然后，虽然视觉上隐藏，但是元素的尺寸依然是原本的尺寸，在 IE 浏览器和 Firefox 浏览器下抹掉了不可见区域尺寸对布局的影响，Chrome 浏览器却保留了。
     
10 absolute 的流体特性
    a. 仅仅设置一个方向： 元素的另外方向的流体特性依然保留。
    b. 若同时声明 left=0 和 right=0 则 absolute 发生流体特性会自动格式化上下文。此时子元素宽度 = 父元素 padding box 宽度 + content box 宽度。

11 absolut 和 margin：auto
   a. 绝对定位元素的 margin:auto 的填充规则和普通流体元素的一模一样
    • 如果一侧定值，一侧 auto，auto 为剩余空间大小；
    • 如果两侧均是 auto，则平分剩余空间。
    实现垂直居中：
      .element { 
             width: 300px; height: 200px; 
             position: absolute; 
             left: 0; right: 0; top: 0; bottom: 0; 
             margin: auto; 
        }
```

#### position:relative

```
1. relative定位特性:
    a.相对自身：
    
    b. 无侵入： 自身发生移动不会影响上下左右的元素， 原本的位置空间依然
               保留。
    
  相对自身定位： 
  
2. relative 的百分比值是相对于包含块来算的，具体如下：
     a. top / bottom 垂直方向的百分比是按照包含块的高度 height
        若是 auto 则计算无效 计算值为0。
     b. top/bottom 同时使用时 bottom 无效
        left/right 同时使用时 left 无效
        
3. relative 最小化原则
     a. 尽量不使用 relative，如果想定位某些元素，看看能否使用“无依赖的
        绝对定位”；
     b. 如果场景受限，一定要使用 relative，则该 relative 务必最小 
        化。  最小化指的是包含的子元素最小， 因为子元素的父元素 relative 则其层
        叠等级变高。
```

#### position:fixed

```

```

#### CSS 层叠规则

```css
名词：  
   层叠水平： 同一个层叠上下文中元素的显示顺序  
   层叠顺序： 规则， 元素发生层叠时特定的垂直显示顺序  
   层叠上下文： 类似于 BFC 层叠上下文的元素比普通元素层叠水平高。

层叠规则： 当网页上元素发生重叠的时候的表现规则

1. z-index : z 轴顺序， 只有和定位元素在一起时才有作用，可以是正数也可以是负数
             数值越大等级越高。

2. stacking context： 层叠上下文， 如果一个元素含有层叠上下文，我们可以理解为这个元素在 z 轴上就“高人一等。 

3. stacking level： 层叠水平， 其指的是同一层叠上下文中的元素 z 轴上的显示顺序。  stacking level 水平和和 z-index 不同， z-index 觉得定位元素的层级水平。 层叠水平指的是在一个层叠上下文中所有元素 z轴的顺序。


4. 层叠规则：  装饰  -->  布局 ---> 内容
    
      a. 具体如下： background --> 负z-index --> block块状水平盒子
                  float浮动盒子 --> incline水平盒子 --> z-index：auto/0
                  正z-index
   CSS 世界是为更好的图文展示而设计的，因此，一定要让内容的层叠顺序相当高，这样当发生层叠时，重要的文字、图片内容才可以优先显示在屏幕上。
   定位元素一旦被声明， 其z-index:auto, 自动生效，因此层级在普通元素之上。
 
5 两条层叠规则：
     a. 谁大谁上：当具有明显的层叠水平标识的时候，如生效的 z-index 属性值，在同一个层叠上下文领域，层叠水平值大的那一个覆盖小的那一个。
     b. 后来居上：当元素的层叠水平一致、层叠顺序相同的时候，在 DOM 流中处于后面的
元素会覆盖前面的元素
   
6. 层叠上下文元素有如下特性：
     a. 层叠上下文的层叠水平要比普通元素高
     b. 层叠上下文可以阻断元素的混合模式
     c. 层叠上下文可以嵌套，内部层叠上下文及其所有子元素均受制于外部的“层叠上下
        文”。
     d. 每个层叠上下文和兄弟元素独立，也就是说，当进行层叠变化或渲染的时候，只需要
        考虑后代元素。相邻元素层叠变化不相互影响。
     e. 每个层叠上下文是自成体系的，当元素发生层叠的时候，整个元素被认为是在父层叠
        上下文的层叠顺序中。子元素继承父元素的层叠顺序。
   

7. 层叠上下文的创建：  不是所有元素都可以创建层叠上下文
    a. 天生派： 页面根元素天生具有层叠上下文
    b. 正统派： z-index 值为数值 0| 正数 |负数 的定位元素
    c. 扩招派： CSS3 带来的属性

对于 position:fixed  的元素不需要 z-index 会自动生成层叠上下文

  根元素构建了一个层叠上下文，包含了所有子元素。

  层叠上下文类似于块级格式化上下文， 也是指明在某一个区域上元素的层叠水平， 相邻层叠上下文中的元素的层叠水平的比较是父元素层叠水平比较结果， 若两者相同则按照后来居上原则。 

   对于 position 值为 relative/absolute 以及 Firefox/IE 浏览器（不包括 Chrome 浏览器）下含有 position:fixed 声明的定位元素，当其 z-index 值不是 auto 的时候，会创建层叠上下文。 chrome 浏览器 的 position:fixed 自带层叠上下文。

1. 如果层叠上下文元素不依赖 z-index 数值，则其层叠顺序是 z-index:auto，可看成 z:index:0 级别；  
2. 如果依赖 z-index 数值， 则层叠顺序由 z-index 值决定。

8. CSS3 与 新时代层叠上下文

（1）元素为 flex 布局元素（父元素 display:flex|inline-flex），同时 z-index
值不是 auto。 
（2）元素的 opacity 值不是 1。 
（3）元素的 transform 值不是 none。 
（4）元素的 mix-blend-mode 值不是 normal。 
（5）元素的 filter 值不是 none。 
（6）元素的 isolation 值是 isolate。 
（7）元素的 will-change 属性值为上面 2～6 的任意一个（如 will-change:opacity、
    will-chang:transform 等）。
（8）元素的-webkit-overflow-scrolling 设为 touch。

9. 深入理解 z-index 负值
  z-index 负值渲染的过程就是一个寻找第一个层叠上下文元素的过程，然后层叠顺序止步于这个层叠上下文元素。

10 z-index 值不超过2
```



 ### 常用CSS属性

```css
white-space:

line-height:

vertical-align

text-align:

animation
@keyframes

clip：

bcakground-clip： 

word-break: break-all;   // 连续英文字符换行

```

### CSS选择器

```javascript
A  B  C  D

1. 内联选择器设 A：1
2. Id 选择器设 B：1
3. 类选择器，属性选择器，伪类选择器 C：1
4. 元素选择器 ，伪元素选择器 D：1

!important 优先级最高
.app {
	color: 0f0 !important;
}
max-width 可以超越 width !important 
```

### 水平垂直居中方案

```
1. Flex 方案
2. Grid 方案
3. absolute + transform
4. absolute + calc
5. absolute + 负 margin
6. absolute + margin: auto
7. writing-mode
```



### CSS注意事项

```css
1. 即 Chrome 浏览器下，如果容器可滚动（假设是垂直滚动），则 padding-bottom 也算在滚动尺寸之内，IE 和 Firefox 浏览器
忽略 padding-bottom。

2.  <a href="javascript:" class="icon-delete tips" data-title="删除">删除</a>
     .tips[data-title] {
        position: relative;
     }
    .tips[data-title]::before,
    .tips[data-title]::after {
      position: absolute;
      left: 50%;
      transform: translateX(-50%);
      visibility: hidden; 
    }
    .tips[data-title]::before {
      content: attr(data-title);
      top: -33px;
      padding: 2px 10px 3px;
      line-height: 18px;
      border-radius: 2px;
      background-color: #333;
      text-align: left;
      color: #fff;
      font-size: 12px;
    }
    .tips[data-title]::after {
      content: "";
      border: 6px solid transparent;
      border-top-color: #333;
      top: -10px;
    }
    .tips[data-title]:hover::before,
    .tips[data-title]:hover::after {
      transition: visibility .1s .1s;
      visibility: visible;
    }

    .icon-delete {
      display: inline-block;
      width: 20px; height: 20px;
     // background: url(/images/6/delete.png) no-repeat center;
      background-size: 16px;
    }
这段代码实现;   删除[链接] 点击删除显示黑色指示框 黑色指示框包含文字删除
              黑色指示框利用::before 生成  下三角使用 ::after实现
              精确定位将::before，::after定位方式修改： absulte
              .tips[data-title] 为positive 定位
初始生成：  矩形框+文字  删除  三角框     这三个都在<a> </a> 标签中
           ::befor :: after {position:absolute
                             left:50%     两矩形挪到一起
                             transition: transformX(-50%)
                                          第一个矩形框移动自身宽度一
                                          半， 使得小矩形在其中间
                             visibility：hidden  隐藏
                             }
```


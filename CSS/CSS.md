

### 特性

```css
CSS 本身注重的是特性间的【相互联系】和【具象】能力， 对于逻辑要求较低。

【属性】 CSS 是魔法师， 【标签】即 HTML 是魔法石. 【操作系统】是它们所在的世界。【平行世界】： Windows世界、OSX 世界，移动端的 ios 世界 和
Andriod 世界。

注： windows 世界中 IE区域活跃， Safari地区较为落寞
      OSX 世界中， IE区域不存在， Safari是最活跃的地区

《CSS 世界》 中规定
     元素尺寸： border box尺寸      原生的DOM API写作： offsetHeight/offsetWidth
     元素内部尺寸： padding box尺寸  原生的DOM API写作： clientWidth/clientHeight
     元素外部尺寸： margin box尺寸   没有相应的DOM API 
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
     1. 充分利用可用空间： 在<div>、 <p> 元素下宽度默认是100%   [fill-avaliable]
     2. 收缩与包裹： 元素设置为浮动、 绝对定位、 inline-block 元素或者 table 元素
                   自动将元素宽度收缩为合适                  [shrink-to-fit]
     3. 收缩到最小: table-layout:auto, 表格的列元素设置成宽度最小
                                                        [min-content]
     4. 超出容器限制: 内联元素设置成 wihte-space:nowrap.
     
尺寸：
     1. Instrinsic Sizing： 内部尺寸， 元素尺寸由内部元素决定，并非外部的容器
     2. Extrinsic Sizing：  外部尺寸

外部尺寸与流：
   上述的四种宽度表现，第一种 [fill-avaliable] 下的尺寸是外部表现， 具体是 <div> 元素标签放入到水平流中时自动铺满整个水平流。

格式化宽度： 格式化宽度仅出现在 '绝对定位模型' 中， position: absolute / fixed 元素中。 默认情况下， 绝对定位元素的宽度表现是包裹性的， 宽度由内部尺寸决定。 但是， 当left/right ,或者 top/bottom 同时出现时[其宽度大小相对于最近的父元素，其position 属性值不为 static ]

内部尺寸与流：
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
         9. 单边框属性设置: border-left、 border-right、 border-top、 border-
            bottom
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

```
文字、 图片、 按钮、 表单控件都是内联元素

内联元素的外在盒子都是内联盒子。  并且内联元素中的内联指的是外在盒子， 与display：inline
是不同的。 内联元素的 display的默认值都为incline

内联盒模型
     <p> where is the goal ,where I will go </ p>
      1                  2
1. 内容区域: 元素自身，即文本中的背景色区域    2
2. 内联盒子：元素的外在盒子与其并列的块级盒子，其决定不让元素按块布局而是排成一行 2
3. 行框盒子： 每一行都是一个行框盒子， 每行上的一个有一个内联盒子组成了行框盒子  2
4. 包含盒子：<p>标签就是一个包含盒子， 此盒子由一行一行的行框盒子组成。        1

幽灵空白节点：HTML5 的所有内联元素的解析和渲染表现的像其之前有一个空白节点。
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
            chrome 浏览器下 缺少 src 和 alt="" 同样会发生上述变换
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
            4.1 深入理解 content 59
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

2. padding的作用： 利用层叠效果我们可以增加按钮的区域

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

​           

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

```


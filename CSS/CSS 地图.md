### CSS 基础

```
1.  HTML 世界中的 CSS
  a. HTML 中任何内容都是一种内容都是一种节点， 在HTML中显示的是三种节点：
                   文本节点、 注释节点、 元素标签节点
     CSS 通过 [盒模型] 施加对三种节点添加样式： 位置布局， 内容显示
     [位置布局]： 页面生成后， 标签在页面中的位置显示
     [内容显示]： 页面生成后， 标签中的内容
     
  b. HTML 元素在 CSS 眼中都是盒子， 盒子的结构是：margin、 border、 padding、 content，
     
     I. 由于 display: incline-block 属性， 因此每个元素其是两层盒子， 外面的盒子被称作
        外在盒子，两种类型： 块级盒子 和 内联盒子。
        
     II. 文字又被称为匿名内联元素， 内联元素除了拥有与块级盒相同的盒子结构，其还定义如下盒子： 
         em框： 字符大小 
         内容区：相连的 em 框组成内容区， 内容区 = 背景颜色
          行框： 每一行就是一个行框盒子， 行框盒子是由一个个 em 框组成的  
         包含盒子： 由一行行的行框盒子组成。
         
     III. 内联元素的行框盒子之前都有一个空白的幽灵节点，宽度为 0， 其继承元素的子体大小和
          行高属性。
     
2. HTML 中的环境
     a. HTML 中高度是无限的， 宽度是有限的， 元素自上而下，自左向右摆放， 默认的水平流
        方向自左向右。
     
     b. 流：
          块级元素： 水平流上只显示一个，该元素自动铺满整行，当前行的流成为该块级元素的内流
                   又成为 [内河]， 在内河中可再次放置：块级元素、内联级元素。
          内联元素： 内联元素文字和图片都有默认的宽度， 其他内联元素宽度是 auto ，他们
                   摆放时都是被流引导自动摆放。
           流动性： 元素的 margin/border/padding/width 自动适配。 
                  当我们不主动设置内河中子元素宽度， 则其会自动适应其它元素宽度的改变，这种
                  就称为利用流体进行自动布局。
                  
           鑫三无准则的一条： 无宽度， 不规定元素宽度，是元素使用流完成自动布局。
         
     c. BFC: 块级格式化上下文， 当添加特定属性后， 父类标签会成为块级格式化上下文
        里面元素独立于外面元素， 不相互影响。
        I. 形成 BFC 的条件
           float： 不为 none
           position： 不为 relative 和 static
           overflow： auto/hidden/scroll
           display: table-cell、table-caption 和 inline-block 中的任何一个。
        
        II. BFC 与 流
           overflow： hidden； 即使得父级元素内部是块级格式化上下文，又完好的保留了流的特性。
            display：inline-block 会让元素尺寸包裹收缩， 同样失去流动性。
           利用BFC 与 流实现自动化布局：  结合 float 元素实现一个两栏自动布局      
           <div class="father"> 
           <img src="me.jpg"> 
           <p class="animal">小猫 1，小猫 2，...</p> 
           </div> 
           img { float: left; }
           .animal{
           overflow: hidden;
           }
           
       III. 利用 BFC 实现清除浮动、 实现取消相邻 margin 元素合并。
          清除合并：
                 <div class='bro1'></div>
                 <div class='bro2'></div>
                 .bro1{
                      overflow:hidden;
                  }
          清除浮动引起的高度塌陷: float 会破坏内河，加入 BFC 将其包含其中，静止了它对外部的破坏。
              <div>
                <div class='clear'>
                 <img src='xxx.jpg'>
                </div>
                 <div>wo</div>
                 .clear{
                    overflow:hidden;
                 }
              </div>

3. CSS 中的层叠：
     a. 层叠上下文： 类似于 BFC 可以使某种元素具备层叠上下文， 若元素具备层叠上下文
                   后，该元素的层叠等级比普通元素高.
     
     b. 层叠水平：同一个层叠上下文中的显示顺序。
     
     c. 层叠顺序：所有元素发生层叠时的显示顺序
     
         I. 层叠上下文的 background/border -> 负的 z-index
            -> block 块状盒子 -> float 浮动盒子 -> inline水平盒子
            -> z-index:auto/z-index=0/不依赖z-index层叠上下文元素-> 正数的 z-index 盒子
            
         II. inline水平盒子包括： incline 、 inline-block、 inline-table
         
         III. position: relative/absolute/   z-index：auto
              当 z-index=0 即为数值才会创建层叠上下文， 在 chrome 浏览器
              中 position: fixed 会自动创建层叠上下文。
         
         IV. z-index 负值渲染是寻找第一个层叠上下文，然后层叠顺序止步于其之上，
             若元素前面无层叠上下文元素，其止步于 html 之上，视觉上看，其在所有
             元素之下。
             
     d. 层叠上下文的特性：
         I.  层叠上下文的水平比普通元素高
         II. 层叠上下文可以发生嵌套， 内部可以存在层叠上下文，但是受制于父级
             的层叠上下文。
        III. 每个层叠上下文与兄弟元素独立。
        
    e. 层叠关系的两条准则：
         I.  谁大谁在上面
         II. 后来者居上， 即兄弟层叠顺序相同， 后来者居上。
    
    f. 创建层叠上下文
         I.  html 元素会创建层叠上下文
         II. z-inde 为数值的 定位元素， 不包括 position:static
         III. flex 元素， 且 z-index 为数值
         IV. transform 值不为 none
          V. opacity 值不为1
          VI.will-change: transform, opacity, filter
          VII. filter 不为 none。
    问题： 不依靠将一个元素声明为 position:absolut, 如何使得上下两个元素重叠

4. 选择器优先级：
     ！imporant                    10000
     内联 <xx style= "">           01000
     id 选择器                      00100
     类选择器/:伪类选择器/属性选择器[]  00010
     元素选择器/::伪元素选择器         00001
     
     !important 优先级最高
        .app {
            color: 0f0 !important;
        }
        
    关系选择器： 空格、 >、 ~、 +
        后代选择器： 选择所有合乎规则的后代元素。 空格连接
        相邻后代选择器： 仅仅选择合乎规则的儿子元素， 孙子、重孙忽略。 > 连接
        兄弟选择器： 选择当前元素后面的所有符合规则兄弟元素。 ~连接
        相邻兄弟选择器： 仅仅选择当前元素相邻的那个合乎规则的兄弟元素。+连接 IE7以上
     
 5. 隐藏元素：
      1. display: none  元素的宽度和高度丢失
      2. visiablity： hidden 元素的宽度和高度未丢失，但是不可操作性
      3. opacity:0 完全透明，元素依然可操作。
      
 6. 块级元素 和 内联级元素的 width/height
 
      a. 块级元素的的 width/height 作用在盒子的 content 上
      
      b. 内联级元素： 非替换元素是不可以设置 width/height 的。
      
      c. 块级元素 width:auto 的四种表现： 
               I. fill-available: 充分利用可利用空间，块级元素标签默认的 width
                  设置属于该种特性。 width 默认为当前内河。
              II. shink-to-fit: 紧包性， 元素的宽度由子元素决定。 float、inline-bolck、
                  position:absolute
              III. 最小宽度
              IV. 超出容器限制： 相当于 内联元素设置 white-space:nowrap;

      d. 内联元素的 padding / border 的top/bottom属性,是可操作的，只是与块级
         元素不同的是 padding-top 是往上扩张， 不影响元素位置， 只有加入背景色
         才可以看出来。 boder-top 同理。

包含块： 元素用于计算自身宽度和高度的参考块，普通元素的包含块是其父元素的 content box。

7. position 定位： 对于可以移动位置的元素，我们必须搞清楚其相对于谁移动
     

     a. position:fixed      破坏文档流     display:block;
        I. 元素相当于根元素定位
        
     b. position:absoulte   破坏文档流     display:block;
     
        I. 元素只设置 position:absolute , 此时元素的位置
           由 position:static 时的位置决定， 被称作无依赖的绝对定位。
           若只设置一个方向，另一个方向不设置，依然保留相对特性。
        
        II. absolut 的流体特性： 元素宽度由父元素决定
            当同时设置 left：0 right：0，此时元素宽度 = 父元素 padding box 宽度 + content box 宽
            度。 此时修改父元素的 padding ，子元素也不会移动。
            
        III. 绝对定位元素设置 Height=100% 相当于最近的定位祖先元素， height:inherit, 是相当于纯粹的
            的祖先元素。
            
        IV. 绝对定位元素的 marigin：auto， 具备流体特性， 当两侧都为 marigin:auto, 会发生自动平分
            从而实现居中。 
           
        V.  若父元素是 非static的绝对定位元素， 则 top/left 相当于父元素的 padding定位。
        
     c. position: relative
        I. 元素相当于父元素的 content box 定位。
         . top / bottom 垂直方向的百分比是按照包含块的高度 height
         若是 auto 则计算无效 计算值为0。
         . top/bottom 同时使用时 bottom 无效
         left/right 同时使用时 left 无效
        
        II. 元素移动后，原始位置依然保留, 并且不影响上下左右的元素
        
        III. 父元素为 position:relative 可以用于限定子元素 position:absolute
        
     
```

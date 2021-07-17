### CSS 综述

#### 核心概念

```
1. 层叠
    a.  格式化上下文
    b.  层叠上下文
    c.  层叠水平
    d.  样式层叠
    
2. 继承
    
3. 权重
    a. CSS 选择器权重
    b. 样式来源; 编写者规则、 用户、 用户代理
    
4. 视觉格式化模型: 计算元素转换为盒子的[规则]
      a.  盒子布局跟以下元素相关：
          盒子尺寸
          盒子类型：行内盒子（inline）、行内级盒子（inline-level）、原子行内级盒子（atomic inline-
                  level）和块盒子（block）
          定位方案：         普通流定位、浮动定位或绝对定位
          文档树中的其他元素： 即当前盒子的子元素或兄弟元素
          视窗尺寸与位置
          包含的图片尺寸
          其他外部因素
      b. 视窗：视窗就是浏览器中可视区域。视窗大小指的就是浏览器可视区域的大小
      c. 块级格式化上下文  BFC
      d. 行内格式化上下文  IFC
      F. Flex 格式化上下文
      G. Grid 格式化上下文
      
      额外需获悉的概念：
            a.  块
            b.  包含块
            c.  盒子：
            d.  块级盒子
            e.  行内级盒子
            f.  块盒子
            g.  原子行内级盒子
            h.  行盒
            l.  块容器盒子
            m.  块级元素
            n.  行内级元素
            o.  匿名盒子
4. 盒模型
       a. Content
       b. Padding
       c. Border
       d. Margin
    
5. 布局
       a.  定位布局
       b.  浮动布局
       c.  Flexbox 布局
       d.  Grid, Shapes, 多列布局
6. 样式维护
```

文章：

1. [大漠：CSS学习](https://w3cplus.medium.com/css%E7%8E%B0%E7%8A%B6%E5%92%8C%E5%A6%82%E4%BD%95%E5%AD%A6%E4%B9%A0-1ac786328761)

2. [月影: Flex 布局](https://www.w3cplus.com/blog/tags/157.html)

3. [月影： 图解元素尺寸](https://www.w3cplus.com/css/css-intrinsic-and-extrinsic-sizing.html)

4. [月影：移动端Flex适配方案](https://www.w3cplus.com/mobile/lib-flexible-for-html5-layout.html)

5. [月影：移动端页面适配](https://www.w3cplus.com/css/vw-for-layout.html)

6. [月影：移动端的设计和适配](https://www.w3cplus.com/mobile/mobile-design-and-adapter.html)

7. [月影：安卓折叠屏带来的变化](https://www.w3cplus.com/mobile/mobile-folding.html)

8. [月影: 写 css 的姿势](https://www.w3cplus.com/css/css-evolution.html)

   

#### 新概念 & 趋势 

```
CSS3 新功能：   仅列出每一部分50%以上的使用概率具体见 css3 报告
  a. Media Queries： perfers-reduced-motion、 
                     perfers-color-scheme
  b. 文字排版： 
       i. @font-face
       ii. Line Breaking Properties
      iii. font-display
       IV. font-variant
       
  c. 版面安排：
       i. flexbox
       ii. Grid
       iii. position:sticky
        IV. Multi-Column Layout
       
  d. 形状 & 图形
        i. object-fit
       ii. Filters & Effects
      iii. clip-path
       IV. blend-mode
       V. backdrop-filter
       VI. Masking
       
  e. 动画 & 变形
       i. Animation
       ii. Transitions
      iii. Transforms
       IV. Perspective
       
  f. 互动
       i. pointer-events
       ii. overscroll-behaviour
       
  g. 其它
      i. calc()
      ii. Variables
      iii.Comparison Functions
      IV. will-change
       V. @supports
       
用过哪些 CSS 单位 (排名从上到下)
1. px        99.1%
2.  %        96.1%
3. vh, vw    94.7%
4. em        91.6%
5. rem       91.6%
6. vmin,vmax 39.5%
7. pt        38.1%
8. ch        19.6%
9. cm        <= 10%
10.mm
11.in
12.ex

用过 css 伪元素
1. ::before       99%
2. ::after        99%
3. ::placeholder  71.2%
4. ::selection    43%
5. ::first-letter 41.6%
6. ::first-line   31.2%
7. ::marker       <15%
8. ::backdrop

用过哪些互动的 CSS 选择器：
 1. :hover         99.7%
 2. :focus         99.1%
 3. :active        94.6%
 4. :focus-within  30.8%
 5. :focus-visible
用过哪些与地址相关的 css 选择器：
 1. :link & :visited    91.6%
 2. :target             50.4%
 3. :any-link            7.5%
 4. :local-link
用过哪些结构相关的 CSS 选择器：
 1. :first-child        96.5%
 2. :nth-child()        96%
 3. :last-child         94.3%
 4. :not()              83.7%
 5. :nth-last-child()   74.3%
 6. :nth-of-type()      73.4%
 7. :root               63.7%
 8. :first-of-type      61.7%
 9. :last-of-type       58.2%
 10.:nth-last-of-type() 49.6%
 11.:empty              42.2%
 12.:only-child         33.2%
 13.:is()
 用过哪些与表单有关的选择器：
 1. :checked               92.3%
 2. :enabled & disabled    77.9%
 3. :required & :optional  46.5%
 4. :valid & unvalid       44.3%  
 4. :read-only :read-write 30.5%
 5. :default               23.6%
 6. :placeholder-shown     18.5%
 7. :indeterminate
```

#### CSS  技术

```
1.  预 & 后 处理器: 健壮 CSS 的处理器。
    a. sass     预处理器     92%
    b. PostCss  后处理器     88%
    c. Stylus               41%
    d. less                 39%

2.  CSS框架: 提供预先设置好组件和样式库。
    a. Tailwind CSS         87%
    b. PureCSS              71%
    c. Bulma                61%
    d. Ant Design           60%
    e. Materialize CSS      53%
    f. Tachyons

3.  CSS方法论   编写更简洁 CSS 代码的方式   CSS METHODOLOGIES
    a. Utility-first CSS   83%
    B. bem                 82%
    c. ITCSS               78%
    d. SMACSS              67%
    e. OOCSS               66%

4.  CSS-in-JS: 实现 JavaScript 编写 CSS 代码的库
    a. CSS Modules           87%
    b. Styled Components     82%
    c. Emotion               80%
    d. Styled JSX            68%
    
5. 常用的工具函数库
   a. Stylelint              75%
   b. PurgeCSS               37%
   d. PurifyCSS              12.2%
   
6. 其他工具函数库
   a. Prettier               38.3%
   b. Autoprefixer           22.6%
   c. cssnano                10.3%
   e. Sass
   f. PostCSS
   g. ESLint
   

```



#### 社区 & 博客

```
1. CSS-Tricks   
   a. Link: https://css-tricks.com/
   
2. Dev.to  
   a. Link:https://dev.to/

3. Smashing Magazine   
    a. Link: https://www.smashingmagazine.com/
    
4. Medium
    
5. CSS weekly


state of css      https://stateofcss.com/    CSS年度报告
CSS day           https://cssday.nl/2022     CSS年度会议

```



#### 关注者

```
1. Rachel Andrew     https://rachelandrew.co.uk/  （Her Website with focus on css）
   a. intruduct: Co-founder of Perch CMS and Notist. Member of the CSS Working Group. 
   b. Article: 《Why there is no CSS4 — explaining CSS Levels》
   c.  Link:https://rachelandrew.co.uk/archives/2016/09/13/why-there-is-no-css4-explaining-css-levels/
   
2. Jen Simmons     https://github.com/jensimmons?tab=repositories
  a. intruduct: Member of the CSS Working Group   
  b. https://css-tricks.com/css4/   有关 CSS4 的社区讨论
  
3. Geoff Graham  https://css-tricks.com/author/geoffgraham/
 a. Articlie: https://css-tricks.com/2020-roundup-of-web-research/  
 
4. Max Stoiber   推特

5. Brandon Smith
   a. Article: https://css-tricks.com/css-is-awesome/    （CSS is Awesome）
   
6. Stephanie Eckles 
  a. Style Stage  https://stylestage.dev/styles/
 
7. argyleink 
  a. 《What’s new with CSS?》 https://london-css-2020.netlify.app/

```



#### 规范






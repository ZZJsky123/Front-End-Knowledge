## Canvas

```
1. canvas 是位图 逐像素进行渲染的，适合游戏。
2. 一旦图形被绘制完成，就不会继续得到浏览器关注，如果位置发生变化，整个场景也需要重新绘制。

<canvas width="" height="">        // canvas只能设置width、 height 其实内联置换元素

</canvas>

3. canvas必须用JS来填充
   var canvas = document.getElementById('ID号')     // 首先获取画布
   var ctx = canvas.getContext('2d')              // 获取渲染上下文(画笔) 2DRenderingContext
                    (注：其他可选webgl 创建三维渲染上下文对象）WebGlRenderingContext

4. canvas原生做图只支持矩形，其他复杂图形都需要通过路径生成的方法
5. canvas元素默认被网格所覆盖。通常来说网格中的一个单元相当于canvas元素中的一像素。栅格的起点为左上角（坐标为（0,0））。所有元素的位置都相对于原点来定位。所以图中蓝色方形左上角的坐标为距离左边（X轴）x像素，距离上边（Y轴）y像素（坐标为（x,y））。

6. 三种矩形方法 ctx.fillRect(x,y,width,height)   // 绘制一个填充矩形
              ctx.strokeRect(x,y,width,height) // 绘制一个矩形边框
              ctx.clearRect(x,y,width,height)  // 区域变得完全透明

7. 画线条的方法：
       ctx.beginPath();   // 新建一条路线  (拿起画笔)
       ctx.moveTo(x,y)    // 在画布范围内移动到起始点 (设置起始点)
       ctx.lineTo(x,y)    // 路径经过的中间点 (设置中间点)
   最终状态：ctx.closePath()// 闭合路径   终点会连接上起点
           ctx.stroke()   // 描边
           ctx.fll()      // 填充颜色  path没有闭合fill可以自动闭合
           
   画弧线：
      ctx.beginPath()
      // 画一个以x,y为圆心，startAngle起始角度，endStartAngle终止角度，anticlockwise顺时针和逆时针
      ctx.arc(x,y,r,startAngle,endAngle,anticlockwise)    // 弧度制
      ctx.arcTo(x1,x2,y1,y2,radius) // 给定两个控制点，半径画弧 即通过两条切线画圆
8. 添加样式和曲线
   ctx.fillstyle =  //添加颜色
   ctx.strokeStyle  // 轮廓颜色
   ctx.lineWidth    // 默认为1 不能为0 线宽是线的终点上下各区一半
   ctx.lineCap      // 'butt' 'round' 'squre' 线段末端以方形结束，圆形结束 方形结束且绘制一个矩阵
   ctx.lineJoin = 'round(圆形)/bevel(三角形)/miter(默认)'




       
```



## SVG

```
1. svg 是矢量图 (scalabale Vector Graphics)
2. svg 是使用xml描述的2D图形语言
3. svg 适合做地图(google/baidu)，缩放不影响显示
4. svg 中每个被绘制的图形都会被视为对象，对象属性发生变化，浏览器会自动重现图形

```


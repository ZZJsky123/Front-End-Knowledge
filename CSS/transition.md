## transition

```
定义： 过度，变迁
transition：property duration function delay  
    property字段： none all 特定属性名称
    duration: 过度时间，期间不可被停止
    function：变化方式 linear ease(对数) ease-in(加速) ease-out
    
2. transition需要事件触发没有办法加载时自动引入
3. 一个transition只针对1个人属性
4. transition包含两个状态：起始，终点，无中间结果
```

## transform

```
transform：  rotate(xdeg)           // 必须是以deg结尾的角度值  元素顺时针旋转角度
             translate(x,y)        //  以元素中心点为基点移动
             translate3D(x,y,z)
             scale(x,y)            // 缩小倍数 scaleX(a) scaleY(b)
             skew(x,y)             // 倾斜，逆时针围绕x轴旋转x度 ，围绕y轴旋转y度
                                      skewX，skewY
             
```

## animation

```
animation: name duration timing-function delay fill-mode dircection

animation-fill-mode: none/backwards/forwardesboth    none:默认值回到动画未开始状态
                                                     backwards：动画回到第一帧
                                                     forwards：动画停留在结束的状态
                

@keyframes name{
       from {属性：value1}
       50%  {属性：value}
       to  {属性：value}
}
```


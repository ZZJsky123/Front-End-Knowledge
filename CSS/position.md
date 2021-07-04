## position

```
1.position 属性决定了元素位置的定位方式

2. position: static(默认)
             relative: 元素在正常文档流中，相对于static定位
             absolute: 元素不在正常文档流，相对于最近的非static父元素的margin定位，无则相对于根元素html定位
             fixed：    元素不在正常文档流， 相对于视口(浏览器窗口)定位，因此不随滚动条移动
             sticky： relative+fixed 定位
3. 元素定义position后 可配套使用top bottom left right
4. sticky生效的前提是，必须搭配top、bottom、left、right这四个属性一起使用，不能省略，否则等同于relative定位，不产生"动态固定"的效果。原因是这四个属性用来定义"偏移距离"，浏览器把它当作sticky的生效门槛
```


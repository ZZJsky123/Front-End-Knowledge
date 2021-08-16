## DOM 获取节点的方式

```
1. 通过ID获取：  document.getElementById('id')
2. 通过name属性：document.getElementsByName('name')
3. 通过标签名：   document.getElementsByTagName('p')
4. 通过类名：     document.getElementsByClassName('class')
5. 获取html的方法：document.documentElement
6. 获取body的方法：document.body
7. 通过选择器获取一个元素：document.querySelector('选择器的名字')   %% 输入的字符串必须是CSS中的选择 
器
8. 通过选择获取一组元素：document.querySelectorAll
```

### Boswer 对象

1. window 对象

```
window 对应的具体实物是浏览器窗口

```

2. Navigator 对象

```
Navigator 对应的具体实物是浏览器信息
```

3. Screen 对象

   screen 对象包含有关客户端显示屏幕的信息。

   属性：

       1. availHeight:   返回屏幕的高度（不包括Windows任务栏）
          2. availWidth:   返回屏幕的宽度（不包括Windows任务栏）
          3. colorDepth： 
          4. height:          返回屏幕的总高度
          5. pixelDepth：    颜色分辨率
          6. width：         返回屏幕的总宽度

4. History 对象

   History 对象是 window 对象的一部分，可通过 window.history 属性对其进行访问。

   History 对象包含用户（在浏览器窗口中）访问过的 URL信息

   属性： 

   ​      a. length        : 返回历史列表中的网址数

   方法：

   ​     a. back()   :      加载 history 列表中的前一个 URL

   ​     b. forward()  :   加载 history 列表中的下一个 URL

   ​     c. go(number | URL):   加载 history 列表中的某个具体页面, 其中number 可正可负。

   

5. Location 对象

​      Location 对象是 window 对象的一部分，可通过 window.Location 属性对其进行访问。

​      Location 对象包含了有关当前 URL 的信息：  如下属性

​              a. hash        :返回一个 URL 的锚部  

​              b. host         : 返回一个URL的主机名和端口 www.runoob.com

​              c.  hostname： 返回URL的主机名 www.runoob.com

​              d. href            ： 返回完整的URL https://www.runoob.com/jsref/obj-location.html

​              e. pathname：  url 的路径名  /jsref/obj-location.html

​              f.  port：   端口号  

​              g. protocol： 协议    https

​     方法： 

​              a.  assign()    载入一个新文档

​              b.  replace()  用新的文档取代当前文档

​              c.   reload()   重新加载文档

6. 存储对象
   1. window.localStorage：  在浏览器中存储 key/value 对。没有过期时间。

​         2. window.sessionStorage： 在浏览器中存储 key/value 对。 在关闭窗口或标签页之后将会删除这些数据。

​       方法： 

​              a. key(n) :  第n个键的名称

​              b. getItem(keyname)  : 返回指定键的值

​              c. setItem(keyname, value) : 添加键和值，如果对应的值存在，则更新该键对应的值。

​               d. clear()

​                f. remvoeItem(key)   ： 移除键

## JS基础特性

> ECMAScript 中的一切(变量、函数名和操作符)都区分大小写。
>
> ​    1、 标识符的第一个字母必须以一个字母、下划线_或者一个美元符号$开始
>
> ​    2、ECMAScript标识符采用驼峰大小写格式，第一个字母小写。剩下的每个有意义的单词首字母大写
>
> 标识符： 属性，变量，函数名，函数的参数

**严格模式**

> 两种添加方式：
>
> 1.   在程序顶头添加：  'use strict'
> 2.   在函数内部第一行添加:  'use strict'
>
> 支持严格模式的浏览器：
>
> ​    IE 10+ 、 Firefox 4+、Safari 5.1+、Opera12+、Chrome

**语句**

> ECMAScript 中的语句以一个分号结尾，省略分号，则由解析器确定语句的结尾

**变量**

> ECMAScript的变量是松散类型的，即可以用来保存任何类型的数据

**数据类型**

> ```javascript
> ECMAScript有5种简单数据类型(基本数据类型): undefined、null、string、boolean、number
> 
> 一种复杂的基本类型： object
> 
> typeof 可用于检测
>        undefined、string、boolean、number、function  
> instanceOf用于区分null、Object
>        null instanceOf Object             \\ false
> undefined值从null中派生，undefined == null   \\ true
>        
> 【null】: 空的对象引用，未定义的对象都可先赋值为null
> 
> ```
>
> ```javascript
> 【Boolean】
>  1. Boolean的字面值是：true、false,不可大写。
>  2. ''、0、[]、null、NaN、undefined 逻辑都为false
>  3. 除【2】外，其他变量值直接做逻辑判断为true
> ```
>
> ```javascript
> 【Number】
>  1. javascript 的整型和浮点型都统一用Number类型表示
>  2. 不要测试某个特定的浮点数： 0.1+0.2 !== 0.3   //   0.30000000000004
>  3.Number.MIN_VALUE储存最小值、Number.MAX_VALUE存储最大值
>  4. 超出范围会返回 [-infinity infinity],两个值不可用于计算，可用isFinite(num)检测是否超出范围 // 返回true和false
>  5. 非数值，用NaN代替抛出错误，与NaN有关的计算结果都是NaN，NaN不与任何数据类型相同包括其本身，使用isNaN（）函数进行判断。
>  6. 数值转换： Number()函数、parseInt()函数、parseFloat()函数
>     Number(value):  undefined -> NaN
>                       boolean -> 0/1
>                        number -> 十进制
>                     string: 包含数字以外的字符 -> NaN
>                                   字符串为空  -> 0
>                                '0123'/'123' -> 123/123
>                                十六进制/八进制 -> 十进制
>                     Object:  valueOf() ->若返回NaN
>                              toString()
>    parseInt(str, 进制(可选)): 
>              string: 第一个非空格字符不是数字或者负号 -> NaN
>                      第一个非空字符是数字，开始解析直达非数字，将数字段转化为数字. '123blue' -> 123
> ```
>
> ```javascript
> 【String】
>    1. 每个字符串具有length属性  str.length
>    2.  + 运算符拼接字符串
>    3.  Array.from(str) 字符串数组化
>    4. 其他类型转字符： toString()方法 (null,undefined没有)
>                      String()方法 (调用toString，针对null、undefined单独返回)
>       Number.toString(进制=10) // 可设置转换的进制
>   5. str.slice(start, end=length)
>      str.substring(start,end=length)
>      str.substr(start, num)
>   6. 字符串大小写转换：
>      str.toLowerCase()
>      str.toUpperCase()
> ```
>
> ```javascript
> 【Object】
>            var obj = new Object()
>  1. obj 属性分两种：    自身属性
>                    _proto_属性
>  2. 对象创立之初：obj自带的属性都是_proto_:Object的属性
>     obj.constructor
>        .hasOwnProperty('属性名')
>        .isPrototypeOf(object)
>        .propertyIsEnumerable('属性名') // 属性名是否可枚举
>        .toLocalString()
>        .toString()
>        .valueOf()  // 返回对象的字符串、数值或者布尔值表示
>    
> 3. for...in.. 用于对对象属性进行迭代，若属性为null、undefined不执行循环体。
>    对象属性名顺序不可预测，因此
> ```
>
> ```javascript
> 【逻辑操作符】
> 1. JS中 ||、&& 在if中使用返回的是Boolean
> 2. JS中 ||、&& 也可用于其他类型数据
>    ||:  返回第一个为true的数据，若无则返回最后一个操作数
>    &&:  返回第一个为false的对象，无返回最后一个操作数
> ```
>
> ```javascript
> 【==】
> 1. 利用相等运算符判断时，当等式两边类型不一致需要先最类型转换。
>    (1) boolean 需要先转换成数值
>    (2) str == number需要先将str转换为number
>    (3) object == other 先调用object的valueOf()方法
>    (4) undefined == null    //true
>    (5) NaN == NaN           // false
> ```
>
> ```
> 【function】
>   1. 默认被传进两个采纳： this、arguments(箭头函数无)
>   2. arguments是类数组
>   3. 无重载，声明相同的函数名，后面覆盖前面
>   4. 声明的参数，调用时未被传入值，会被设置为undefined
>   5. arguments中的值永远于命名参数的值保持同步，修改arguments中的值，对应的命名参数上的值也会改变
>   6. arguments的长度是由调用函数时传入的参数个数决定的，不是
>   由定义函数时参数的个数决定的。
> ```

**引用类型**

> ```javascript
> Object属性访问的方式:
>   1. obj['属性名']
>   2. obj.属性名
> 
> Object内部是键值对，键值采用字符串的形式，如果属性名不是标准的标识符，则只能通过[]的形式进行查询。
> ```
>
> ```javascript
> 【Array】
> 
> 1. array可以动态扩展，因此若超出长度存放，则length自动以最后一个元素为基准+1.
> 2. Array.valueOf() // 返回的是数组
> 3. let arr = [1,2,3] 
>    arr['0'] === 1 // true
>    arr.hasOwnProperty('0')  // true
>    总结:  数组其实也是对象，它也可以利用整数型字符串作为索引
> 4. for...in... 遍历的是数组的索引
>    for...of... 遍历的是数组的值
> 5. 数组模仿栈行为是从最后推入，最后退出
>       Array.push()/ Array.pop()
> 6. 数组模仿队列行为
>       Array.push()/ Array.shift()
> 7. Array.sort()   // 默认采用升序排序
>                   // 接受一个callback作为参数，caalback:比较函数(value1,value2) // 返回-1/1/0
> ```
>
> ```javascript
> 【Date】
> 
> ```
>
> ```javascript
> 【RegExp】
> 
> ```
>
> ```javascript
> 【Function】
> 
> 1. 函数名实际上也是一个指向函数对象的指针  // 
> 
> 2. arguments 拥有一个callee属性，该函数是一个指针，指向拥有
>    这个arguments对象的函数，在递归调用时可以使用arguments.callee代替原函数名，从而起到解耦合的作用。
> 
> 3. 函数有两个基本属性：prototype、length 
>    fun.length获取函数希望接受到的参数个数
> 
> 
> ```
>
> **基本包装类型**
>
> ```javascript
> Number、Boolean、String
> 
> 1. 当利用基本类型去调用属性和方法时，会进行：
>     a.创建一个基本类型的对象实例
>     b.利用该对象实例去调用方法
>     c.销毁这个实例
> 
> 2. 自动创建的基本包装类型的对象，只存在于一行代码的执行瞬间，然后立即被销毁。
> ```
> 
>```
> 【Global】对象
> 
> 1. 所有全局定义的属性和函数，都是Global对象的属性
>    e.g: isNaN()、isFinite()。parseInt()和parseFloat()
> 
>    2. URI编码
>    encodeURI(uri)   // 对uri进行编码，以便发生给浏览器
>                        将url的空格用%20替换
>    encodeURIComponent(uri) //对所有非标准字符(数字、字母)进行替换。
>    decodeURI()
>    decodeURIComponent()
> 
>    3. eval() 方法
> 说明：只接受一个参数，即字符串，它会将字符串当作语句放在eval所在行进行执行。
>    eval('alert('hello')')  ==>  alert('hello')
>    eval('function foo(){}')  // eval存放的函数不会提升只有在执行到该语句时才会创建。 可在语句后调用该函数
> ```

**BOM**

> ```javascript
> 【BOM】浏览器对象模型
> 
> 1. window对象即代表着浏览器，又是ECMAScript规定的Global对象
> 在网页中定义的任何属性和方法都以window作为Global对象
> 
> 2. 利用window查询未存在的变量，会返回undefined
> 
> 3. window.screenLeft属性  窗口相对于屏幕左边的距离
>    window.screenFloat属性 窗口相对于屏幕上面的距离
> 
> 4. 窗口大小
>    IE、Safari、Chorme、Opera都支持四个属性
>                window.innerWidth  
>                window.innerHeight
>                window.outerWidth
>                window.outerHeight
>   chrome：四个属性返回相同值（viewport大小非浏览器窗口大小）
>   IE9+、 Safari， Firefox：outerWidth和outerHeight返回浏览器窗口本身尺寸。innerWidth，innerHeight表示页面视口大小（减轻边框宽度）。
>   
>   混杂模式下： doucment.documentElement.clientHeight
>              doucment.documentElement.clientWeight
> 
>   尺寸修改： window.resizeTo(v1,v2)   // 新浏览器宽高
>            window.resizeBy(v1, v2)  // 与原窗口宽高差
> 
>   浏览器窗口大小： 上边框(地址+工具) + 视图
> 
> 5. 新建窗口
>    window.open(url,'窗口名称','新建窗口属性(xx1=、xx2=)',boolean)
>   e.g:window.open("http://www.wrox.com/","wroxWindow", 
>  "height=400,width=400,top=10,left=10,resizable=yes");
>   第二个参数： 指定浏览器在特定的窗口框架中打开，若不存在该窗口会根据第三个参数新建窗口，在不打开新窗口时会忽略第三个参数
>   
>    window.open()返回新串口的引用，若浏览器将其拦截返回null
>   
> ```
>
> ```javascript
> 【location】对象
> 
> 1. 记录了窗口加载的文档有关信息：hash：返回URL中的Hash
>                             host： 服务器名称和端口号
>                             hostname：服务器名称
>                             href：完整的URL
>                             pathname
>                             port
>                             protocol：页面使用的协议
>                             search：返回URL查询字符串
> 2. location即属于window，也属于document
>    window.location 与 document.location引用的是相同的对象
> 
> 3. window.location = '新的url'；
>    doucment.href = '新的url'； 
>    上述会立即打开新的url，并且在浏览器历史记录中生成一条记录
>   other：
>       location.hash= '#xxx';   打开新的url
>       location.search = '?q=java' 
>       location.hostname = 'wwww.baidu.com'
>       location.pathname = 'home1';
>       location.port = 8080;
>   上述任何一种方法：打开url的同时都会生成新的历史记录
>   若不希望生成新的历史记录：location.replace('url')
> 
> 4. 重新加载页面
>    location.reload() // 重新加载 （可能从缓存中）
>    location.reload(true) // 重新加载 （强制从服务器）
> ```
>
> ```javascript
> 【navigator】
> 
> 1. navigator对象记录了浏览器信息，浏览器不同属性不同
> 
> 2， 检测插件：
>    非IE浏览器： navigator.plugins 返回一个插件数组，数组元素是对象有四个属性：  name: 插件名字
>                description：插件的描述
>                filename： 插件的文件名
>                length：插件处理的MIME类型数量
>    IE浏览器： 需要尝试创建ActiveXObject(name)
>              将上述语句放入try catch模块中，成功返回true
>              name是一个COM标识符
> ```
>
> ```javascript
> 【screen】
> ```
>
> ```javascript
> 【history】
> 
> 1. history对象保存着用户上网的历史记录
> 2. hostory.length  // 浏览器历史纪律数量，0是第一条记录
> 3. history.go(int) // 正数前进，复数后退
> 4. history.go('url') // 跳转到记录中与之匹配的最近的url
> 5. history.back()
> 6. history.forward()
> ```

**客户端检测**

> ```javascript
> 【能力检测】
> 
> 1. 目的： 不识别特定浏览器，只识别该浏览器是否具备某种能力
>    步骤1： 先检测常用的属性是否存在，后检测备选方案
>    步骤2： 能力检测检测的是属性是否存在，我们不能想当然认为属性
>           的存在就一定是另外一种浏览器。我们使用什么属性就一定要检测什么属性。
>    步骤3： 特性存在后，我们应该对其行为作出检测。因为不同对象会存在相同的属性名
> ```
>
> ```
> 【怪癖检测】
> 
> 1. 目的： 检测浏览器存在的缺陷
> ```
>
> ```
> 【用户代理检测】
> 
> 1. 服务器通过HTTP的userAgent字段，对浏览器类型进行检测
> 
> 2. 服务器容易被浏览器欺骗
>    【用户代理字段发展史】
> ```

**DOM**

> ```
> 【DOM】:文档对象模型
> 
> 1. HTML和XML的API为document
> 
> 2. 文档中节点的类型：
>     a. 文档元素： 最外层元素，其他元素都包含在文档元素中 
> <html>(html中，xml中任何元素都可成为文档元素)。 
> 
> ```
> 
>```javascript
> 【document】
> nodeType： 9
> nodeName:'#document'
> nodeValue:null
> parentName: null
> 
> 1. document.body 直接访问body元素
> 
> 2. document.createElement() 创建新的元素
> 
> 3. document.title 标签页标题
> 
> 4. document.URL  取得完成URL
> 
> 5. document.domain 取得域名
> 
> 6. document.getElementById('ID名')  // 区分大小写
> 
> 7. document.getElementByTagName('标签名') // 返回HTMLCollection对象， 支持按索引或者按name值访问
> 
> 8. document.getElementByName('name名')  // 返回HTMLCollection对象
> 
> 9. document.images  // 获取所有img 标签
> 
> 10 document.links   // 获取文档中带有href特性
> ```
> 
>```javascript
> 【Element】
> nodeType：1
> nodeNmae：元素标签名
> nodeVlaue：null
> parentNode：Document or Element
> 
> 1. 元素特性操作 
>     getAttribute、   // 一般用于访问用户自定义属性
>       ele.getAttribute('属性名')； // 不区分大小写
>     setAttribute、
>       ele.setAttribute('属性名1'，'值1')
>     removeAttribute
> 
> 2. attributes属性
>    attributes属性中包含一个NamedNodeMap对象
> NamedNodeMap对象拥有下列方法：
>    getNamedItem(name);  返回nodeName属性等于name的节点
>    removeNamedItem(name); 从列表中移除nodeName属性等于name的节点。
>    setNamedItem(node); 向列表中添加节点，以节点的nodeName属性为索引。
>    item(index);  返回位于idnex处的节点
>    element.attributes.getNamedItem("id").nodeValue;   
> ```
> 
>```javascript
> 【Text】
> nodeType: 3
> nodeName: '#text'
> nodeValue: 节点所包含的文本
> parentNode: Element
> 
> 1. nodeValue属性和data属性访问text包含的文本
>    <div></div>   没有内容，没有文本节点
>    <div> </div>  有一个空格，存在文本节点
> 
> 2. appendData(text) 
>    deleteData(text)
>    insertData(offset, text) // 从offerset指定的位置加入text
>    replaceData(offset,count,text) text文本替换[offset,offset+count]
>    substringData(offset, count) 提取[offset，offset+count]的字符串
>    splitText(offset)  // 在指定位置分割成两个文本节点
> 
>    3. 创建文本节点
>    var text = document.createTextNode('文本')
>    div.appendChild(text);
> ```
> 
>```javascript
> 【Comment】注释类型
> nodeType: 8
> nodeName: '#comment'
> nodeValue: 注释内容
> parentNode: Element或者Document
> 
> 1. 创建注释节点
> document.createComment('注释内容')
> ```
> 
>```javascript
> 【CDATASection】
> 只针对XML文档，表示CDATA区域，与Comment类似，CDTATSection类型继承自Text类型
> ```
> 
>```javascript
> 【DocumentType】
> 1. Firefox、Safari、Opera支持
> 
> 2. 支持它的浏览器会将其放入在document.doctype中
> ```
> 
>```javascript
>  【DocumentFragment】
>  在文档中没有对应的标记。DOM 规定文档片段
> （document fragment）是一种“轻量级”的文档，可以包含和控制节点，但不会像完整的文档那样占用
> 额外的资源。DocumentFragment 节点具有下列特征：
>  nodeType 的值为 11；
>  nodeName 的值为"#document-fragment"；
>  nodeValue 的值为 null；
>  parentNode 的值为 null；
> ```
> 
>```javascript
> 【Attr】
> 元素的特性在 DOM 中以 Attr 类型来表示。
> 
>  nodeType 的值为 2；
>  nodeName 的值是特性的名称；
>  nodeValue 的值是特性的值；
>  parentNode 的值为 null；
> 
> Attr对象有三个属性：name、value、specified(bool值)
> 
> 1. 创建属性，并将其添加到元素中
>   var attr = document.createAttribute("align"); 
>   attr.value = "left"; 
>   element.setAttributeNode(attr); 
> ```
> 
>```javascript
> 【DOM1】
>
> 1. DOM1定义了节点类型Node，除了IE浏览器，其他浏览器都可以访问到该属性。
> 
> 2. Node.noderType属性表明节点类型
> 
> 3. 一共12个节点类型，保存在Node的常量属性中
>    Node.ELEMENT_NODE    1
>    Node.ATTRIBUTE_NODE  2
>    Node.TEXT_NODE       3
>    Node.CDATA_SECTION_NODE 4
>    Node.ENTITY_REFERENCE_NODE 5
>    Node.ENTITY_NODE 6
>    Node.PROCESSING_INSTRUCTION_NODE 7
>    Node.COMMENT_NODE  8
>    Node.DOCUMENT_NODE 9
>    Node.DOCUMENT_TYPE_NODE 10
>    Node.DOCUMENT_FRAGMENT_NODE 11
>    Node.NOTATION_NODE 12
> 
>    4. childNodes属性
>    someNode.childNodes[0]  // 访问firstchild
>    document.creatElement === document.childNodes[0]
> 
> 5. 操作节点
>   someNode.appendChild(newNodes)
>   someNode.insertBefore(node)
>   someNode.replaceChild(原节点, 替换的节点)
>   someNode.removeChild(node) //返回该节点
> 
> 6. cloneNode
>   创建调用该方法的节点完全相同的副本。
> 
>     e.g: someNode.cloneNode(true)  // 执行深复制
> 
> ```
> 
> ```
> 【DOM操作技术】
>
> ```

**DOM扩展**

> ```
> W3C制定了一个新标准，Selectors API，其使得浏览器可以支持CSS查询。
> 
> 【querySelector】
> querySelector(): 接受CSS选择符，返回与该模式匹配的第一个元素，不存在则返回null。
> querySelector('body');
> querySelector('#mydiv');
> querySelector('.mydiv');
> 
> 【querySelectorAll】
> querySelector(): 接受CSS选择符，返回与该模式匹配的所有元素，不存在则返回null，返回类型是NodeList。
> 
> 能够调用上述两个方法的节点类型： Document、DocumentFragment、Element
> 
> 【matchesSelector】：
> Selectors API Level2 为element元素新增一个方法，该函数接受一个CSS选择符，如果调用元素与该选择符匹配，返回true。
> ```
>
> ```
> 【元素遍历】
> 
> 为解决空白文节点问题， W3C定义了Element Traversal，其为DOM元素添加了5个属性：
>  1. childElementCount： 返回子元素个数
>  2. firstElementChild： 指向第一个子元素
>  3. lastElementChild：  指向最后一个子元素
>  4. previousElementSibling： 指向前一个同辈元素
>  5. nextElementSibling： 指向后一个同辈元素
>  
> ```
>
> ```
> 【HTML5】
> 
> 1.getElementsByClassName():接受一个参数，一个包含一个或者多个类名的字符串，返回符合的所有元素(Nodelist)。该方法了可以被document以及所有Element元素调用。
> 
> 2. classList
>    【length】: 指明元素class有几个  <div class="db user disabled">
>    【add()】: 将给定字符串值添加到列表中，值存在不添加
>    【contains(value)】: 列表中是否存在给定的值，存在返回true
>    【remove(value)】: 从列表中删除给定字符串
>    【toggle(value)】: 列表中已经存在给定的值删除它，列表中没有给定的值，添加它。
>    
> 3. 焦点管理： document.activeElement属性。该属性会始终引用DOM中获得焦点的元素
>    【焦点方式】： 页面加载，用户输入
>    【默认】：文档刚刚加载完，document.activeElement中保存的是docuemnt.body元素。
> 
> 4. HTMLDocument变化
>    HTML5新增readyState这个属性用于检测文档加载状态
>    1、 readyState = loading  //正在加载
>    2.  readyState = complete //加载完成
>    
> 5. head属性
>   HTML5之前有document.body引用文档的<body>元素
>   HTML5使用document.head引用文档的<head>元素
>   
> 6 字符集属性：  document.charset  文档中实际使用的字符集
>               document.defaultCharset 文档中默认使用的字符集。
> 
> 7 插入标记：
>   innerHTML：  ele.innerHTML 会返回其所有子节点
>                ele.innerHTML = xx 创建新的DOM树用该DOM替换所有子节点。
>   限制： 通过innerHTML插入<script>标签不会被执行，称为无作用域的标签。插入的字符串会成为空，若想执行必须在字符串之前插入一个有作用域的字符。
>   
>   outerHTML： 读模式： 返回给该元素及所有子元素
>               写模式： 创建新的DOM树，将该DOM数替换原先元素。
>               
>   insertAgjacentHTML(参数1， 参数2)：
>   
> ```
>
> ```
> 【专有扩展】
> 
> 1. 文档模式： 决定使用哪个级别的CSS，在JS中使用那些API
> 
> 2. children属性 ，该属性是HTMLCollection实例只包含元素中同样是元素的子节点。
> 
> 3. contains()方法， 检测输入的节点是否是调用该方法节点的后代
> 
> 4. innerText 插入文本，删除元素所有子节点并将文本替换，FireFox不支持该属性，其支持textContent
> 
> 5. outerText   写模式: 会用字符串替换整个子元素
> 
> 6. 滚动
>       scrollIntoViewIfNeeded()
>       scrollByLines(LineCount)
>       scrollByPages(pageCount)
> ```

**事件**

> ```javascript
> 【事件流】
> 
> 1. 事件流：描述页面接收事件的顺序
>    IE：       事件冒泡流
>    Netscape： 事件捕获流
> 
> 2. 事件冒泡流：事件从触发元素开始向上传递，直到document
> 
>    事件捕获流：事件从最顶层开始document，直到触发元素
> 其用意是在于事件到达预定目标之前捕获它。
> 
> 3. DOM2级规定事件流包括三个阶段：事件捕获阶段、处于目标阶段、事件冒泡阶段。
> ```
>
> ```javascript
> 【DOM级事件处理程序】
> 
> 1. DOM0级处理程序
>   (1). btn = document.getElementById('myBtn');
>        btn.onclick = function(){}
>    注： function 中的this对象是元素本身
> 2.DOM2级处理程序
>   (1) document上定义两个方法 addEventListener()
>                            removeEventListener()
>       使用addEventListener可以为同一个事件添加多个回调函数
>       按顺序执行。
> 
> 3. IE事件处理程序 attachEvent、detachEvent()
>    var btn = document.getElementById('');
>    btn.attachEvent('onclick',callback);
>    
>    btn这种方法与DOM0级的区别，回调函数的作用域是不一样的，IE中函数this绑定的是window。
>    attachEvent也可以为相同事件添加多个回调，但是执行顺序是从最新的开始。
>    
> ```
>
> ```javascript
> 【DOM中事件对象】
> 
> 1. event是DOM中的事件对象，触发回调函数时，都会将默认将该对象传入
> 
> 2. event上的属性： bubbles
>                  cancelable
>                  currentTarget
>                  defaultPrevented
>                  eventPhase 事件当前阶段
>                  target     事件的目标
>                  type       被触发的事件类型
>                  preventDefault() 阻止事件的默认行为
>                  stopPropagation() 阻止事件传播
>           
> 3. 跨浏览器使用事件对象              
> ```
>
> ```javascript
> 【事件类型】
>    1. UI事件： 用户界面事件，用户与页面上元素交互时触发
>    2. 焦点事件： 当元素获得或者失去焦点时
>    3. 鼠标事件： 鼠标在页面执行操作时触发
>    4. 滚轮事件： 使用鼠标滚轮时触发
>    5. 文本事件： 文档中文本输入时触发
>    6. 键盘事件： 用户在页面使用键盘输入时触发
>    7. 合成事件
>    8. 变动事件： 底层DOM结构发生变化时触发
>  
>  【UI事件】：
>     load事件：页面完全加载完成(图像，JS文件，css文件)，会触发window上的load事件
>     img、script、link 都有onload事件，在定义这些标签的onload事件时，必须保证window的load事件完成
>     
>     unload事件： 用户从一个页面切换到另一个页面，使用该事件清楚引用避免内存泄漏
>     使用javascript
>     使用<body onunload="">, event.target=document
>     
>     resize事件 ：浏览器窗口被调整到新的高度或宽度
>     
>     scroll事件： 其会在页面滚动期间重复触发
>  
>  【焦点事件】
>     页面上的元素失去焦点或者获得焦点时触发，6个焦点事件
>    
>     blur： 元素失去焦点时触发，事件不会冒泡，所有浏览器都支持它
>     DOMFocusIn: 元素获得焦点时触发，与focus等价，但会冒泡，只有Opera支持这个事件
>     DOMFocusOut：元素失去焦点时触发，只有Opera支持
>     focus： 元素获得焦点时触发，不会冒泡，所有浏览器支持
>     focusin： 获得焦点，可冒泡
>     focusout：失去焦点，可冒泡 IE5+ chorme、Safari5.5+
>     
>     从一个元素移动到下一个元素：
>     focusout、focusin、blur、DOMFocus、focus
>     
>  【鼠标与滚轮事件】
>     DOM3 定义了9个鼠标事件
>     
>     1. click
>     
>     2. dbclick 双击鼠标触发
>     
>     3. mousedown 用户按下任意鼠标按钮时触发
>     
>     4. mouseenter 鼠标光标从元外部首次移动到元素范围内时触发，事件不会冒泡，IE。FireFox9+、Opera支持
>     
>     5.mouseleave：元素上方的鼠标移动到元素范围之外时触发
>     
>     6.mousemove：元素指针在元素内部移动时重复触发
>     
>     7. mouseout： 鼠标指针位于元素上方，用户将其一如到另一个元素时触发。新的元素可能在原元素的外部或者内部
>     
>     8. mouseover：鼠标指针位于元素外，用户首次将其移入到另一个元素边界时触发。
>     
>     9.mouseup：用户释放鼠标按钮时触发
>  
>  页面上所有元素都支持鼠标事件
>      mousedown、mouseup、click、dbclick 必须相继触发
>    mousedown、mouseup、click、mousedown、mouseup、click、dbclik
>    
> 【鼠标滚轮事件】
>    鼠标事件发生的位置信息，都被保存在事件对象的clientX。clientY中。event.clientX 和 event.clientY
>    
>    页面坐标位置：事件在页面中什么位置发生，event.pageX
>                event.pageY
>    在页面不发生滚动时，clientX = pageX
>                     clientY = pageY
>    屏幕坐标位置： event.screenX、event.screenY，指明鼠标在整个电脑屏幕的位置。
>    
>    mousewheel: 在垂直方向上滚动页面时(无论向上还是向下)，就会触发mousewheel事件，事件会一直冒泡到window/document上
>    mousewheel事件的event对象上有event.wheelDelta属性，该属性在用户进行前后滚动时会发生+120/-120倍的变化。
>    
> 【键盘与文本事件】
> 
> 1. keydown : 用户按下键盘上的任意键时触发,按住不放会重复触发此事件
> 
> 2. keypress: 用户按下键盘上的【字符键】时触发，而且如果按住不放的话会重复触发此事件。
> 
> 3. keyup：用户释放键盘上的键时触发
> 用户按下非字符键时：首先触发keydown、然后就是keyup事件
> 
> 4. 键码，在发生keydown事件和keyup事件时，event对象的keycode属性中会包含一个代码。对于小写字母或者数字，keycode与ASCII码相同，数字7：55, 字母A：65。
> 
> 【变动事件】
> 
> 1. DOMSubtreeModified：DOM结构发生任何变化时触发。这个事件在其他任何事件触发后都会触发
> 2. DOMNodeInserted：一个节点作为子节点被插入到另一个节点时触发。
> 3. DOMNodeRemoved: 节点从其它父节点中被移除时触发
> 4. DOMNodeInsertedIntoDocument: 
> 5. DOMNodeRemovedFromDocument
> 6. DOMAttrModified: 特性被修改后触发
> 7. DOMCharacterDataModified：文本节点的值发生变化时触发
> 
> 删除节点： removeChild() 、replaceChild()
>      DOMNodeRemoved -> DOMNodeRemovedFromDocument
> 
> 插入节点：appendChild()。replaceChild()
>      DOMNodeInserted --> DOMNodeInsertedIntoDocument
> 
> 【HTML5事件】
> 
> 1. contextmenu
> 
> 2. beforeunload
> 
> 3. DOMContentLoaded事件
>    window的load的事件会在一切都加载完毕时触发，嗯DOMContentLoaded事件是在形成完整的DOM树之后就会触发，不理会图像，javaScript文件，CSS文件或其他资源是否已经下载完毕。
>    
> 4. haschange事件
>   URL的参数列表中#后面发生改变会触发该值
> 
> ```
>
> ```javascript
> 【事件委托】
> 
> 1. 利用事件冒泡机制，通过指定一个事件管理某一类型的所有事件。
> ```

**错误处理与调试**

```javascript
【try-catch】：
    try{
        // 
    }catch(error){
        
    }finally{
       // 无论catch和try包含什么代码，都不会阻止finally执行
    }

【错误类型】： 7种错误类型
      Error： 基本错误类型，其它类型继承该类
      EvalError ： 使用eval()函数发生异常时抛出
      RangeError： 数组超出范围时触发
      ReferenceError：访问不存在的变量或者对象
      SyntaxError：语法错误的字符串传入eval中
      TypeError：变量保留意外类型，或者访问不存在的方法
      URIError：使用encodeURI()/decodeURI()时，URI格式使用错误。
      每种错误类型都接受一个构造参数(字符串)，即错误信息
      
 【抛出错误】： throw， 代码遇见thow会立即停止运行
 
 【自定义错误】 function XxxError(str){
             this.name = 'XxxError';
             this.message = str
           }
          XxxError.prototype = new Error()
 
【error事件】: Web浏览器支持error事件，只要程序没有通过try-catch处理，则会触发该事件(Opera和Safari不支持)。
error只支持DOM0级事件处理方式： window.onerror = function(){}
       TIP: 图像也支持error事件
 
 
【调试技术】：
    1。console.log      打印在控制台
       console.error()      
       console.info()
       consoole.warn()

   2. 将信息记录在当前页面
      1. 创建一个div节点，将信息通过该节点的innerHtml
      
   3. throw 抛出错误，大型程序会使用assert(结果为true的条件，false时程序抛出的错误)；
   
   
```

**JSON**

```javascript
1. 一种数据结构：基本值、对象、数组 //对象名字必须带引号

2. JSON可以直接解析为JavaScript对象

3， IE 8+ 、FireFox3.5+ Safari 4+、Chorome、Opera 10.5+
    引入JSON对象，对象有两个方法：stringify()、parse()

4. JSON.stringify(obj)  // 将javascript对象序列化成为JSON对象
   JSON.stringify(obj, filter,options)
   filter:过滤器，若是数组则 指定函数对obj特定属性进行序列化并返回。
   若filter是函数，function(key,value),函数返回的值会替代原来键对应的值，若返回undefined则序列化时会忽略这个键值

   options: 数值，指定属性开始处缩颈几个空格
            字符串，指定属性开始处用该字符串代替空格
 5.
```



## JS知识点汇总清单

```
1. 变量的命名方式

2. 操作符：位操作符、 全等和非全等的区别
   操作符的优先级 (MDN, 练习题)
   with语句

3. 数据类型：基本类型 引用类型  

4. 作用域和内存 (高程第四)

5. 对象、函数、 原型链
   函数如何添加属性

6. 异步事件机制 Promise awaite

7. 错误处理与调试

8 浏览器： BOM DOM


【进阶书籍】

【公众号】
    1. 技术漫谈：专注于从规范的角度讲解 JS 知识点，图解重难点，分享前端面试，前端工程化，项目实战等系列内容
    2. 前端技术江湖 ：javascript垂直技术分享社区
                    500道面试题
    3. React ：专注于 React系列精彩内容推荐。关注大前端、Node全栈、Flutter、WebAssembly、小程序等互联网科技领域最前沿技术，定期分享个人创业经验
    
    4. 图雀社区：已有 React / Vue / Nest.js / Docker / TypeScript / 算法 / Taro、uni-app、原生小程序等完整的学习路线和实战教程
    
    5. 前端印象
    
    6.全栈修仙路：专注分享 TS、Vue3、前端架构和源码解析等技术干货。关注后可免费下载《重学TS》、《前端进阶》、《源码探秘》等高质量原创电子书。
    
    7. 程序员成长指北：专注 Node.js 技术栈分享，从 高级前端 到 Node.js与前端工程化 再到 后端数据库，祝您成为优秀的高级 Node.js 全栈工程师
    
【大佬】

    1. 尤雨溪：专业是室内艺术和艺术史，找不到工作去了Parsons就读【美术设计和技术的硕士】，涉及设计和编程。 受JavaScript吸引【快速开发，将内容发布在浏览器中让任何人可以看到】。 受【chorme experments】震撼开发类似chrome experments的项目，加入google。
    尤雨溪： 眼中的Vue和React框架
    我认为在所有的框架中，Vue 可能与 React 最像，但从更广泛的意义上说，在所有框架中，我自己创造了一个概念叫渐进的框架。因为 Vue 的核心组成只是数据绑定和组件，和 React 差不多。它只是解决了一小部分很重要的痛点。与 React 相比，Vue 可能更简单易用，只知道一些 HTML，JavaScript 和 CSS 知识的人都可以很快入门 Vue。

在框架层面上，我是用一个非常精简和尽可能小的的内核来构建的。但是当构建更复杂的应用的时候，有很多其他的问题需要解决。比如说路由，或者说怎么处理跨组件通信，怎么样在大型应用程序中共享状态，这样的话我们就还需要更多的构建工具来模块化我们的代码库。怎么样来组织样式和各种各样的静态资源？像 Ember 或 Angular 这些非常完整的框架，它们就想解决所有可能遇到的这些问题，并把这些功能全都集成到框架中。

这就叫有得必有失吧。对用户使用情况的假设越多，框架最终的灵活性就越低。或者像 React 这样把很多问题都留给社区。React 社区是非常非常活跃的，经常有很多牛 X 的想法跳出来，当然也有不少不完美的想法。Vue 就是比较折中，仍然保持一个很小的核心，只提供一些最重要的功能。但是我们还是在逐渐提供一些更多的独立解决方案，比如说路由，状态管理，构建工具链和 CLI。它们都是官方维护的，有很好的文档，设计的也非常好，可以各种搭配使用，但重点是不需要的时候就可以不用。我认为这可能是 Vue 作为一个框架最大的特色。
     尤雨溪的【偶像】: TJ Holowaychuck 和 Guillermo Rauch
尤雨溪主要通过看网上资源和书来学习编程，同时他提到重要的学习方法【别人的代码】，TJ的代码十分优雅，是他的偶像
     TJ的推特：https://twitter.com/tjholowaychuk
 TJ： 设计师出身，工作几年开始搞Flash，开始写脚本，最主要学习方式【阅读别人代码，并搞懂】
 
 【玉伯】： 全情投入、 守正出奇、 等待花开
  全情投入： 超越一切的热爱；
  
  守正出奇：《华杉讲透孙子兵法》  正是你的核心方向，奇要帮助到这个方向。
  
  等待花开： 定力和耐心。 两三年才可以看见一点回报。
  
  【取舍】【投入】【战略】 才能撑起你的 【方向】【目标】【愿景】
                    支点： 【使命感/意义】
               深海： 【心态】【能力】【价值观】
    
【周爱民】： 《大道至简——软件工程实践者的思想》


【前端题库】

高频前端面试题汇总之JavaScript篇
 
   https://juejin.cn/post/6940945178899251230

再来100道JS输出题酸爽继续
   https://juejin.cn/post/6844904203110842376

中文排版指南
   https://github.com/sparanoid/chinese-copywriting-guidelines/blob/master/README.zh-CN.md  
   
```

## JS题型总结

### 数据类型

```
1. JavaScript有哪些数据类型
   Undefined、Null、Boolean、Number、String、Object、Symbol、BigInt
   
2. 数据类型和引用类型区别


3. 数据类型的检查方式：
    a. typeof
    b. instanceof
    c. constructor
    d. Object.prototype.toString.call()
 
4. 判断数组的方式：
   a. Array.isarray()
   b. obj.__proto__ = Array.prototype
   c. Array.prototype.isPrototypeof(obj)
   d. Object.prototype.toString.call(obj).slice(8,-1) === 'Array';
   e. obj instanceof Array   ? 
 

5. null 和 undefined 的区别                   【4】

6. typeof null 的结果是什么，为什么
     res: object
     
7.  instanceof 操作符实现原理及实现
    ans: 比较右边构造函数是否在左边对象的原型链上
 
8. 为什么0.1+0.2 ! == 0.3，如何让其相等 ？       【7】

9. 如何获取安全的 undefined 值？                【8】
   原因： undefined可以被当作一个标识符使用
   
10. typeof NaN 的结果是什么？
    ans: number,  NaN 是一个特殊值，它和自身不相等.
    
11.  isNaN 和 Number.isNaN 函数的区别？

12.   == 操作符的强制类型转换规则？              【11】

13.   其他值到字符串的转换规则？

14.   其他值到数字值的转换规则？
      
15.  其他值到布尔类型的值的转换规则？

16. 什么是 JavaScript 中的包装类型？           【17】

17. 为什么会有BigInt的提案？                   【20】

总： 【数据类型】 【检测数据类型】 【数据类型的互转】 【数据类型的包装】 
```

### 操作符

```
1.  || 和 && 操作符的返回值？                      【15】

2.  Object.is() 与比较操作符 “===”、“==” 的区别？   【16】

3.  JavaScript 中如何进行隐式类型转换？              【18】

4.  + 操作符什么时候用于字符串的拼接？                【19】

5.  == 操作符的强制类型转换规则？                    【11】

6. new 操作符的实现原理
   a. 创建一个空对象
   b. 将构造函数赋予到该对象的原型链上
   c. 将该对象绑定为构造函数的this参数
   d. 执行函数的代码。
   e. 判断返回类型，若是值类型返回创建的对象，若是引用返回引用的对象。
   
7. 常见的位运算符有哪些？其计算规则是什么？             【3.11】
   a. &
   b. |
   c. ^
   d. ~
   e. <<
   f. >>
   g. 原码、 补码、 反码

8. 运算符优先级 
 https://juejin.cn/post/6844904024991334407#heading-20

【数据类型的隐式转换】 【优先级】
```

### JS基础

```
A. 对作用域、作用域链的理解
   a. 全局作用域
   b. 函数作用域
   c. 块级作用域
   
B. 对执行上下文的理解
   a. 执行上下文的类型
   b. 执行上下文栈
   c. 创建执行上下文

1. map 和 Object 的区别          【3.2】

2. map 和 weakMap 的区别         【3.3】

3. JavaScript有哪些内置对象       【3.4】

4. 对JSON的理解                  【3.6】

5. JavaScript脚本延迟加载的方式有哪些？ 【3.7】

6. escape、encodeURI、encodeURIComponent 的区别   【3.15】

7.  JavaScript为什么要进行变量提升，它导致了什么问题？ 【3.17】

8.  ajax、axios、fetch的区别

【作用域】 【执行上下文】 【垃圾回收】 【其它】

【文章】： 
   1. 栈、堆、上下文、作用域、任务队列
   https://juejin.cn/post/6966158666030383118
```



### 对象

```

1. object.assign和扩展运算法是深拷贝还是浅拷贝，两者区别  【21】

2. 数组和对象的区别

3. 数组的原生方法

4. 类数组对象的理解， 如何转化为数组

5. JavaScript 类数组对象的定义？    【3.8】

6. for...in和for...of的区别       【3.25】

7. 对原型、原型链的理解             【3.26】

8. 原型链的修改和重写

9. 原型链的指向

10. 原型链的终点是什么，如何打印出原型练的终点

11. 如何获得对象非原型链上的属性

12. 对象创建的方法

13. JS如何创建二维数组
https://juejin.cn/post/6968645442691137572

【对象创建方法】 【数组】 【原型链】
```

### 函数

```  
1. 如果new一个箭头函数的会怎么样                【2.3】

2. 箭头函数与普通函数的区别                     【2.4】
   a. this指针声明时固定
   b. 无arguments参数
   c. 箭头函数无自己的prototype
   d. 箭头函数不能用作Generator函数，不能使用yeild关键字
    
3. 箭头函数的this指向哪                        【2.5】

4. 为什么函数的 arguments 参数是类数组而不是数组？ 【3.12】

5. 什么是尾调用，使用尾调用有什么好处？            【3.18】

6. 如何判断一个对象是否属于某个类？               【3.22】

7. 闭包的理解                                 【5.1】

8. 绑定this的方法

【this绑定】 【闭包】 【函数的原型】 

一文读懂this
https://juejin.cn/post/6968591172918837284
```

### ES6

```
1. ES6方法：对象与数组的解构的理解  【2.8】

2. 如何提取高度嵌套的对象里的指定属性？    【2.9】  运用解构
            const school = {
            classes: {
            stu: {
            name: 'Bob',
            age: 24,
            }
          }
        }
    如何读取name

3. let、const、var的区别        【2.1】

4. ES6中模板语法与字符串处理      【2.11】

5. 扩展运算符的作用及使用场景      【2.6】

6. 如何使用for...of遍历对象      【3.26】


【解构】【扩展运算符】【模板语法】
```

### DOM与BOM

```
1. 什么是 DOM 和 BOM？              【3.13】

2. 常见的DOM操作
   a. 节点获取：
   b. 节点修改：
   c. 节点删除：

```

### 模块

```
1. ES6模块与CommonJS模块有什么异同？   【3.19】
```



## 精通JS

```
1. 实现一个简易的MarkDown编辑器
  https://juejin.cn/post/6968632189894262791
  
2. 利用JS给图片打马赛克
  https://juejin.cn/post/6968258826285875208
  
3. 在线生成CSS三角形
  https://juejin.cn/post/6962897454781956133
  
4. 36个代码手写题
  https://juejin.cn/post/6946022649768181774
```

## 喜欢JS

### 忍者秘籍

#### 函数

```javascript
【JavaScript 的编写水平】：是否将代码当作函数式语言(functional language)来编写

【一等公民】：  1. 函数与对象共存   
             2. 函数能被当作任意类型的JavaScript对象 
             3. 函数能被变量引用
             4. 函数能作为参数传递
          
 【公民】是社会普遍成员 
 【一等】：在JS中指的是与对象拥有着相同的行为。
 【第一类对象】：在JS中一等公民又可以被称作第一类对象，它被创造之出便拥有和对象相同功能，是第一类对象。
 
 【基本特权】：首要满足三个条件 1. 能够作为参数传递  2. 可以被函数返回
                           3. 可以赋给变量
 【函数式编程】： 第一个函数式编程语言是 Lisp 由约翰.麦卡锡提出。
 
 【函数式】: 将函数作为实体创建， 并将其作为参数传入，并将其作为参数接
           收。
 
 对象的特性： 1. 支持字面量创建   var obj ={};
            2. 对象可以赋给变量， 数组项， 对象的属性
            3. 对象可以作为参数传递给函数
            4. 对象可以作为返回值
            5. 对象可以动态分配内存  obj.name = "zzj";
            
 函数的特性： 1. 支持字面量创建  function myfun () {};
            2.  函数可以赋给变量， 数组项， 其他对象的属性
            3.  函数可以作为参数传递
            4.  函数可以作为返回值
            5.  函数可以动态分配内存  mfun.name = 'zzj'
  
 【字面量】literal：按照字面的方式直接定义变量. 这个对象什么样子就是我们
                  字面上的样子    var zzj = {name:  age:} (显式)
                                var zzj = new Person()
 
                                
  【回调函数】: 函数作为参数传递给另一个函数， 该函数会在某个时间节点调用
             该函数。 
     【同步】：函数作为参数
     【异步】：回调
 
 【自记忆结果】：通过声明函数属性，将结果进行记忆
     function myfun(value){
         
         if(!myfun.record){
             myfun.record = {}；
          }
         
         if(myfun.record[value]){
            return myfun[value];
         }
         // 函数逻辑
         return myfun.record[value] = 结果；
     }

                    【函数是可以用在程序中的值】
 【函数定义】： 4种不同的方式
     1. 【函数定义】/【函数表达式】       
         函数定义： function myfun(){          函数名强制 声明独立
                      // 函数体
                   }
                   
                   function myfun(){
                       function myfun2(){    函数名可选
                          // 函数体2
                       }
                   }
    
        
        函数表达式： var a = function() {};    // 将函数表达式整体看作对象
        
        IIFE： 函数表达式的立即调用，加括号。 
               (function (){})(args); 括号的作用是提醒JS解析器这不是一个函数声明。
               +function(){}()
               -function(){}()
               !function(){}()
               ~function(){}()
               (function(){}(args))
       立即函数： 函数表达式被单独使用时立即调用。
        
     2. 【箭头函数】
         
         () => expression   直接返回表达式的值
               { 代码块 }    代码块无return 返回undefined
                            否则返回return 值
          var a = (() => expression) ();    IIFE形式
         
     3.  【函数构造函数】
     
     4.  【ES6中的构造器函数】
     
【实参】： 使用函数时传入的参数arguments
【形参】： 定义函数时使用的参数parameter

 形参 > 实参: 未送入的形参被定义成undefined
 实参 > 形参： 多余的实参不会被使用。
 
 arguments的长度是由实参决定的，而不是形参。
 
 【剩余参数】： var a = function (first, ...remain){}     ...remain = 1,2,3,4
    ES6           a(1,24,'zzj',170);                      remain = [1,2,3,4]
              剩余参数是一个数组，可以使用数组的所有方法
 
 【默认参数】： var a = function(first, age=24, name='zzj')
    ES6         
  
 【arguments】： 函数参数的别名，在非严格模式下修改两者任意都会影响到对
                方。严格模式下，修改arguments不会修改对应的参数。
           
  (arguments 是一个对象)
  
 【函数上下文和this参数】：
 
     【函数上下文】：来源于面向对象语言中的概念， 在类模板的方法中使用
                   this， this会指向与该函数关联的对象，具体对象由上 
                   下文决定，被称作上下文。   
        【上下文】：具体的使用场景。 但在JS中this的指向跟函数的调用方式
                  有很大的关系。
     【函数上下文】：this的指向
              
      1. 作为函数调用：  除方法调用、构造函数调用、 apply/call调用
            非严格模式： this 绑定为 window      
             严格模式： this 绑定为 undefined    【合理】
             
             a. 函数声明后调用
             b. 函数表达式赋予变量后调用
             c. IIFE调用
            
     2. 作为对象方法调用
      
        a.  当函数作为方法调用时，该函数的上下文成为该对象，我们可以通过
            this 指针访问宿主对象。
        b.  函数可以作为方法调用是 JavaScript 实现面向对象编程的基
            础。由于函数是【第一类对象】，不同变量是引用同一个函数又
            称为【共享】。
      
     3. 使用 new 操作符作为构造函数
      
        a. 创建一个空对象
        b. 将空对象作为函数上下文传递给构造函数
        c. 返回该对象  (若返回基本类型会被忽略，返回对象则忽略创建的对
           象)，传入的this会被丢弃。
        
        构造函数的目的： 1. 创建一个新对象，并对其进行初始化
                      2. 返回这个新对象
        
       【构造函数】：一般将其首字母大写以示和其他普通函数的区别，因为构
                   造函数作为普通函数使用会有问题。 中间涉及 this 的                    指向问题， 
                   非严格模式是window，严格下是undefined
        
        通过构造函数【优雅】创建多个相同模式的对象。
      
      4. 使用call/bind 
      
          function Button(){
              this.clicked = false;
              this.click = function(){
                 this.clicked = true;
              }
          }
          
          var button = new Button();
          ele.addEventListenter('click', button.click);

      【解释】： 我们希望click函数中绑定的this是button，在实际事件
               触发调用后this丢失了。此时需要借助【apply/call】进行
               显示邦定。
      
      【问题】： call/apply传入的是非对象时this如何绑定
      
      
      5. 箭头函数继承定义时的函数上下文， 普通函数继承调用时的上下文 
  
         【this指向】：箭头函数的上下文与其声明的地方一致，调用箭头函数
                     时不会隐式传入，而是从定义时的函数继承上下文。
         
         function Button(){
              this.clicked = false;
        
              this.click = () => {
                 this.clicked = true;
              }
          }
          var button = new Button();
          button.click调用时， this绑定的就是button对象
          
         【箭头函数作为对象字面量】： this会继承对象所在环境中的this指
                                 向
   
         6. bind ：返回一个新函数，且这个新函数返回绑定指定对象。 
                   新函数的上下文不会丢失，类似于箭头函数。
 
 【闭包】：一种机制规定了函数嵌套时内部函数发生的行为
 
    核心： 闭包允许函数访问并操作外部变量或者函数，只要变量和函数存在于声
          明函数的作用域内。
      
    解释： 在函数中声明一个内部函数时，不仅定义函数的声明，并且创建一个闭包，闭包会将函数声明时作用
          域上的变量都会被记录下来。内部函数调用时，声明的作用域消失，但是函数依然可以通过闭包返回
          访问这些变量。内部函数一直存在，则会一直保存着该作用域中的变量。
      
  【每一个通过闭包访问变量的函数都具有一个作用域链】
  
  【 
    代码执行的基础单元是函数，使用函数进行计算，使用函数更新UI，使用函数达到复用代码的目的，JS两种 
    代码：全局代码、函数代码， 每一条语句都处于特定的上下文中，上下文分为两种：全局上下文、函数上下 
    文。当函数在全局调用时，全局作用域会停止，进而将当前函数作用域压入栈并完成作用域切换。
  】
  
  【代码类型】: 全局代码、 函数代码，每一种代码类型都会创建一种执行上下文，连续的执行上下文的顺序我们又可称
              作调用栈。
 
   【词法环境】：lexical environment  JS引擎用于跟踪标识符与特定变量之间的【映射关系】。词法环 
    境是存在于上下文中：函数的词法环境是存放于内部属性[[Environment]],  
    其包含三部分：环境记录
                    EnvironmentRecord： 存放let const声明的变量和函数
                                outer： 外层引用
                          ThisBinding： 确定当前环境中的this指向
    (词法环境是作用域的内部实现机制)

    闭包保存了外部函数的词法环境的存在。
    
    环境类型： 全局环境、 函数环境、 块级作用域。
    
    编译阶段词法环境只负责声明和初始化变量，具体赋值要在代码执行阶段
       
    【核心】： JS引擎跟踪变量，并判断可访问性
       
    别名： 作用域， 作用域可以是一个函数， 一片代码， 也可以是try-catch语句。  [[Envirothmum]]， 无论何时创建函数， 都会创建一个与之相关联的词法环境，并存储在内部属性[[Environment]]
       
    【变量提升】： 变量和函数的声明只是在代码执行之前现在词法环境中进行注册。
       
    【三种变量类型】：主要在两方面不同
     
     1. 可变性：  const 不可变， 但是可以为const声明的对象添加属性
                let var 可变
     
     2. 与词法环境的关系
     
                 var： 在距离最近的函数或者全局词法环境中定义变量，不关注块级作用域。
                 
                 let 和 const：  直接在最近的词法环境中定义变量
                 
    【词法环境中注册标识符】：JS引擎代码执行分作两个阶段：
                          第一阶段：JS会访问并注册新词法环境中的变量和函数
    
 【关键字】：上下文、 词法环境、 作用域(函数作用域、 块级作用域、 全局作用域) 
```

#### 对象

```
对象： 属性名和属性值的【集合】

对象字面量 ： let obj = {
                prop1: 1,
                prop2: function(){},
                prop3: {}
            }


对象属性删除：  delete obj.propi

【继承】： 代码复用的一种方式关键在于组织代码。 JS继承方案是原型

       
【原型】:  
         1.  对象的[prototype]存放着对象指向的原型，原型指的是对象基于谁构造的。 基于构造函数则其原型是function.prototype
         2.  每个函数的原型都具有一个constructor属性，该属性指向函数本身。
         3. construct对象的原型设置为新创建对象的原型: 存放的是函数名
         
         4. 实例创建完成后，构造函数的原型被重置(赋予一个新的对象)，实例依然指向的是原来的原型对象，而新创建的对象只能引用新的原型
         
         5. 函数的属性储存在prototype上，在实例化对象时新对象将继承prototype上的属性。
         
         6. 【原型的查找】： 对象属性 - [[prototype]]查找
         
         7. 使用constructor属性可以进行类型检验
         function Ninja(){}
         const ninja = new Ninja();
         
         assert(typeof ninja === 'object', "");
         assert(ninja instanceof Ninja, "");
         assert(ninja.constructor === Ninja, "");
 
【创建原型链】：对象的原型直接是对象的实例
         subclass.prototype = new SuperClass();
         
         function Person(){
            Person.prototype.dance = function(){};
         }
         function Ninja(){}
         Ninja.prototype = new Person();
         const ninja = new Ninja();
    
    【constructor】丢失问题： 使用defineProperty方法在Ninja.prototype属性上增加新的constructor属性。
    Object.defineProperty(Ninja.property, 'constructor',{
       enumerable: false;
       value: Ninjia,
       writable: true
    })
         
    【糟糕的写法】： Ninja.prototype = Person.prototype;
         
重要：    此时ninja.[[prototype]] = Person对象， 此时Ninja旧的原型 对象未被引用， 即刻被删除。

    【instance of】： 检验右边的构造对象是否在左边对象的原型链上
    
    
【ES6中的class】: 提供了一种更优雅的创建爱你对象和事件继承的方式
         class Ninja {                function Ninja(name){
            constructor(name){             this,name = name;
              this.name = name;       }
            }                      Nijia.prototype、swing = {}
                                      let ninja = new Ninja()
            swingSword(){
               return true;
            }
            
            static compare(){}     // 静态方法
         }
         
    【静态方法】：对象实例访问不到， 类可以访问。
        class Ninja extends Person {
         
            constructor(name){
              super(name);        // 使用关键字super调用基类对象
              this.name = name;
            }
            
            swingSword(){
               return true;
            }
            
            static compare(){}     // 静态方法， 将方法作为对象属性进行添加
         }
    【ES6】继承：  
     在ES6之前： Ninja.compare， 由于方法不在prototype上因此实例对象访问不到。 
         
    添加原型的方法： Object.setPrototypeOf(对象， 原型）

【getter 和 setter 控制属性访问】：
      【需求】： 1. 避免赋错误类型的值
               2.  记录属性的变化
               
   function Ninja(){
      let skillLevel;           // 定义私有变量skillLevel
      
      this.getSkillLevel = () => skillLevel;
      
      this.setSkillLevel = value => {
         skillLevel = value;
      }
   }
   
   【两种方法】： 1 。通过对象字面量，在相应属性前加get 或者 set
                2. 通过内置Object.defineProperty()
                3. 属性名前添加get关键字定义getter方法，getter方法不接受任何参数
                4. 属性名前添加set关键字定义setter方法，setter方法接受一个参数
                5. get和set属性可以使我们将属性当作方法来访问
                6. 调用get和set方法也会创建函数上下文。
                7. get和set属性需要同时定义， 在严格模式下get和set属性缺一个会报错
                
        1. obj = {
           get name(){},
           set name(){}.
        }
        obj.name   // 获取值将隐式调用get方法
        obj.name = "" 属性赋值将隐式调用setter方法
        
【代理】： 新的对象类型Proxy实例化一个对象，其代理目标函数  ES6提出
       const emperor = {name: 'Komei'};
       const representative = new Proxy(emperor, {
         get: (target, key)=>{
            return key in target ?target[key]:undefined
         },
         set: (target, key, value) => {
            target[key] = value;
         }
       })
     representative是目标对象emperor的代理对象， 其是通过Proxy构建.Proxy构建时第一个参数是目标对象target， 第二个参数也是一个对象。
     
【代理的作用】 1. 对象操作的日志打印
                let ninja = new Ninja();
                ninja = makeLogable(ninja); // 返回一个 new Proxy(ninja, {get:(), set:()})
             2. 使用代理检测性能   new Proxy(obj, {apply: (target, thisargs, args)})
             3. 使用代理自动添加属性
             4. 使用代理实现负数组索引 
             function createNegativeArrayProxy(array){
                if(!Array.isArray(array)){
                   return new TypeError('Excepted an array');
                }
                      
                return new Proxy(array, {get:(target, index){
                      index = +index;   // 一元加性操作符将index变成数值
                      
                      return target[index<0? target.length+index:index]
                }, set:(target, index, val){});
             }
   
  【代理的结果】：
```

```
【数组】： JS中的对象

    创建数组：   字面量
               Array(length)/ Array(1,2,3)   等价调用new Array()
               new Array(length)/new Array(1,2,3)
               Array.of(elements)
               
    手动修改数组的length属性会删除多余元素。
    
    数组两端添加、删除元素：   push：数组末尾添，  返回数组长度
                           unshift： 数组开头添加， 返回数组长度
                           pop 、shift
    性能： shift 和 unshift使用后需要修改后面数组的索引会使性能有所下降
    
    数组在任意位置添加和删除：
   
    delete Array[i] :  不会将元素从数组中删除只会将元素值置为undefined， 没有做到真正的删除。
    
    Array.splice(st, num, new1, new2) 使用splice方法完成任意数据的删除和插入 (配合获取索引的参数)， 该方法返回被阐述的数组。
    
    访问超出索引之外的元素，返回undefined
    
    数组填充：  Array.prototype.fill(value) , fill函数会根据数组长度进行value值的填充
    
    数组常用操作：
                1. 遍历数组
                2. 基于现有数组元素怒映射创建新数组
                3. 验证数组元素是否匹配指定的条件
                4. 产兆特定的数组元素
                5. 聚合数组， 基于数组元素计算
       [数组遍历]：   a. for(let i =1; i<arr.length; i++)
                           缺点：考虑起始条件 长度 记步器
                    b. Array.forEach((val, index, arr) = >)
                    c. Array.map() 内部新建数组，回调函数结果会加入到新建的数组中返回
                    e. Array.every() 数组的回调结果都返回true， every返回true.
                    d。Array.some() 数组中有一项返回true， some返回true。
       b
       [数组查找] ：  a. Array.find(() => {}) 返回符合条件的第一个元素
                    b. Array.filter(()=>{}) 返回符合条件的多个
                    c. Array.indexOf(val)  获取元素索引第一次
                    d. Array.lastindexOf() 获取元素索引最后一次
                    f. Array.includes(val) 元素存在则返回true
                    
       [合计数组]： Array.reduce((tol, cur, arr)=>{}, ini)
                  // 回调函数必须返回值
          
       [复用数组方法]
                   const elements = {
                          length:0
                          add: function(elem){
                             Array.prototype.push.call(this, elem)
                 // 新的对象的添加方法利用数组的push
                          }
                   
                   }
                   
        [Array.__prpto__]:  数组的原型依然是一个数组
        
        [数组字符串化]：   arr.toString()  --->  元素使用toString并用逗号拼接起来
                         arr.join('xx')  --->  元素使用'xx'拼接起来  
 【ES6中的 Map 和 Set 】
          利用普通对象充当Map两个问题：
               1. 原型继承属性， 即在原型上存在的变量可以被访问到
               2. 对象的key值仅支持字符串。
               
           创建Map   let map = new Map();
           添加：     map.set(val, {})
           长度：     map.size
           询问：     map.has(key)
           访问：     map.get(key)  无的话是undefined
           删除：     map.delete(key)
           使用map时key是不同对象即使值相同， key值也不同
           
           遍历map ： for..of
                     for item of map   item是1*2数组 key，value
                     for key of map.keys()
                     for value of map.values()
【set】集合: 元素只能出现一次
           创建set ：  let set = new Set([])  数组初始化
              长度：    set.size
              添加：    set.add(val)
              询问：    set.has(val)
              并集：    new Set([...arr1, ...arr2]);
              遍历：    for..of
              交集：    [...set1].filter(val =>set2.has(val))
              差集：    [...set1].filter(val =>！set2.has(val))
 
```

#### 模块

```
模块的出现是为了结构化管理代码

优化程序的结构和组织的方式：将其分成小的， 耦合相对松散的片段，这些片段称
                        为模块。

模块是比对象和函数更大的代码单元，使用模块可以将程序进行归类， 并防止全局空间的污染。

目的： 【小的】、 【组织良好】的代码远比庞大的代码更容易理解和维护， 并且模块降低了理解成本， 提高了代码的【重用性】。

1， 立即执行函数
    通过立即执行函数，我们可以隐藏指定的模块执行细节。通过添加对象和闭包，我们可以定义模块接口，通过接口暴露模块功能。
    const MouseCounterModule = function(){
       let numClicks = 0;
       const handleClick = () =>{
          alert(++numClicks);
       }
       
       rerurn {
          countClicks: () =>{
             document.addEventListener("click", handleClick);
          }
       }();
    
    }

2. AMD
   AMD的设计理念明确基于浏览器
   define('MouseCounterModule',['jQuery'], $ =>{
       let numClicks = 0;
       const handleClick = () => {
          alert(++numClicks);
       };
     
     return {
       countClicks: () => {
          $(document).on("click", handleClick);
       }    
      };
    });
    [注]： AMD提供名为define的函数， 它接收以下参数
    1. 新创建模块的ID。 使用该ID， 可以在系统的其他部分引用
    2. 当前模块依赖的模块ID列表
    3. 初始化模块的工厂函数，该工厂函数接受依赖的模块列表作为参数。
    写法上与立即函数相似， AMD优点是帮助我们收集了模块的依赖，依赖模块的收集是异步加载的。


3. CommonJS
   CommonJS的设计时面向通用的JavaScript环境, 其是Node.js社区具有最多的用户。CommonJS使用基于文件的模块，每个文件中只能定义一个模块。CommonJS提供的变量module，该变量具有属性exports，通过exports很容易的扩展额外属性。 最后，module.exports作为模块的公共接口。
    1. 导入依赖 
    const $ = require("jQuery");
    let numClicks = 0;
    const handleClick = () =>{
        alert(++numClicks);
    };
    
    2. 定义公共接口
    module.exports = {
       countClicks: () => {
          $(document).on("click"， handleClick);
       }
    };
    
    在另个一文件中：
    const MouseCounterModule = require("MouseCounterModule.js")
    MouseCounterModule.countClicks();
 [注]：只有在Module.exports中的变量和接口才可以被外部访问，其最大的缺点是不显示
       地支持浏览器，浏览器端的JavaScript不支持module变量以及export属性。
       
ES6模块
   1. 与CommonJS相似， 模块是基于文件
   2. 与AMD类似， ES6模块支持异步模块加载
   3. ES6引入两个关键字： export 和 import
   const ninja = "Yoshi"
   export const message = "Hello"
   
   export function sayHiToNinja(){
      return message + " " + ninja;
   }
   
   最后一行整体导出： export {message， sayHiToNinja};
   
     另一个文件导入： import {message， sayHiToNinja} from "Ninja.js"
     导出全部标识符： import * as ninjaModule from "Ninja.js"
     模块默认导出： export default xxx,   同时可以导出其他标识符
     
  导出时设置别名：  exoprt {sayHi as sayHello}， 且只能在 export 表达式中
  设置别名，不能通过关键字 export 进行修改
   
```

#### Proxy

```javascript
[说明]： 通过对象代理获得对象的完全控制权， 对象的修改会直接反映给Proxy对象， 反之亦然。

函数调用： Proxy(target, handle)
参数说明： target is Object  ， handle is Object that recodes operator 
         methods.
   例子： let person  = {name: 'zzj', age: 24}
         let archives = new Proxy(person, {
                  get: function(target, key){
                      return target[key]
                  },
                  set: function(target, key, value){
                      target[key]  = value;
                  }
         })
handle 装载的所有方法：
             Internal Method     handle Method
           [[GetPrototypeOf]]    getPrototypeOf
           [[SetPrototypeOf]]    setPrototypeOf
            [[IsExtensible]]      isExtensible
           [[PreventExtensions]] preventExtensions
            [[GetOwnProperty]]     getOwnProperty
             [[HasProperty]]            has
                 [[Get]]                get
                 [[Set]]                set
                [[Delete]]          deleteProperty
             [[DefineOwnProperty]]  defineOwnProperty
               [[Enumerate]]           enumerate
              [[OwnPropertyKeys]]       ownKeys
                 [[Call]]                apply
               [[Construct]]            construct

  Every Proxy objects has an iternal slot called [[ProxyHandler]] ,its value is an object called the proxy's handler object,or null. Every proxy object also has an internal slot called [[ProxyTarget]] whose value is either an object or the null value. it is called the proxy's target object
  
  The [[ProxyHandler]] and [[ProxyTarget]] internal slots of a proxy object are always initialized when the object is created and typically may not be modified. 初始化时被创建， 通常不会被修改

the handle method is called to provide the implemention of proxy object internal method , handler method was passed a argument [proxy’s target object] . [注] 如果 handler object does not have method corresponding to the internal trap. 其会 invocation of corressponding internal method on the proxy's target object.

O is an ECMAScript proxy object, P is a property key value, V is any ECMAScript language value and DESC is a Property Descriptor record. 


[[GetPrototypeOf]]  --- getPrototypeOf
1. Let handler be the value of the [[ProxyHandler]] internal slot of O
2. if handler is null , throw  a TyperError exception
3. Assert:Type(handler) is Object
4. Let target be the value of the [[ProxyTarget]] internal slot of O
5. Let trap be GetMethod(handler, "getPrototypeOf")
6. ReturnIfAbrupt(trap)
7. if trapp is undefined then
     Return target[[GetPrototype]]()
8. Let handlerProto be Call(trap, handler, target)
9. ReturnIfAbrupt(handlerProto)
10.if Type(handlerProto) is neither Object or null, throw TypeError
11. Let extensibleTarget be isExtensible(target)
12. ReturnIfAbrupt(extensibleTarget)
13. if extensibleTarget is true ,return handlerProto
14. Let targetProto be target[[GetPrototypeOf]]()
15. ReturnIfAbrupt(targetProto)
16. if SameValue(handlerProto, targetProto)is false throw TyperError 
    exception
17. if SameValue(handlerProto, targetProto) is false throw TypeErroe
18. Return handlerProto 

 [[Get]]            --- get
1.Assert: IsPropertyKey(P) is true.
2.Let handler be the value of the [[ProxyHandler]] internal slot of O.
3.if handlder is null throw a TypeError
4.Assert： Type(handle) is Object
5.Let target be the value of the [[ProxyTarget]] internal slot of O
6.Let trap be GetMethod(handler, "get").
7.ReturnIfAbrupt(trap)
8.if trap is undefined then
a. Return target[[Get]](P, Receiver)
9.Let trapResult be Call(trap, handler, «target, P, Receiver»).
10.ReturnIfAbrupt(trapResult).
11.Let targetDesc be target.[[GetOwnProperty]](P).
12.ReturnIfAbrupt(targetDesc).
13.If targetDesc is not undefined, then
a.  If IsDataDescriptor(targetDesc) and targetDesc.[[Configurable]] is false 
and targetDesc.[[Writable]] is false, then
i. If SameValue(trapResult, targetDesc.[[Value]]) is false, 
    throw a TypeError exception.
    b. if IsAccessorDescriptor(targetDesc) and targetDesc.
    [[Configurable]] is false and targetDesc.[[Get]] is undefined then
    i.If trapResult is not undefined, throw a TypeError 
    exception.
    14. Return trapResult.       
```

#### Iterator

```
Iterator 【遍历】器为什么被提出
1. ES6， 又提出两种数据结构， Map 和 set， 加上原本的 Array 和 Object， 共有4种数据结构。 
   此时需要统一的接口机制访问不同的数据结构。 
2. for..of.. ，是ES6引入的， Iterator主要供其消费。

Iterator 的作用
1. 遍历器 Iterator 是一种机制，它是一种接口，为各种不同的数据结构提供统一的访问机制。任何数据结构只要部署Iterator接口，就可以完成遍历操作。 
   机制： 触发是靠遍历某种数据结构
                过程
           返回数据结构的元素
           
Iterator 的过程
1. 创建遍历器对象， 其是一个指针， 指向当前数据结构的起始位置
2. 调用指针对象上的next方法， 指针指向数据结构的第二个成员
3. 不断调用指针对象的next方法， 直到它指向数据结构的结束位置
4. next 方法会返回当前数据结构的成员信息， 返回一个包含 value 和
   done 两个属性的对象， value是的当前成员的值， done 是一个布尔值，表示遍历是否结束。
 
Iterator 的实现
  Obj.prototype[Symbol.iterator] = function() {
  var iterator = { next: next };
  var current = this;

  function next() {
    if (current) {
      var value = current.value;
      current = current.next;
      return { done: false, value: value };
    }
    return { done: true };
  }
  return iterator;
}

ES6 中的 Iterator

1. 一个数据结构只要具备 Symbol.iterator 属性，则可认为该数据及结构是可以遍历的，Symbol.iterator 本身是一个【遍历器生成函数】， 原生具备遍历器结构的数据结构：Array、Map、Set、String、 arguments、 Nodelist 对象。 
     let arr = ['a', 'b', 'c'];
     let iter = arr[Symbol.iterator]()   iter是遍历器
2. 对于可迭代的数据结构，都要将生成遍历器放在 Symbol.iterator上。

3. Array、 Map、 Set、 类数组对象、 DOM的NodeList对象、 Generator对象  
                         |
                         |
                  achieve Iterator
                         |
                         |
        for..of   ...extend grammer  [] 解构运算符   使用 Iterator 访问数据

4. 遍历器对象的 return(), throw() 方法

   return：  for..of 中途断开后， 会调用 return()方法， 可以在其中放置
             释放资源
 
5. 利用 Generator 函数去实现 Iterator 


6. for...of ： 获得键值， 而不是键
 
  1. for..of 内部调用的是 Symbol.iterator方法， 其可遍历：数组
     Map、 Set、 类数组对象、 DOM的NodeList对象、 Generator对象 
            （类数组对象特性： 对象成员有序）
  2. Map 和 Set 的遍历
     let map = new Map().set("name", "zzj").set("age", 24);
     for (let [key, value] of map){
         xxx 
     } 
```

#### Generator

```
Generator 是什么
  1. 它是【函数】， ES6 提供的一种异步编程解决方案
 
Generator 的特征
  1. function 关键字与函数名之间有一个星号
  2. 函数体内有 yield 表达式， 该关键字用于定义不同的内部状态
  3. 它返回一个【遍历器对象】，用于依次遍历 Generator 函数内部的每一个状态
  4. 调用返回的 内部状态指针对象 的 next 方法 ，指针在上一次停止的地方执行，遇到
     下一个 yield 和 return 语句为止。
  5. 暂停执行， 第一次函数调用是返回一个遍历器对象，当调用 【next方法】时函数才会开始
     执行。
     
yield 的表达式
  遍历器对象 next 方法的执行逻辑：
     1. 遇到 yield 表达式， 暂停执行后面操作， 并将紧跟 yield 后面【表达式】的值
        作为返回对象的 value 值
     2. 下一次调用 next 方法，继续往下执行，直到遇到下一个 yield 表达式
     3. 没有新的 yield 表达式，一直运行到 return 位置，将return返回值作为返回
        的对象的 value 值，若无 return 则返回的对象的 value 属性值为 undefined 
     4. yield 表达式如果用在另一个表达式之中， 必须放在圆括号里面。
           function *demo(){
            console.log('Hello' + (yield));
            console.log('Hello' + (yield 123))
           }
     5. yield 表达式用作函数参数或者放在赋值表达式的右边， 可以不加括号
           function *demo(){
              foo(yield 'a', yield 'b');
           }

与 Iterator 接口的关系
    1. Generator 函数返回遍历器对象， 因此是遍历器生成函数， 可以把Generator
       赋值给对象的 Symbol.iterator , 使得对象可迭代。对象迭代返回什么完全由
       Generator 函数中的 yield 表达式决定。
             var myIterable = {};
            myIterable[Symbol.iterator] = function* () {
              yield 1;
              yield 2;
              yield 3;
            };
            [...myIterable] // [1, 2, 3]
    2. Generator 函数执行后，返回一个遍历器对象。该对象本身也具有Symbol.iterator属
       性，执行后返回自身。

next 方法的参数
     1. yield表达式无任何返回值， 其返回一个 undefined 
     2. next 方法可以携带参数作为上一个 yield 表达式的返回值
             function* foo(x) {
                  var y = 2 * (yield (x + 1));
                  var z = yield (y / 3);
                  return (x + y + z);
                }

                var a = foo(5);
                a.next() // Object{value:6, done:false}
                a.next() // Object{value:NaN, done:false}
                a.next() // Object{value:NaN, done:true}

                var b = foo(5);
                b.next() // { value:6, done:false }
                b.next(12) // { value:8, done:false }
                b.next(13) // { value:42, done:true }
    3. V8引擎默认第一次调用 next 函数参数会忽略， 下一次 next 参数会作为上一个yield表达式的
       返回值。
                
for... of 循环
  1. for...of 循环可以自动遍历 Generator 函数运行时生成的 Iterator 对象， 且此时不再需要调用 next 方法。
            function Ficconb(){
                let [pre, cur] = [0, 1];
                yield cur;
                while(true){
                  [pre, cur] = [cur, pre + cur];
                }
            }
            
            for(let n of fibonacci()){
                if(n > 1000) break;
                console,log(n);
            }
  2. for...of 不会捕捉return语句的返回值
  
Generator函数 返回遍历器对象被其他运算符直接使用
                    Generator 函数调用
                         |
                         |
                   return Iterator 对象
                         |
                         |
    for..of 迭代对象   ...迭代对象  [x,y] (解构运算符) = 迭代对象   使用 Iterator 访问数据
  
Generator.prototype.throw()
    1. Generator 函数内部返回遍历器对象，具备一个 throw() 函数，调用该方法抛出
       的错误会在 Generator 内部捕获。
    2. 若内部没有 try-catch 语句， 则错误将被外部 try-catch 捕获
    3. throw() 方法调用前提是 Generator 函数执行过一次next()方法， 因为开始调用
       next方法程序的代码才可以开始被执行。 执行内部 try-catch 方法后会执行其后的
       yield 表达式， 即使执行完 try-catch， 后面的 yeild 语句可以被继续执行。
    4. Generator 执行过程中抛出错误，没有被内部捕获，就不会再执行下去了。如果此后还调用next方法，
       返回一个value属性等于undefined、done属性等于true的对象，即 JS 引擎认为这个                        Generator 已经运行结束了。
    5. 一个 Generator 函数只能定义一个 try-catch 块， 只能调用一次throw()方法， 下次调用则只
       会在外部捕捉。
    
Generator.prototype.return(value)
    1. 遍历器对象有一个 return 方法，返回给定的值，done 属性为true ，结束 Generator 函数运行
    2. 如果 Generator 函数内部有try...finally代码块，且正在执行try代码块，那么return()方法会导            致立刻进入finally代码块，执行完以后，整个函数才会结束。 (这与 finally 存放的逻辑有关系，会
       保证 finally 的内容执行完毕才会运行 return 语句)。
    3. return方法可以人为的结束 Generator 
 

Generator 函数作为对象属性： 
    1. let obj = {
              myGeneratorMethod: function* () {
                // ···
              }
       };
     2. let obj = {
             *myGeneratorMethod() {
             // ···
             }
         };
     以上是 Gnerator 函数作为对象属性的两种写法
     

Generator 函数的 this 值
    为什么 Generator 需要this， 一般方法和构造函数需要知道他们的调用上下文。
    
    1. Generator 函数无法作为构造函数使用， 因此无法获得内部的 this 对象。
       因为 Generator 中的 this 在不指定的情况下指向的 window 对象 
    2. 获得 this 对象的两种方法： 
           a.  function *foo(){
                    yield this.a = 1
                    yield this.b = 2
               }
               let obj = {};
               let ff = foo.call(obj);
               ff.next();   
               ff.next(); 
               consoloe.log(obj);
           //  obj = {
                   a:1
                   b:2
               }
            b.  function *foo(){
                    yield this.a = 1
                    yield this.b = 2
               }
               let ff = foo.call(foo.prototype);
               ff.next();   
               ff.next();
               consoloe.log(ff);
            // ff = {
                    a: 1
                    b: 2
               }
            b 方法实现的方式是因为， 返回的 ff 对象是 Generator 函数的实例，且其继承了 Generator
              函数的 prototype 属性
              
          c. function* gen() {
                  this.a = 1;
                  yield this.b = 2;
                  yield this.c = 3;
                }

                function F() {
                  return gen.call(gen.prototype);
                }

                var f = new F();

                f.next();  // Object {value: 2, done: false}
                f.next();  // Object {value: 3, done: false}
                f.next();  // Object {value: undefined, done: true}

                f.a // 1
                f.b // 2
                f.c // 3
      
yield* 表达式
    1. yield 表达式解决嵌套在内部的 Generator 函数需要手动在内部调用的问题 
    function *foo1(){                        function *foo1(){
      yield a=1;                                  yield a=1;
      yield b=2;                                  yield b=2;
    }                                        }

    function *foo2(){                        funciton *foo2(){   
      yield c=3;                                  yield c=3
      yield *foo1();                              let v= foo1()
      yield b=4;                                  yield foo1.next().value
    }                                             yield foo1.next().value
                                                  yield b=4
                                             }
    let f = foo2();
    console.log(f.next())
    console.log(f.next())   // 调用 foo1
    console.log(f.next())   // 调用 foo1
    console.log(f.next())
    
    function* concat(iter1, iter2) {
            yield* iter1;
            yield* iter2;
    }    
    先打印完iter1 、 再打印iter2

   2. yield* 表达式返回一个迭代器对象
      a. yield* string
      b. yield* [1,2,3]
      当调用next方法时，返回的值是‘s’、 1 而不是整个值
      
   3. 嵌套的Generator函数如果有return语句则， return的返回值需要赋值给变量从而获得
       function* foo() {
              yield 2;
              yield 3;
              return "foo";
        }
        function* bar() {
          yield 1;
          var v = yield* foo();       // 若未定义变量v则， return值不会被捕获
          console.log("v: " + v);
          yield 4;
        }
      
   4. 任何数据结构只要具有 Iterator函数接口，都可以使用 yield*遍历
   
   5. yield* 表达式解构嵌套数组
   function* iterTree(tree) {
      if (Array.isArray(tree)) {
        for(let i=0; i < tree.length; i++) {
          yield* iterTree(tree[i]);
        }
      } else{
        yield tree;
      }
   }
    const tree = [ 'a', ['b', 'c'], ['d', 'e'] ];

   a.  [...iterTree(tree)]
   
   b.  for(let x of iterTree(tree)) {
          console.log(x);
        }

Generator 状态机
     1. Generator 不需要依靠内部状态位去更替状态
    ES5状态机：                         ES6状态机:
        var clock = function(){              var clock = function *(){
           if(ticking)                           while(true){
             console.log('Tick');                  console.log('Tick');
           else                                    yield;
             console.log('Tock');                  console.log('Tock');
           ticking = !ticking;                     yield;
        }                                        }
                                             }
    2. 不需要保存外部变量ticking，【简洁】，【安全】（状态不会被非法篡改）、【符合函数式编程的思想】，        写法上【优雅】。Generator 之所以可以不用外部变量保存状态，是因为它本身就包含了一个状态信息，即
       目前是否处于暂停态。   状态1 - yield暂停 - 状态2
           

Generator 函数的上下文：
     1. Generator 函数在第一次调用时会产生一个执行上下文， 即入栈
     2. Generator 函数在遇见第一个 yield 命令时会退出当前堆栈，并冻结
        当前所有变量的值， 下次再次调用 next() 方法时上下文环境会重新加入
        栈中。
  
Generator 应用        
    
    1. 异步操作的同步化表达
    
    2. 控制流管理
    
    3. 部署 Iterator 接口
    
    4. 作为数据结构
```

#### Async

```javascript
Generator 的语法糖：  
     1. async 代替 * 声明  
     2. await 代替 yield， 执行后面 Promise 的同步部分，并阻塞后面执行， 直到 Promise 状态改变。
     3. 内置执行器， 不需要人为调用 next 执行
     4. 返回一个 Promise， 其详细状态未知
     5. 返回的 Promise 需要等内部 await 后的所有 Promise 状态改变才会发生状态改变。
     6. 一旦 await 后有一个 Promise 发生错误 ， Async 停止执行抛出错误，可被外部 catch 捕捉。
     7. 在内部使用 try-catch 语句块， 或者 Promise后跟 catch 可以阻止全局停止。

async function main() {
  try {
    const val1 = await firstStep();
    const val2 = await secondStep(val1);
    const val3 = await thirdStep(val1, val2);

    console.log('Final: ', val3);
  }
  catch (err) {
    console.error(err);
  }
}
```

#### 事件代理

```javascript
<ul id='manager'>
  <li> son1 </li>
  <li> son2 </li>
  <li> son3 </li>
  <li> son4 </li>
</ul>

<script>
  普通写法： 
        window.onload=function(){
            const ulNode = document.getElementById("list");
            const liNodes = ulNode.children;
            for(var i=0; i<liNodes.length; i++){
                liNodes[i].addEventListener('click',function(e){
                    console.log(e.target.innerHTML);
                }, false);
            }
        }
        
  事件代理：全权交给 ul 元素
        window.onload=function(){
        const ulNode=document.getElementById("list");
        ulNode.addEventListener('click', function(e) {
            /*判断目标事件是否为li*/
            if(e.target && e.target.nodeName.toUpperCase()=="LI"){
                console.log(e.target.innerHTML);
            }
        }, false);
    };
</script>

事件的常用属性：
   event.type
   event.target
   event.currentTarget
   event.bubbles
   event.eventPhase
   
document.addEventListener(‘event’, cb, options):
     1.  可以定义多个同类型事件不同的回调函数，依次执行。
     2.  在一个节点上可以定义不同类型事件的回调函数。
     3.  event.stopPropagation() 阻止当前事件的向上或者向下冒泡或者捕获
     4.  event.stopImmediatePropagation() 阻止当前及之后同类型事件的冒泡或者捕获。
```



### Effective Java

#### 函数

```
<Effective Java>

UNINT2 变量作用域：

   全局命名空间： JavaScript程序中独立的组件进行交互的唯一途径。
   
   全局命名空间在浏览器中与全局对象绑定在一起， 浏览器的window会自动添加在全局命名空间的变量作为它的属性。
   
   在LeetCode中声明全局变量不会被主动初始化导致测试会出错。
   
   【用途】：全局对象提供了全局环境的动态反应机制，可使用它查询一个运行环境，检测平台下那些特性是可用的。
   
   建议： 始终声明局部变量。在JavaScript中未被声明的变量赋值，其会被隐式转化为新的全局变量。
   
   建议： 不使用With，使用简短的变量名代替重复访问的对象。
   
   with的本意是方便对象的方法和属性进行简短的调用，但是关键在于他创建了一变量作用域(ES5称为词法环境)。 在对象作用域中引用的外部变量将会不确定，因为如果with(对象)含有这个属性，将会优先调用对象的属性而不是外部变量。
   with代码块内部是通过对象原型链进行属性查找，运行速度要比通过直接作用域查找慢。
   
   建议： 熟练掌握闭包，闭包是一种机制其作用是存储外部函数的变量引用，而不是他们的副本。
   
   [基于的三个基本原则]:  1. 可以使用函数以外定义的变量
                       2. 外部函数返回，当前函数也可以应用外部函数定义的变量。
                       3. 闭包可以更新外部变量的值
   [函数表达式帮助更快创建闭包]
   
   
   建议： 理解变量声明提升
         1. 代码块中变量的声明会被隐式般的提升到封闭函数顶部
         2. 重声明变量被视为单个变量
      
   建议： 使用立即调用的函数表达式创建局部作用域
   
   运行时进入一个作用域， JS会为每一个绑定在该作用域的变量分配一个槽， 闭包引用的是这些槽。
   
   IIFE解决JS缺少块级作用域的手段之一：
   
   var result = [];
   for(var i=0; i<=length; i++{
       (function(){
          var j =i;
          result[i] = function(){return a[j]}
       })();
   }
   return result;
   
   
   建议： 当心命名函数表达式笨拙的作用域
      匿名和命名函数的表达式官方区别在于后者会绑定到与其函数名相同的变量上，该变量名可以作为该函数内的一个局部变量。  
      
      var f = function find(tree, key){
           
         if(!tree){
             return null
         }
         
         return find(tree.left, key) || find(tree.right, key)
      }
      
      其中find的作用域只在其自身函数中，即命名函数表达式不能用该名字在外部进行调用， 利用find 作为递归调用没有必要， 因为也可以直接使用f。
      
      ES3命名函数表达式作用域表示一个对象， 该对象只有一个属性，将函数名和函数自身绑定起来。同时该作用域对象也继承Object.Prototype属性。ES5修复了这一点
      
      JavaScript环境中会提升命名函数的表达式申明，并导致命名函数表达式重复存储。
      var  f = function g(){return xx};
      var g = null;
      
  
  建议：局部块函数声明的作用域问题    【问题】： chrome执行false会报错
  
      function f() {return 'global'}
      
      function test(x){
         var result = [];
         
         if(x){
            function f(){ return "local";}  // 在块中声明函数
            result.push(f());
         }
         result.push(f());
         return result;
      }
      test(true);
      test(false);
      
      核心： 块级无作用域问题， if中的f()的作用域依然在test中， ES5将在非标准环境声明的函数报告为错误或者警告。
                   
      1. 始终将函数声明置于程序或者被包含的函数最外层
      
      2. 使用var声明和有条件的赋值语句替代有条件的函数声明。
   
   
        
  关于Eval： eval会将其参数作为js程序运行， 它会将这段代码引入到当前的作用域中当它被调用。
  
  建议： 避免使用eval函数创建的变量污染调用者的作用域， 可以使用eval进行封装。
  
  建议： 间接调用eval， 即将eval赋给一个变量， 此时eval失去访问局部作用域的能力。  或者(0, eval)(src)
  
  
UNINT3 函数

18： 函数调用、 方法调用、 构造函数之间的调用

this ： 函数行为的调用者和函数行为的接收者
函数调用将全局对象作为调用者和接收者this在非严格模式下被绑定为window， 但其实作为函数使用时不应该期望它有什么调用者和接收者。

19 熟练掌握高阶函数

  高阶函数： 将函数作为参数或者返回值的函数。
  
  学会使用高阶函数可以简化代码并消除繁琐的样板代码。 数组的遍历方法都采用的是高阶函数
  
20： 使用call方法自定义接收者来调用方法

21： 使用apply方法通过不同数量的参数调用函数

23： 永远不要修改arguments对象

function callMethod(obj, method){

   var shift = [].shift;
   shift.call(arguments);     移除第一个元素
   shift.call(arguments);     移除第二个元素
   return obj[method].apply(obj, arguments);
}
此时 obj=arguments[0]  //  此时的arguments[0]是arguments[2]

24: 使用变量保存arguments的引用

当嵌套函数要使用外层函数的arguments时要将外层函数的arguments用变量保留下来。

25： 使用bind方法提取具有确定接受者的方法

26： 使用bind方法实现函数柯里化。

27： 使用闭包而不是字符串来封装代码

    核心： 使用闭包保证代码访问的是局部变量而非全局变量
    建议： 当将字符串传递给eval函数以执行他们的API时，绝不要在字符串中包含局部变量的引用。
    
28：  不要信赖函数对象的toString方法
   
      JS的函数可以利用toString方法将其源代码转为字符串。但是一些内置函数由于宿主环境只提供编译后的结果因此无法展现源代码。第二就是toString方法并不展示保存的与内部变量有关的引用值。
```

#### 对象



## 图片

![img](https://pic1.zhimg.com/80/v2-b1b091876097dca10f8f7adb1b6109f5_720w.jpg?source=1940ef5c)

![字符串函数](https://pic2.zhimg.com/80/v2-37e019253da89667d996e60e514bafab_720w.jpg?source=1940ef5c)

![数组](https://pic1.zhimg.com/v2-c3ec2351846c4c19fda32536f386ca34_r.jpg?source=1940ef5c)

![JS运算符](https://pic1.zhimg.com/80/v2-85755e1a96e018365c18ae831de35e92_720w.jpg?source=1940ef5c)




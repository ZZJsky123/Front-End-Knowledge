## Node

### 核心

```
1. 异步
2. 事件驱动
3. 非阻塞
4. 性能优良
```

### 定义

```
1. 定义： Node.js 与浏览器一致是 JavaScript 的运行环境， 其为我们提供无需依赖浏览器， 可以直接与操作系统交互的 Js 环境。

2. 两种执行方式：
    a. REPL： Read Eval Print Loop ： 读取-执行-打印-循环
    b. 代码写入Js文件， 并用 Node 执行。  
       i. Node xxx.js
  
    第一种方式 ： 直接 cmd 输入 Node 指令， 进入 Node 环境，可直接写 JS 代码并运行。
```



### Node 全局对象

```
1. process ：Node 的灵魂
     a. 管理当前 Node.js 进程状态的对象
     b. 提供与操作系统的简单接口
     c. 常用属性：
         i.  pd:  进程编号
        ii. env: 系统环境变量
       iii. argv: 命令行执行此脚本时的输入参数
        IV. platform: 当前操作系统平台
        
2. Buffer： 二进制文件处理

3. __dirname  : 当前运行脚本的目录路径

4. __filename : 当前运行脚本的文件路径
```

### Node 模块机制

```
1. 模块机制： 从外部导入模块， 模块之间也可以在导入区域互相访问。

2. Node 模块机制分类：
   a. 核心模块： Node 内置模块 ，二进制可执行文件
      
   b. 文件模块： 用户编写的模块。 
      注： 此模块可以是文件， 也可以是目录， Node 可以通过目录中的 package.json 文件将其中 main 字段指
          向的文件作为模块入口文件。
          
3. Node 模块机制浅析       common.js 规范
   a. require: 导入模块
      i. 按照模块名称：  const os = require('os')
     ii. 按照相对路径：  const os = require('./os')
    iii. 按照绝对路径
    
   b. exports： 导出模块
     i, 通过将导出内容加入到 exports 的对象中完成导出
    ii. 导出方式：
          (1). export.add = function(){};
          (2). const ｛ add ｝ = require('./myModule')  用解构的方式优雅的导入 add 模块
   
   c. module
       i. id
       ii. exports： exports 是 module.exports 的引用
       iii.parent & children
       IV. loaded
       v.  paths
```



### npm

```
1. npm -v       // npm 版本号
2. npm init    // npm 相关信息初始化 完成后创建 package.json 文件
                   其中字段： dependencies 记录项目的直接依赖
3. npm install 
   a. npm install xx --save-dev  : 开发时依赖项，项目发布或者部署不需要
   b. npm install xx -D          : 同上

4.package.json 的 scripts 脚本 : 该字段定义了全部的 npm scripts
  a. npm scripts 的分类：
         i.  预定义脚本 ： test、 start、 install、 publish。 直接通过运行 npm xx
         ii. 自定义脚本 ： npm run xx 进行运行
         
  b. npm 会将开发时依赖添加到 dependecies字段中， 并分别添加 start 、 lint 脚本
         
   
```

### 监听



## Express 框架

### 核心

```
1. 路由： express.Router()  // 生成一个路由实例

2. 中间件

3. 模板引擎
```

### Express 封装HTTP

```
1. 传统直接利用 http 模块构建后端服务器

const http = require('http');

const hostname = 'localhost';
const port = 3000;

const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader('Content-Type', 'text/html');
  res.end('Hello World\n');
});

server.listen(port, () => {
  console.log(`Server running at http://${hostname}:${port}/`);
});
 
 将上述脚本写入到 txt 文档中， 并修改后缀名为 Js ， 即可使用 node 运行。


2. 缺点： 
     a. 手写底层代码
     b. 缺少路由机制


3. Express 封装HTTP
   a.  Request & Response
    i. Response 一般用 req 表示
        •req.body：   客户端请求体的数据，可能是表单或 JSON 数据
        •req.params： 请求 URI 中的路径参数
        •req.query：  请求 URI 中的查询参数
        •req.cookies：客户端的 cookies
    ii. Response 一般用 res 表示
        // 发送一串 HTML 代码
        res.send('HTML String');

        // 发送一个文件
        res.sendFile('file.zip');

        // 渲染一个模板引擎并发送
        res.render('index');
   iii. 
     路由： 服务器根据客户端请求的端点(URI + http 方法)选择相应的处理逻辑。
     app.METHOD(PATH, HANDLER);
       •app 就是一个 express 服务器对象
       •METHOD 可以是任何小写的 HTTP 请求方法，包括 get、post、put、delete 等等
       •PATH 是客户端访问的 URI，例如 / 或 /about
       •HANDLER 是路由被触发时的回调函数，在函数中可以执行相应的业务逻辑
```

### 中间件

```
1. 中间件是中间执行过程的必要环节， 其按照顺序执行。
2. 在 Express 中，中间件就是一个函数：
         function someMiddleware(req, res, next){
         
         }
3. 全局中间件
   a. 通过 app.use 函数就可以注册中间件，并且此中间件会在用户发起任何请求都可能会执行，例如：
      app.use(someMiddleware);
   
4. 路由中间件

  a, 通过在路由定义时注册中间件，此中间件只会在用户访问该路由对应的 URI 时执行，例如：
        app.get('/middleware', someMiddleware, (req, res) => {
        res.send('Hello World');
        });
     那么用户只有在访问 /middleware 时，定义的 someMiddleware 中间件才会被触发，访问其他路径时不会触发

```


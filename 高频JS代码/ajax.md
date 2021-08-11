## Ajax

```javascript
function get(url,callback){
    
    if (window.XMLHttpRequest){
        const xhr = new XMLHttpRequest()
    }else{
        const xhr = ActiveObject('Microsoft.XMLHTTP')
    }
    
    
    xhr.onreadystatechange = function(){
        if (xhr.readystate === 4){
            if (xhr.status ===200 || xhr.status ===304){
                callback(xhr.responseText)
            }else{
                alert("Your browser does not support XMLHTTP.");
            }
        }
    }
    
    xhr.open('get',url)
    xhr.send()
}
```

```javascript
function post(url,data,callback){
   let xhr
   if (windows.XMLHttpRequest){
        xhr = new XMLHttpRequest()
   }else{
        xhr = ActiveObject("Microsoft.XMLHTTP")
   }
   
   xhr.open('POST',url,true)
   
   xhr.setRequestHeader('Content-Type':"application/x-www-form-urlencoded")
   
   xhr.onreadystatechange = function(){
      if (xhr.readyState === 4 && xhr.status === 200 || xhr.status ===304){
         callback(response)
      }
   }
   xhr.send(data)
}
```



```
知识点：
   Ajax是什么：JS异步通信，向服务器端发送请求获取相应数据并对网页特定部分进行更新，而不用刷新整个网页。
   Ajax步骤： 创建XMLHttpRequest对象
             发送Http请求
             服务器返回XML格式字符串    (XML暂时不用，而使用JSON)
             JS解析XML，并更新局部页面
   请求建立：xhr.open()  // 接受5个参数
       method:'GET','POST','PUT','HEAD'
          url
        async: bool值，默认异步true
         user: 用于认证的用户名，默认为空
        password: 认证的密码，默认为空
             
   请求状态判断： xhr.readyState
         0:  尚未调用open
         1:  已经调用open初始化请求，尚未发送即调用send
         2:  已经发送请求
         3:  已经收到请求返回的数据
         4:  请求已经完成
   响应状态： xhr.status
   监听函数： xhr.onreadystatechange
   返回数据： xhr.responseText
   请求响应时间： xhr.timeout
   
   设置HTTP头： xhr.setRequestHeader('参数1'，'参数2')
          参数1： 字符串，请求报文的头字段
          参数2： 参数1对应的值
          (注： 必须调用在send前，open后)
   获取HTTP响应头： xhr.getRequestHeader
   
   

```

## Ajax Level 2

```
 Ajax Level 2 
 
 1. 增加 cors 机制
 
 2. 增加请求过程信息
 
 3. 设置HTTP请求时限
 
 4. 可以上传文件/ 上传和下载二进制文件
 
 5. 使用 FromeData 对象管理表单数据
 
 a. 若是跨越请求， 浏览器自动增加 Origin 字段
 
 b. xhr.timeout = 3000ms  设置请求时限，规定时间内未完成请求调用 xhr.ontimeout 回调函数
 
 c. 增加请求过程信息：
            I. xhr.onerror :  传输过程出错回调
            II. xhr.loadStart: 传输过程开始回调
            III.xhr.load:  传输过程完成回调
            IV. xhr.abort: 传输被用户取消
            V.  xhr.loadEnd: 传输完成但不知道具体是否成功
            
            xhr.onprogress:  下载过程的回调事件
            xhr.upload.onprogress:  上传过程的回调事件
            
 d. FromData 对象
             I. let formdata = new FormData()   新建一个 formdata 对象
             
             II. formdata.append('列名',  data)；
             
             III. xhr.send(formdata);    直接发送表单
             
             IV. new FormData(表单元素)    会将该表单元素转换为 FormData 对象
```


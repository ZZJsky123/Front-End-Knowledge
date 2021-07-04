## ajax

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
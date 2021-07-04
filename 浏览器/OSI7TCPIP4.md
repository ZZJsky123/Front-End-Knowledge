

![img](https://images2015.cnblogs.com/blog/927608/201607/927608-20160704203635124-1548160057.jpg)

> OSI： open system Interconnect  开放国际互联系统，规划出网络模型中端到端信息上行和下行的过程
>
> OSI模型提出了： 服务、接口、协议、分层
>
> OSI 模型是先建立起层级，规划好服务，之后再由服务为每一层引入相应协议。
>
> TCP/IP： 是协议簇，其仿照OSI模型，按照其协议的不同功能建立起5层和四层模型。



![img](https://img-blog.csdn.net/20180411120702438?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5NTIxNTU0/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)



![image-20210503100427692](C:\Users\Sky\AppData\Roaming\Typora\typora-user-images\image-20210503100427692.png)



![img](https://img-blog.csdn.net/2018041112053246?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5NTIxNTU0/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)



> 总结： 计算机网络是一个由人构造的世界，这里的核心： 1.物理连接层：光纤、电缆  2. 协议：交流准则。 
>
> 这里面的主体是： 1. 应用软件  2. 数据上传和下行设备  3. 路由 。  交流方法：  1. 先建立沟通通道(会话层-传输层-网络层-物理层)  2. 核心信息传递（应用层）



## 计算网络体系

![OSI模型](D:\计算机\A_书籍\面试\计算机网络图\OSI模型.jpg)

![image-20210517142152741](C:\Users\Sky\AppData\Roaming\Typora\typora-user-images\image-20210517142152741.png)

#### 物理层

> ```
> 物理层传输的基本单位是【比特流】，即0和1，这些比特数据被转换成【电信号】和【光信号】在物理介质层中传输。
> ```

#### 数据链路层

> ```
> 数据链路层传输的基本单位是【帧】，比特组合成字节、字节再组合成帧，使用链路层地址或者MAC地址(以太网)访问介质，并为网络层提供【差错控制】和【流量服务控制】
> 
> 数据链路层
>   MAC(介质访问控制子层)：规定如何在物理线路上传输帧(与物理层相连)
>   LLC(逻辑链路控制子层): 识别不同协议类型，并对其进行封装(与网络层对接)
> 
> ```
>
> #### 网络层
>
> ```
> 网络层传输的基本单位是【数据包】，提供IP地址，负责把数据包从源网络传输到目标网络的路由。
> 
> IP协议：提供不可靠、无连接的传送服务
> ```

#### 传输层

> ```
> 传输层基本单位是【段】，提供面向连接/无连接的数据传递，以及重传之前的差错检验。
> ```

#### 会话层

> ```
> 负责实体之间的通信会话的：建立、管理、终止
> 
> 该层的通信由不同设备中的应用程序间服务的【请求】和【响应】组成。
> ```

#### 表示层

> ```
> 负责应用层数据的编码/转换功能， 确保数据可以被目的主机的应用层识别。
> ```
>
> ![image-20210517141910375](C:\Users\Sky\AppData\Roaming\Typora\typora-user-images\image-20210517141910375.png)

#### 应用层

> ```
> 负责向应用程序提供网络服务
> ```
>
> ![image-20210517142017076](C:\Users\Sky\AppData\Roaming\Typora\typora-user-images\image-20210517142017076.png)


### 题目列表

1. HTTP协议包括哪些请求?
2. HTTP中GET和POST的区别?



#### 1. HTTP协议包括哪些请求?

- GET 对服务器资源的简单请求
- POST 用于发送包含用户提交数据的请求.
- PUT: 传说中请求文档的一个版本
- DELETE: 发出一个删除指定文档的请求.

以及

- HEAD: 类似于GET请求，不过返回的响应中没有具体内容，用于获取报头
- TRACE：发送一个请求副本，以跟踪其处理进程
- OPTIONS：返回所有可用的方法，检查服务器支持哪些方法
- CONNECT：用于ssl隧道的基于代理的请求

#### 2. HTTP中GET和POST的区别?

从原理上来看:

- 根据HTTP规范，GET用于信息获取，而且应该是安全和幂等的
- 根据HTTP规范，POST请求表示可能修改服务器上资源的请求

从表面上看:

- GET请求的数据会附在URL后面，POST的数据放在HTTP包体
- POST安全性比GET安全性高







HTTP HTTPS HTTP2 
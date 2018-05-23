# 剖析Web
万维网基本架构
* HTTP

    规定了网络客户端和服务器之间如何交换请求和响应
* HTML

    结果的展示格式
* URL

    唯一表示服务器和服务器上资源的方法

简单场景，通过HTTP连接到一个web客户端，请求一个URL，收到HTML。

## Web客户端
HTTP是Web数据交换的标准协议，Web是一个客户端-服务器系统。客户端向服务器发起请求：他会创建一个TCP/IP链接，通过HTTP发送URL和其他信息并接受一个响应。，响应的格式也由HTTP定义。

HTTP重要的一个概念是无状态。
## 使用telent进行测试。
pass
## Python的标准Web库
Python3 将web模块打包成两个包
* http会处理所有客户端-服务器HTTP请求的具体细节

1.client会处理客户端部分

2.server会协助编写Python Web服务器程序

3.cookies和cookiejar会处理cookie，cookie可以在请求中存储数据

* urllib 是基于http的高层库：

1.request处理客户端请求

2.response处理服务端响应

3.parse会解析URL

* request模块（重要）
## Web服务端
* web服务器网关接口，WSGI是一个通用的API，连接Python Web应用和Web服务器。
* 框架，框架具备：路由，模版，认证和授权，Session
* bottle模块（重要）
* Flask模块（重要）
* 其他框架：django,web2py,pyramid,turbogears

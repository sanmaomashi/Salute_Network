# HTTP协议和静态web服务器

## 一、HTTP 协议

### 1. 介绍

HTTP 协议的全称是(HyperText Transfer Protocol)，翻译过来就是**超文本传输协议**。

超文本是超级文本的缩写，是指超越文本限制或者超链接，比如:图片、音乐、视频、超链接等等都属于超文本。

HTTP 协议的制作者是**蒂姆·伯纳斯-李**，1991年设计出来的，**HTTP 协议设计之前目的是传输网页数据的，现在允许传输任意类型的数据**。

**传输 HTTP 协议格式的数据是基于 TCP 传输协议的，发送数据之前需要先建立连接。**

### 2. HTTP 协议的作用

它**规定了浏览器和 Web 服务器通信数据的格式，也就是说浏览器和web服务器通信需要使用http协议**。

### 3. 浏览器访问web服务器的通信过程



## 二、URL

### 1. URL的概念

URL的英文全拼是(Uniform Resoure Locator),表达的意思是统一资源定位符，通俗理解就是网络资源地址，也就是我们常说的网址。

### 2. URL的组成

**URL的样子:**

https://news.163.com/18/1122/10/E178J2O4000189FH.html

**URL的组成部分:**

1. **协议部分**: https://、http://、ftp://
2. **域名部分**: news.163.com
3. **资源路径部分**: /18/1122/10/E178J2O4000189FH.html

**域名:**

域名就是**IP地址的别名**，它是用点进行分割使用英文字母和数字组成的名字，**使用域名目的就是方便的记住某台主机IP地址**。

**URL的扩展:**

https://news.163.com/hello.html?page=1&count=10

- **查询参数部分**: ?page=1&count=10

**参数说明:**

- ? 后面的 page 表示第一个参数，后面的参数都使用 & 进行连接

## 三、查看HTTP协议的通信过程

### 1. 谷歌浏览器开发者工具的使用

首先需要安装Google Chrome浏览器，然后Windows和Linux平台按**F12**调出开发者工具, mac OS选择 视图 -> 开发者 -> 开发者工具或者直接使用 **alt+command+i** 这个快捷键，还有一个多平台通用的操作就是在**网页右击选择检查**。

**开发者工具的效果图:**

![标签说明](imgs/通信过程-1.png)

**开发者工具的标签选项说明:**

- 元素（Elements）：用于查看或修改HTML标签
- 控制台（Console）：执行js代码
- 源代码（Sources）：查看静态资源文件，断点调试JS代码
- 网络（Network）：查看http协议的通信过程

**开发者工具使用效果图:**

![使用说明](imgs/通信过程-2.png)

**开发者工具的使用说明:**

1. 点击Network标签选项
2. 在浏览器的地址栏输入百度的网址，就能看到请求百度首页的http的通信过程
3. **这里的每项记录都是请求+响应的一次过程**

### 2. 查看HTTP协议的通信过程

**查看http请求信息效果图:**

![查看http请求信息](imgs/通信过程-3.png) ![查看http请求信息](imgs/通信过程-4.png)

**查看http响应信息效果图:**

![查看http请求信息](imgs/通信过程-5.png) ![查看http请求信息](imgs/通信过程-6.png)



## 四、HTTP 请求报文

### 1. HTTP 请求报文介绍

**HTTP最常见的请求报文有两种:**

1. GET 方式的请求报文
2. POST 方式的请求报文

**说明:**

- GET: 获取web服务器数据
- POST: 向web服务器提交数据

### 2. HTTP GET 请求报文分析

**HTTP GET 请求报文效果图:**

![GET请求报文分析](imgs/get请求报文分析.png)

**GET 请求报文说明:**

```http
---- 请求行 ----
GET / HTTP/1.1  # GET请求方式 请求资源路径 HTTP协议版本
---- 请求头 -----
Host: www.itcast.cn  # 服务器的主机地址和端口号,默认是80
Connection: keep-alive # 和服务端保持长连接
Upgrade-Insecure-Requests: 1 # 让浏览器升级不安全请求，使用https请求
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/69.0.3497.100 Safari/537.36  # 用户代理，也就是客户端的名称
Accept:text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8 # 可接受的数据类型
Accept-Encoding: gzip, deflate # 可接受的压缩格式
Accept-Language: zh-CN,zh;q=0.9 #可接受的语言
Cookie: pgv_pvi=1246921728; # 登录用户的身份标识

---- 空行 ----
```

**GET 请求原始报文说明:**

```http
GET / HTTP/1.1\r\n
Host: www.itcast.cn\r\n  
Connection: keep-alive\r\n
Upgrade-Insecure-Requests: 1\r\n
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/69.0.3497.100 Safari/537.36\r\n
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8\r\n
Accept-Encoding: gzip, deflate\r\n
Accept-Language: zh-CN,zh;q=0.9\r\n
Cookie: pgv_pvi=1246921728; \r\n
\r\n  (请求头信息后面还有一个单独的’\r\n’不能省略)
```

**说明：**

- 每项数据之间使用:**\r\n**

### 3. HTTP POST 请求报文分析

**HTTP POST 请求报文效果图:**

![GET请求报文分析](imgs/post请求报文分析.png)

**请求体效果图:**

![GET请求报文分析](imgs/post请求报文分析-1.png)

**POST 请求报文说明:**

```http
---- 请求行 ----
POST /xmweb?host=mail.itcast.cn&_t=1542884567319 HTTP/1.1 # POST请求方式 请求资源路径 HTTP协议版本
---- 请求头 ----
Host: mail.itcast.cn # 服务器的主机地址和端口号,默认是80
Connection: keep-alive # 和服务端保持长连接
Content-Type: application/x-www-form-urlencoded  # 告诉服务端请求的数据类型
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/69.0.3497.100 Safari/537.36 # 客户端的名称
---- 空行 ----
---- 请求体 ----
username=hello&pass=hello # 请求参数
```

**POST 请求原始报文说明:**

```http
POST /xmweb?host=mail.itcast.cn&_t=1542884567319 HTTP/1.1\r\n
Host: mail.itcast.cn\r\n
Connection: keep-alive\r\n
Content-Type: application/x-www-form-urlencoded\r\n
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/69.0.3497.100 Safari/537.36\r\n
\r\n(请求头信息后面还有一个单独的’\r\n’不能省略)
username=hello&pass=hello
```

**说明：**

- 每项数据之间使用:**\r\n**

### 4. 小结

- 一个HTTP请求报文可以由**请求行、请求头、空行和请求体**4个部分组成。
- 请求行是由三部分组成:
  1. **请求方式**
  2. **请求资源路径**
  3. **HTTP协议版本**
- **GET方式的请求报文没有请求体，只有请求行、请求头、空行组成**。
- **POST方式的请求报文可以有请求行、请求头、空行、请求体四部分组成，注意:POST方式可以允许没有请求体，但是这种格式很少见**。

**GET和POST请求对比效果图:**

![GGET和POST请求报文对比](imgs/get和post请求报文.png)



## 五、HTTP响应报文

### 1. HTTP响应报文分析

**HTTP 响应报文效果图:**

![HTTP 响应报文](imgs/响应报文-1.png)
![HTTP 响应报文](imgs/响应报文-2.png)

**响应报文说明:**

```http
--- 响应行/状态行 ---
HTTP/1.1 200 OK # HTTP协议版本 状态码 状态描述
--- 响应头 ---
Server: Tengine # 服务器名称
Content-Type: text/html; charset=UTF-8 # 内容类型
Transfer-Encoding: chunked # 发送给客户端内容不确定内容长度，发送结束的标记是0\r\n, Content-Length表示服务端确定发送给客户端的内容大小，但是二者只能用其一。
Connection: keep-alive # 和客户端保持长连接
Date: Fri, 23 Nov 2018 02:01:05 GMT # 服务端的响应时间
--- 空行 ---
--- 响应体 ---
<!DOCTYPE html><html lang=“en”> …</html> # 响应给客户端的数据
```

**原始响应报文说明:**

```http
HTTP/1.1 200 OK\r\n
Server: Tengine\r\n
Content-Type: text/html; charset=UTF-8\r\n
Transfer-Encoding: chunked\r\n
Connection: keep-alive\r\n
Date: Fri, 23 Nov 2018 02:01:05 GMT\r\n
\r\n(响应头信息后面还有一个单独的’\r\n’不能省略)
<!DOCTYPE html><html lang=“en”> …</html>
```

**说明:**

每项数据之间使用:**\r\n**

### 2. HTTP 状态码介绍

HTTP 状态码是**用于表示web服务器响应状态的3位数字代码**。

| 状态码 | 说明                             |
| :----- | :------------------------------- |
| 200    | 请求成功                         |
| 307    | 重定向                           |
| 400    | 错误的请求，请求地址或者参数有误 |
| 404    | 请求资源在服务器不存在           |
| 500    | 服务器内部源代码出现错误         |

### 3. 小结

- 一个HTTP响应报文是由**响应行、响应头、空行和响应体**4个部分组成。 ![HTTP 响应报文](imgs/响应报文.png)
- 响应行是由三部分组成：**HTTP协议版本 状态码 状态描述**，最常见的状态码是200

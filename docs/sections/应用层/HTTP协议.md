# HTTP协议

## 一、概述

### 1. 介绍

`HTTP协议`（HyperText Transfer Protocol，超文本传输协议）是一种用于传输Web页面、图像、音频、视频和其他文件的协议。它是一种客户端-服务器协议，客户端通过发送HTTP请求从Web服务器获取数据，服务器通过发送HTTP响应来回复请求。

HTTP是基于TCP/IP协议栈的应用层协议。它使用URL（统一资源定位符）来定位Web资源，并使用各种HTTP方法（如GET、POST、PUT、DELETE等）来操作这些资源。

HTTP协议是一种明文协议，因此，它的请求和响应都以明文形式传输，容易被窃听和篡改。这种不安全性在一定程度上限制了HTTP协议的应用场景。

### 2. 作用

它**规定了浏览器和 Web 服务器通信数据的格式，也就是说浏览器和web服务器通信需要使用http协议**。

HTTP 的作用包括：

1. 传输数据：HTTP 协议允许客户端向服务器请求数据，并允许服务器向客户端传输数据。这使得 Web 应用程序可以通过网络传输数据，包括文本、图像、音频和视频等不同类型的文件。
2. 定位资源：HTTP 协议使用 URL（Uniform Resource Locator）来定位网络资源。URL 是一个用于指定 Web 上资源位置的字符串，可以包括协议类型、服务器名称、端口号、路径和查询参数等信息。
3. 交互性：HTTP 协议允许客户端和服务器之间进行交互式通信。客户端可以向服务器发送请求并接收响应，服务器可以向客户端发送信息，这使得 Web 应用程序可以提供交互式的用户体验。
4. 状态管理：HTTP 协议使用 Cookie 和 Session 来管理客户端的状态。Cookie 是一个小的文本文件，存储在客户端浏览器中，用于跟踪用户的行为和状态。Session 是在服务器上创建的一个对象，用于存储客户端状态信息，包括登录状态、购物车内容等。

总之，HTTP 协议在 Web 应用程序的开发和实现中起着非常重要的作用，它定义了客户端和服务器之间的通信规则，使得 Web 应用程序可以在网络上传输数据，并提供交互式的用户体验。

### 3. 通信过程

HTTP协议通信的基本过程：

1. 建立连接：客户端向服务器发起请求，连接到服务器的端口上。通常使用TCP连接建立，客户端通过三次握手来建立连接。
2. 发送请求：客户端向服务器发送一个请求消息。请求消息通常包括一个方法、一个资源标识符和一个HTTP版本号。
3. 接收请求：服务器接收客户端的请求消息并进行解析。服务器需要检查请求消息的合法性，并决定如何处理请求消息。
4. 处理请求：服务器处理请求消息，并生成一个响应消息。服务器处理请求的过程包括访问数据库、执行应用程序逻辑等等。
5. 发送响应：服务器向客户端发送一个响应消息。响应消息通常包括一个HTTP版本号、一个状态码和一些描述状态的信息。
6. 接收响应：客户端接收服务器发送的响应消息，并进行解析。客户端需要检查响应消息的合法性，并决定如何处理响应消息。
7. 处理响应：客户端处理响应消息，并根据需要执行一些操作，例如更新界面、保存数据等等。
8. 关闭连接：通信完成后，客户端和服务器都可以选择关闭连接，释放资源。

以上是HTTP协议通信的基本过程，其中客户端和服务器之间可以进行多次请求和响应。在实际应用中，还会涉及到缓存、cookie、认证等机制，以及HTTPS加密等功能。

### 4. URL

URL是“统一资源定位符”的缩写。它是用于唯一标识互联网上的资源的字符串。资源可以是网页、图片、视频、文档或任何其他类型的文件。

一个URL由三个部分组成：

1. **协议**：表示资源使用的协议，如HTTP、HTTPS、FTP等。
2. **主机**：表示资源所在的主机或服务器的名称或IP地址。
3. **路径**：表示资源在服务器上的位置或路径。

例如，以下是一个URL：

```http
https://www.example.com/index.html
```

其中，“https”是协议，“www.example.com”是主机，“/index.html”是路径。

#### 4.1 如何创建URL

要创建URL，您需要确定您要访问的资源的协议、主机和路径。然后，将这些部分组合在一起，用冒号和正斜杠分隔协议和主机，用正斜杠分隔主机和路径。

例如，如果您要创建一个指向图片文件的URL，该文件位于名为“images”的文件夹中，您的网站的主机名为“www.example.com”，则可以创建以下URL：

```html
https://www.example.com/images/myimage.jpg
```

#### 4.2 如何使用URL

要使用URL，只需在浏览器的地址栏中输入URL并按下Enter键即可访问资源。您也可以在HTML代码中使用URL来引用其他网页、图片或其他资源。

例如，在HTML代码中，您可以使用以下代码将图像插入网页：

```html
<img src="https://www.example.com/images/myimage.jpg">
```

此代码会将名为“myimage.jpg”的图像文件从名为“images”的文件夹中检索，并在网页上显示它。

## 二、HTTP请求

HTTP最常见的请求报文有两种:

1. GET 方式的请求报文（获取web服务器数据），GET请求参数显示，都显示在浏览器网址上，HTTP服务器根据该请求所包含URL中的参数来产生响应内容，即“Get”请求的参数是URL的一部分。 例如： `http://www.baidu.com/s?wd=Chinese`
2. POST 方式的请求报文（向web服务器提交数据），POST请求参数在请求体当中，消息长度没有限制而且以隐式的方式进行发送，通常用来向HTTP服务器提交量比较大的数据（比如请求中包含许多参数或者文件上传操作等），请求的参数包含在“Content-Type”消息头里，指明该消息体的媒体类型和编码

**注意：避免使用Get方式提交表单，因为有可能会导致安全问题。 比如说在登陆表单中用Get方式，用户输入的用户名和密码将在地址栏中暴露无遗。**

### 1. HTTP GET 请求报文

HTTP GET请求报文通常由两部分组成：请求行和消息头。请求报文通常不包含请求体，因为GET方法是用于获取资源，而不是提交数据。

一个典型的HTTP请求示例

```http
GET https://www.baidu.com/ HTTP/1.1
Host: www.baidu.com
Connection: keep-alive
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/54.0.2840.99 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Referer: http://www.baidu.com/
Accept-Encoding: gzip, deflate, sdch, br
Accept-Language: zh-CN,zh;q=0.8,en;q=0.6
Cookie: BAIDUID=04E4001F34EA74AD4601512DD3C41A7B:FG=1; BIDUPSID=04E4001F34EA74AD4601512DD3C41A7B; PSTM=1470329258; MCITY=-343%3A340%3A; BDUSS=nF0MVFiMTVLcUh-Q2MxQ0M3STZGQUZ4N2hBa1FFRkIzUDI3QlBCZjg5cFdOd1pZQVFBQUFBJCQAAAAAAAAAAAEAAADpLvgG0KGyvLrcyfrG-AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAFaq3ldWqt5XN; H_PS_PSSID=1447_18240_21105_21386_21454_21409_21554; BD_UPN=12314753; sug=3; sugstore=0; ORIGIN=0; bdime=0; H_PS_645EC=7e2ad3QHl181NSPbFbd7PRUCE1LlufzxrcFmwYin0E6b%2BW8bbTMKHZbDP0g; BDSVRTM=0
```

#### 1.1 请求行

请求行包括请求方法、请求的URL和HTTP协议版本，格式如下：

```http
GET https://www.baidu.com/ HTTP/1.1
```

其中，"GET"是HTTP请求方法，"https://www.baidu.com/"是请求的资源路径，"HTTP/1.1"是使用的HTTP协议版本。

> 请求方法

根据HTTP标准，HTTP请求可以使用多种请求方法。

HTTP 0.9：只有基本的文本 GET 功能。

HTTP 1.0：完善的请求/响应模型，并将协议补充完整，定义了三种请求方法： GET, POST 和 HEAD方法。

HTTP 1.1：在 1.0 基础上进行更新，新增了五种请求方法：OPTIONS, PUT, DELETE, TRACE 和 CONNECT 方法。

HTTP 2.0（未普及）：请求/响应首部的定义基本没有改变，只是所有首部键必须全部小写，而且请求行要独立为 :method、:scheme、:host、:path这些键值对。

| 序号 | 方法    | 描述                                                         |
| ---- | ------- | ------------------------------------------------------------ |
| 1    | GET     | 请求指定的页面信息，并返回实体主体。                         |
| 2    | HEAD    | 类似于get请求，只不过返回的响应中没有具体的内容，用于获取报头 |
| 3    | POST    | 向指定资源提交数据进行处理请求（例如提交表单或者上传文件），数据被包含在请求体中。POST请求可能会导致新的资源的建立和/或已有资源的修改。 |
| 4    | PUT     | 从客户端向服务器传送的数据取代指定的文档的内容。             |
| 5    | DELETE  | 请求服务器删除指定的页面。                                   |
| 6    | CONNECT | HTTP/1.1协议中预留给能够将连接改为管道方式的代理服务器。     |
| 7    | OPTIONS | 允许客户端查看服务器的性能。                                 |
| 8    | TRACE   | 回显服务器收到的请求，主要用于测试或诊断。                   |

#### 1.2 消息头

消息头包括了请求的一些元数据信息，例如请求的主机名、浏览器信息、Cookie等。

##### 1.2.1 Host 

Host：对应网址URL中的Web名称和端口号，用于指定被请求资源的Internet主机和端口号，通常属于URL的一部分。

##### 1.2.2 Connection

Connection：表示客户端与服务连接类型

1. Client 发起一个包含 `Connection:keep-alive` 的请求，HTTP/1.1使用 `keep-alive` 为默认值。
2. Server收到请求后：
   - 如果 Server 支持 keep-alive，回复一个包含 Connection:keep-alive 的响应，不关闭连接；
   - 如果 Server 不支持 keep-alive，回复一个包含 Connection:close 的响应，关闭连接。
3. 如果client收到包含 `Connection:keep-alive` 的响应，向同一个连接发送下一个请求，直到一方主动关闭连接。

**keep-alive在很多情况下能够重用连接，减少资源消耗，缩短响应时间，比如当浏览器需要多个文件时(比如一个HTML文件和相关的图形文件)，不需要每次都去请求建立连接。**

##### 1.2.3 Upgrade-Insecure-Requests 

Upgrade-Insecure-Requests：升级不安全的请求，意思是会在加载 http 资源时自动替换成 https 请求，让浏览器不再显示https页面中的http请求警报。

**HTTPS 是以安全为目标的 HTTP 通道，所以在 HTTPS 承载的页面上不允许出现 HTTP 请求，一旦出现就是提示或报错。**

##### 1.2.4 User-Agent

User-Agent：是客户浏览器的名称。

##### 1.2.5 Accept

Accept：指浏览器或其他客户端可以接受的MIME（Multipurpose Internet Mail Extensions（多用途互联网邮件扩展））文件类型，服务器可以根据它判断并返回适当的文件格式。

举例：

`Accept: */*`：表示什么都可以接收。

`Accept：image/gif`：表明客户端希望接受GIF图像格式的资源；

`Accept：text/html`：表明客户端希望接受html文本。

`Accept: text/html, application/xhtml+xml;q=0.9, image/*;q=0.8`：表示浏览器支持的 MIME 类型分别是 html文本、xhtml和xml文档、所有的图像格式资源。

**q是权重系数，范围 0 =< q <= 1，q 值越大，请求越倾向于获得其“;”之前的类型表示的内容。若没有指定q值，则默认为1，按从左到右排序顺序；若被赋值为0，则用于表示浏览器不接受此内容类型。**

**Text：用于标准化地表示的文本信息，文本消息可以是多种字符集和或者多种格式的；Application：用于传输应用程序数据或者二进制数据。**

##### 1.2.6 Referer

Referer：表明产生请求的网页来自于哪个URL，用户是从该 Referer页面访问到当前请求的页面。这个属性可以用来跟踪Web请求来自哪个页面，是从什么网站来的等。

有时候遇到下载某网站图片，需要对应的referer，否则无法下载图片，那是因为人家做了防盗链，原理就是根据referer去判断是否是本网站的地址，如果不是，则拒绝，如果是，就可以下载；

##### 1.2.7 Accept-Encoding

Accept-Encoding：指出浏览器可以接受的编码方式。编码方式不同于文件格式，它是为了压缩文件并加速文件传递速度。浏览器在接收到Web响应之后先解码，然后再检查文件格式，许多情形下这可以减少大量的下载时间。

举例：Accept-Encoding:gzip;q=1.0, identity; q=0.5, *;q=0

如果有多个Encoding同时匹配, 按照q值顺序排列，本例中按顺序支持 gzip, identity压缩编码，支持gzip的浏览器会返回经过gzip编码的HTML页面。 **如果请求消息中没有设置这个域服务器假定客户端对各种内容编码都可以接受。**

##### 1.2.8 Accept-Language

Accept-Langeuage：指出浏览器可以接受的语言种类，如en或en-us指英语，zh或者zh-cn指中文，当服务器能够提供一种以上的语言版本时要用到。

##### 1.2.9 Accept-Charset

Accept-Charset：指出浏览器可以接受的字符编码。

举例：Accept-Charset:iso-8859-1,gb2312,utf-8

- ISO8859-1：通常叫做Latin-1。Latin-1包括了书写所有西方欧洲语言不可缺少的附加字符，英文浏览器的默认值是ISO-8859-1.
- gb2312：标准简体中文字符集;
- utf-8：UNICODE 的一种变长字符编码，可以解决多种语言文本显示问题，从而实现应用国际化和本地化。

**如果在请求消息中没有设置这个域，缺省是任何字符集都可以接受。**

##### 1.2.10 Cookie

Cookie：浏览器用这个属性向服务器发送Cookie。Cookie是在浏览器中寄存的小型数据体，它可以记载和服务器相关的用户信息，也可以用来实现会话功能。

##### 1.2.11 Content-Type 

Content-Type：POST请求里用来表示的内容类型。

举例：Content-Type = Text/XML; charset=gb2312：

指明该请求的消息体中包含的是纯文本的XML类型的数据，字符编码采用“gb2312”。

### 2. HTTP POST 请求报文

一个HTTP POST请求报文通常由三部分组成：请求行、请求头和请求体。

请求行包含了HTTP请求的方法、请求的URL以及HTTP协议的版本，格式如下：

```http
POST /path/to/resource HTTP/1.1
```

请求头包含了一系列的键值对，用来描述请求的信息，例如请求的内容类型、请求的长度、身份验证信息等，格式如下：

```http
Host: www.example.com
Content-Type: application/json
Content-Length: 27
```

请求体包含了实际的请求数据，例如提交的表单数据、JSON数据等。请求体的格式取决于Content-Type头部的值，例如如果Content-Type为application/json，则请求体应该是一个JSON对象，格式如下：

```json
{"name": "John Doe", "age": 30}
```

下面是一个完整的HTTP POST请求报文的例子：

```http
POST /api/users HTTP/1.1
Host: www.example.com
Content-Type: application/json
Content-Length: 27

{"name": "John Doe", "age": 30}
```

这个请求报文表示一个HTTP POST请求，请求的URL是/api/users，请求的内容类型是JSON，请求体是一个包含"name"和"age"属性的JSON对象。

## 三、HTTP响应

### 1. HTTP响应报文分析

HTTP（Hypertext Transfer Protocol）响应报文是Web服务器向客户端（例如浏览器）发送的数据，以响应先前发送的HTTP请求。它包含以下四部分：状态行（Status Line）、空行、响应头（Response Headers）、响应正文（Response Body）。

以下是一个HTTP响应报文的示例：

```http
--- 响应行/状态行 ---
HTTP/1.1 200 OK # HTTP协议版本 状态码 状态描述
--- 响应头 ---
Server: Tengine # 服务器名称
Content-Type: text/html; charset=UTF-8 # 内容类型
Content-Length: 1024
Cache-Control: no-cache
Expires: Wed, 30 Mar 2023 12:00:00 GMT
Set-Cookie: sessionid=12345; Expires=Wed, 30 Mar 2023 12:00:00 GMT; Path=/
--- 空行 ---
--- 响应体 ---
<!DOCTYPE html>
<html>
<head>
  <title>My Webpage</title>
</head>
<body>
  <h1>Welcome to my webpage!</h1>
  <p>This is some example text.</p>
</body>
</html>
```

该响应报文表示HTTP请求成功（状态码200），响应内容为HTML文本，包含一个标题和一些示例文本。此外，响应包含了一些元数据，例如Content-Length、Cache-Control、Expires和Set-Cookie等。

#### 1.1 状态行

该行包含HTTP版本、状态码和状态消息，例如HTTP/1.1 200 OK。状态码指示服务器是否成功处理了请求以及响应的类型（例如成功、重定向或错误）。

##### 1.1.1 HTTP 状态码

HTTP 状态码是**用于表示web服务器响应状态的3位数字代码**。

| 状态码 | 说明                             |
| :----- | :------------------------------- |
| 200    | 请求成功                         |
| 307    | 重定向                           |
| 400    | 错误的请求，请求地址或者参数有误 |
| 404    | 请求资源在服务器不存在           |
| 500    | 服务器内部源代码出现错误         |

响应状态代码有三位数字组成，第一个数字定义了响应的类别，且有五种可能取值。

常见状态码：

- `100~199`：表示服务器成功接收部分请求，要求客户端继续提交其余请求才能完成整个处理过程。
- `200~299`：表示服务器成功接收请求并已完成整个处理过程。常用200（OK 请求成功）。
- `300~399`：为完成请求，客户需进一步细化请求。例如：请求的资源已经移动一个新地址、常用302（所请求的页面已经临时转移至新的url）、307和304（使用缓存资源）。
- `400~499`：客户端的请求有错误，常用404（服务器无法找到被请求的页面）、403（服务器拒绝访问，权限不够）。
- `500~599`：服务器端出现错误，常用500（请求未完成。服务器遇到不可预知的情况）。

#### 1.2 响应头

响应头包含有关响应的元数据信息，例如响应内容的类型（MIME类型）、响应时间、缓存控制和cookie等信息。

##### 1.2.1 Server：Tengine/1.4.6

这个是服务器和相对应的版本，只是告诉客户端服务器的信息。

##### 1.2.2 Connection：keep-alive

这个字段作为回应客户端的Connection：keep-alive，告诉客户端服务器的tcp连接也是一个长连接，客户端可以继续使用这个tcp连接发送http请求。

##### 1.2.3 Date：Sun, 21 Sep 2016 06:18:21 GMT

这个是服务端发送资源时的服务器时间，GMT是格林尼治所在地的标准时间。http协议中发送的时间都是GMT的，这主要是解决在互联网上，不同时区在相互请求资源的时候，时间混乱问题。

##### 1.2.4 Cache-Control：must-revalidate, no-cache, private。

这个值告诉客户端，服务端不希望客户端缓存资源，在下次请求资源时，必须要从新请求服务器，不能从缓存副本中获取资源。

- Cache-Control是响应头中很重要的信息，当客户端请求头中包含Cache-Control:max-age=0请求，明确表示不会缓存服务器资源时,Cache-Control作为作为回应信息，通常会返回no-cache，意思就是说，"那就不缓存呗"。
- 当客户端在请求头中没有包含Cache-Control时，服务端往往会定,不同的资源不同的缓存策略，比如说oschina在缓存图片资源的策略就是Cache-Control：max-age=86400,这个意思是，从当前时间开始，在86400秒的时间内，客户端可以直接从缓存副本中读取资源，而不需要向服务器请求。

##### 1.2.5 Content-Type：text/html;charset=UTF-8

告诉客户端，资源文件的类型，还有字符编码，客户端通过utf-8对资源进行解码，然后对资源进行html解析。通常我们会看到有些网站是乱码的，往往就是服务器端没有返回正确的编码。

##### 1.2.6 Pragma:no-cache

这个含义与Cache-Control等同。

##### 1.2.7 Content-Encoding:gzip

告诉客户端，服务端发送的资源是采用gzip编码的，客户端看到这个信息后，应该采用gzip对资源进行解码。

##### 1.2.8 Expires:Sun, 1 Jan 2000 01:00:00 GMT

这个响应头也是跟缓存有关的，告诉客户端在这个时间前，可以直接访问缓存副本，很显然这个值会存在问题，因为客户端和服务器的时间不一定会都是相同的，如果时间不同就会导致问题。所以这个响应头是没有Cache-Control：max-age=*这个响应头准确的，因为max-age=date中的date是个相对时间，不仅更好理解，也更准确。

##### 1.2.9 Transfer-Encoding：chunked

这个响应头告诉客户端，服务器发送的资源的方式是分块发送的。一般分块发送的资源都是服务器动态生成的，在发送时还不知道发送资源的大小，所以采用分块发送，每一块都是独立的，独立的块都能标示自己的长度，最后一块是0长度的，当客户端读到这个0长度的块时，就可以确定资源已经传输完了。

##### 1.2.10 Vary: Accept-Encoding

告诉缓存服务器，缓存压缩文件和非压缩文件两个版本，现在这个字段用处并不大，因为现在的浏览器都是支持压缩的。

#### 1.3 响应正文

响应正文包含实际的响应数据，例如HTML网页、图片、JSON数据等。响应正文的格式由Content-Type头字段指定。

## 四、HTTP Cookie

### 1. 介绍

HTTP Cookie（HTTP Cookie，通常称为Cookie）是一个用于在Web浏览器和Web服务器之间传递数据的简短文本字符串。Cookie是由Web服务器发送给Web浏览器的，然后存储在Web浏览器中，每次Web浏览器向Web服务器发送请求时都会发送Cookie。

HTTP Cookie通常用于以下目的：

- 记住用户登录状态
- 存储用户偏好设置
- 跟踪用户行为

### 2. 使用

HTTP Cookie是一种在Web浏览器和Web服务器之间传递数据的机制。Python中有许多库可用于处理HTTP Cookie，其中最流行的是Requests库。使用Python处理HTTP Cookie的基本方法包括创建Cookie、读取Cookie、更新Cookie和删除Cookie。在创建Cookie时，可以使用字典来存储Cookie的名称和值。在发送HTTP请求时，可以使用cookies参数将Cookie包含在请求中。在读取Cookie时，可以使用response.cookies属性获取Cookie，并使用get()方法获取特定Cookie的值。在更新Cookie时，可以直接修改Cookie字典中的值，并将更新后的Cookie包含在HTTP请求中。在删除Cookie时，可以使用pop()方法从Cookie字典中删除Cookie，并将更新后的Cookie包含在HTTP请求中。下面是使用Python处理HTTP Cookie的基本方法：

1. 创建一个Cookie

在Python中，可以使用Requests库来创建一个Cookie。

```python
import requests

# 创建一个Cookie
cookies = {
    'username': 'John Doe',
    'session_id': '123456789'
}

# 发送一个HTTP请求，并在其中包括Cookie
response = requests.get('http://example.com/', cookies=cookies)
```

在上面的示例中，使用字典创建了一个名为 "username" 和 "session_id" 的Cookie，并将其存储在变量 "cookies" 中。然后，在HTTP请求中包括Cookie。

2. 读取Cookie

在Python中，可以使用Requests库来读取Cookie。

```python
import requests

# 发送一个HTTP请求，并从其中读取Cookie
response = requests.get('http://example.com/')
cookies = response.cookies

# 获取名为 "username" 的Cookie的值
username = cookies.get('username')
```

在上面的示例中，首先发送一个HTTP请求，并从中获取Cookie。然后，使用get()方法获取名为 "username" 的Cookie的值。

3. 更新Cookie

在Python中，可以使用Requests库来更新Cookie。

```python
import requests

# 创建一个Cookie
cookies = {
    'username': 'John Doe',
    'session_id': '123456789'
}

# 发送一个HTTP请求，并在其中包括Cookie
response = requests.get('http://example.com/', cookies=cookies)

# 更新名为 "username" 的Cookie的值
cookies['username'] = 'Jane Doe'

# 发送一个HTTP请求，并在其中包括更新后的Cookie
response = requests.get('http://example.com/', cookies=cookies)
```

在上面的示例中，首先创建一个Cookie，并将其包含在HTTP请求中。然后，更新名为 "username" 的Cookie的值，并将更新后的Cookie包含在另一个HTTP请求中。

4. 删除Cookie

在Python中，可以使用Requests库来删除Cookie。

```python
import requests

# 创建一个Cookie
cookies = {
    'username': 'John Doe',
    'session_id': '123456789'
}

# 发送一个HTTP请求，并在其中包括Cookie
response = requests.get('http://example.com/', cookies=cookies)

# 删除名为 "username" 的Cookie
cookies.pop('username')

# 发送一个HTTP请求，并在其中包括更新后的Cookie
response = requests.get('http://example.com/', cookies=cookies)
```

在上面的示例中，首先创建一个Cookie，并将其包含在HTTP请求中。然后，删除名为 "username" 的Cookie，并将更新后的Cookie包含在另一个HTTP请求中。

## 五、HTTPS

`HTTPS`（Hypertext Transfer Protocol over Secure Socket Layer）

HTTPS（超文本传输安全协议）是HTTP协议的加密版本。它通过使用SSL或TLS协议来加密HTTP通信，保护数据的机密性和完整性。

HTTPS与HTTP的不同之处在于其使用了加密算法对通信内容进行加密，从而防止中间人攻击、窃听和篡改数据。这种加密机制使得HTTPS协议比HTTP更加安全可靠，因此更适合于传输敏感信息，如用户账号密码、银行卡信息等。

HTTPS的通信过程分为握手、加密和数据传输三个阶段。握手阶段用于建立通信信道，加密阶段用于加密通信内容，数据传输阶段用于传输加密后的数据。

总的来说，HTTP和HTTPS都是用于Web通信的协议，它们之间的主要区别在于安全性和加密机制。HTTP是一种明文协议，不具备安全性，而HTTPS通过使用加密机制提高了安全性，更适合于传输敏感信息。

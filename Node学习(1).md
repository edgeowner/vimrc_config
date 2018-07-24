---
title: Node实战（1）
date: 2018-05-31 12:39:37
categories: Node
tags: [Node]
copyright: true
---

### Node特性以及一些概念介绍
&emsp;&emsp;Node.js采用的事件驱动、非阻塞I/O模型，使得它既轻量、高效，并构建运行在分布式设备上数据密集型的实时程序。使用Node.js可以开发的场景：
1. 具有复杂逻辑的网站；
2. 基于社交网络的大规模Web应用；
3. Web Socket服务器；
4. TCP/UDP套接字应用程序；
5. 命令行工具；
6. 交互式终端程序；
7. 带有图形用户界面的本地应用程序；
8. 单元测试工具；
9. 客户端JavaScript编译器
&emsp;&emsp;Node.js内建了HTTP服务器支持。不仅可以用来调试代码，本身就可以部署到产品环境
<!--more-->

### 事件驱动和异步式I/O
&emsp;&emsp;Node为JS提供了一个事件驱动的、异步平台。浏览器的工作原理和Node的工作原理类似，都是事件驱动（事件轮询）和非阻塞的I/O处理：
#### 1.事件轮询：
查看以下代码Demo
   ``` javascript
   res= db.query('select * from table');
   res.output();
   ```
   以上大码执行到第一行时，线程会阻塞，等待数据库返回查询结果，然后再继续处理。由于数据库查询可能涉及磁盘读写和网络通信，其延时可能相当大(长达几个到几百个毫秒)，线程会在这里阻塞等待结果返回。对于高并发的访问，一方面线程长期阻塞等待，另一方面为了应付新请求而不断增加线程，因此会浪费大量系统资源，同时线程的增多也会占用大量的CPU时间来处理内存上下文切换，而且还容易遭受低速连接攻击。来看Node.js解决方式：
   ```
   db.query('select * from table',function(res){
        res.output();
   });
   ```
   这段代码中db.query的第二个参数是一个函数(回调函数)，进程在执行到db.query时，不会等待结果返回，而是直接继续执行后面的语句，直到进入事件循环。当数据库查询结果返回时，会将事件发送到事件队列，等到线程进入事件循环后，才会调用之前的回调函数继续执行后面的逻辑。
   
#### 2.Node.js的异步机制
基于事件，所有的磁盘I/O，网络通信、数据库查询都以非阻塞的方式请求，返回结果由事件循环来处理。。Node.js 进程在同一时刻只会处理一个事件，完成后立即进入事件循环检查并处理后面的事件。这样做的好处是：CPU 和内存在同一时间集中处理一件事，同时尽可能让耗时的 I/O 操作并行执行。对于低速连接攻击，Node.js 只是在事件队列中增加请求，等待操作系统的回应，因而不会有任何多线程开销，很大程度上可以提高Web应用的健壮性，防止恶意攻击。

#### 3.弊端：
不符合开发者常规线性思路，往往需要把一个完整逻辑拆分为一个个事件，增加开发后调试难度。

------

### Node.js性能
&emps;&emps;Node.js用异步式I/O和事件驱动代替多线程

#### 电子书搜索
&emsp;&emsp;鸠摩搜书([资源地址](https://www.jiumodiary.com/))是一个比较不错的电子书搜索网站。内容也比较全。
![Jiumodiary](http://p5vswdxl9.bkt.clouddn.com/jiumodiary.jpg)

#### 网盘资源搜索
&emsp;&emsp;盘搜([资源地址](http://pansou.com))可以通过这个网站搜索百度网盘上面的各种资源。
![Pansou](http://p5vswdxl9.bkt.clouddn.com/Pansou.jpg)

#### 无版权图片搜索
&emsp;&emsp;Unsplash([资源地址](https://unsplash.com))是我用过的最好的网站，不需要登录，图片很高请，也比较全。唯一的缺点就是需要英文搜搜
![Unsplash](http://p5vswdxl9.bkt.clouddn.com/unsplash.jpg)

#### 在线UML制图
&emsp;&emsp;ProcessOn([资源地址](https://unsplash.com))是一个在线协作绘图平台，为用户提供最强大、易用的作图工具!支持在线创作**流程图** 、**BPMN** 、**UML图** 、**UI界面原型设计**、**iOS界面原型设计**等。
![ProcessOn](http://p5vswdxl9.bkt.clouddn.com/ProcessOn.jpg)

#### Json在线验证及格式化(1)
&emsp;&emsp;json.cn([资源地址](https://www.json.cn/))是比较不错的，不仅支持Json格式的验证及格式化，还可以将Json格式压缩成普通文本等，以及查询Json组件和Json解析相关代码好用功能。
![Json.cn](http://p5vswdxl9.bkt.clouddn.com/json.cn.jpg)

#### Json在线验证及格式化(2)
&emsp;&emsp;bejson.com([资源地址](http://www.bejson.com/jsoneditoronline/))本人推荐这个，**Bejson** 可以在线支持格式化JSON数据，并检测Json数据问题
![bejson.com](http://p5vswdxl9.bkt.clouddn.com/3BD8FD16-438D-461B-9938-4E07E88C83E2.png)

#### Json生成java类
&emsp;&emsp;bejson([资源地址](http://www.bejson.com/json2javapojo/))Json是目前JavaWeb中数据传输的主要格式，很多时候会有把Json转成Java对象的需求。有时候合作方会提供一个Json的样例，需要我们自己定义Java类，这时候这个工具就派上用场了。
![bejson](http://p5vswdxl9.bkt.clouddn.com/bejson.jpg)

#### SQL自动生成Java代码
&emsp;&emsp;Json([资源地址](http://www.autojcode.com/code/sql2class.jsp#))是目前JavaWeb中数据传输的主要格式，很多时候会有把json转成Java对象的需求。有时候合作方会提供一个json的样例，需要我们自己定义Java类，这时候这个工具就派上用场了。
![AutoJCode.jpg](http://p5vswdxl9.bkt.clouddn.com/AutoJcode.jpg)

#### Maven依赖查询
&emsp;&emsp;Mvnrepository([资源地址](http://mvnrepository.com/))查询开源的Java的jar包版本依赖标签
![mvnrepository](http://p5vswdxl9.bkt.clouddn.com/maven.png)

#### Cron表达式生成
&emsp;&emsp;Pdtools([资源地址](http://www.pdtools.net/tools/becron.jsp
))用于配置定时任务的cron表达式。
![cron](http://p5vswdxl9.bkt.clouddn.com/cron.jpg)

#### 正则验证
&emsp;&emsp;([资源地址](http://tool.chinaz.com/regex))Java开发对正则表达式肯定不陌生。站长工具提供的正则验证还不错。
![](http://p5vswdxl9.bkt.clouddn.com/regex%281%29.jpg)

#### 正则代码生成
&emsp;&emsp;([资源地址](http://tool.chinaz.com/tools/regexgenerate))站长工具提供的正则代码生成。可以一键生成身份证号、邮箱、手机号等验证的正则表达式。
![](http://p5vswdxl9.bkt.clouddn.com/regex2.jpg)

#### 时间戳转换
&emsp;&emsp;([资源地址](http://tool.chinaz.com/Tools/unixtime.aspx))时间戳(英语：Timestamp）是指在一连串的资料中加入辨识文字，如时间或日期，用以保障本地端（local）资料更新顺序与远端（remote）一致。
Java中很多地方都会用到时间戳，也经常会使用这种转换工具。
![](http://p5vswdxl9.bkt.clouddn.com/timestamp.jpg)

#### 加密解密
&emsp;&emsp;([资源地址](http://tool.chinaz.com/tools/textencrypt.aspx))加密解密也是JavaWeb可能会经常遇到的，有的时候我们需要验证加密算法是否正确，或者要解密等场景，就需要一个在线工具。
![](http://p5vswdxl9.bkt.clouddn.com/md5.jpg)

#### 在线调色板
&emsp;&emsp;([资源地址](http://link.fobshanghai.com/rgbcolor.htm))常用MarkDown字体配色使用获取RGB代码例如：
```xml
<font face="微软雅黑" color=#9900ff size=2>-Xms1024m -Xmx1024m  -XX:PermSize=512M -XX:MaxPermSize=1024m  -Dfile.encoding=utf-8 </font>
```
![](http://p5vswdxl9.bkt.clouddn.com/tiaose.jpg)

#### CSS样式参照
&emsp;&emsp;([资源地址](https://www.w3schools.com/colors/colors_names.asp))常用字体颜色修改以及相应名称等设置可参照其目录(**翻墙**)：
![](http://p5vswdxl9.bkt.clouddn.com/tiaoseban.jpg)

#### ASCII ART生成
&emsp;&emsp;ASCII ART生成([资源地址](http://patorjk.com/software/taag/))
![](http://p5vswdxl9.bkt.clouddn.com/ASCII%20ART.jpg)

#### 常用对照表
1. [ASCII对照表]( http://tool.oschina.net/commons?type=4)
2. [HTTP状态码](http://tool.oschina.net/commons?type=5)
3. [HTTP Content-type]( http://tool.oschina.net/commons)
4. [TCP/UDP常见端口参考](http://tool.oschina.net/commons?type=7)
5. [HTML转义字符]( http://tool.oschina.net/commons?type=2)
6. [RGB颜色参考](http://tool.oschina.net/commons?type=3)
7. [网页字体参考](http://tool.oschina.net/commons?type=8)



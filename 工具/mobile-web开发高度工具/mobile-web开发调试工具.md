%
id: 20120911mobileweb
date: 2012-09-11
title: mobile-web开发调试工具
desc: 由于设备的局限，手机端的网页，无法像PC端浏览器一样具有方便快捷的开发调试功能，借助于3层结构的通信中转，我们可以找到一些相对优秀的跨设备调试工具，来帮助我们解决这一难题。
cate: 工具
tag: mobile,webapp,weinre,socketbug,Jsconsole
%

# mobile-web开发调试工具


## 跨设备的web开发调试工具

### 1、weinre

weinre是一个开源的基于webkit调试的远程调试工具，它的2.0版本依赖于nodejs运行环境。是目前比较受欢迎且优秀的调试工具。

先来张官方贴图：

<img src="http://people.apache.org/~pmuellr/weinre/docs/latest/images/weinre-demo.jpg" alt="">

没错，如你所见到的，你可以通过PC端的chrome调试手机端正在浏览的网页，这是过程是即时的，你可以理解为将手机端的页面映射到了PC端chrome中。

**更多weinre资料请参见：**

* 官网：http://people.apache.org/~pmuellr/weinre/docs/latest/

* 项目地址：https://github.com/apache/incubator-cordova-weinre


### 2、Socketbug

功能和weinre差不多，也是跨设备调试的那种，基于Node.js和Socket.IO；

官方示意图：

<img src="https://a248.e.akamai.net/camo.github.com/41ad0bf177c6e9f2700bac78c127423d092534b4/687474703a2f2f6769746875622e736f636b65746275672e636f6d2f73625f696e666f2e706e67" alt="">

**更多Socketbug资料请参见：**

* 官网：http://socketbug.com/

* 项目地址：https://github.com/manifestinteractive/socketbug


### 3、JSConsole
> JSConsole是一个风格和Weinre类似的工具，它更多地关注于控制台输出和代码求值。在访问JSConsole的网站的时候，用户输入“:listen”来获得带有GUID的一段JavaScript代码。这段代码需要被加入到待调试的网页中。于是，在加载网页的时候，代码将会连接到JSConsole服务器，并且根据GUID将此会话和用户的会话关联起来，于是用户浏览器中的控制台现在便已经处于待调试网页的JavaScript运行时环境中了。

<img src="https://a248.e.akamai.net/camo.github.com/83749d160471b494282444e8499208ab536407fe/687474703a2f2f692e696d6775722e636f6d2f68795246352e706e67" alt="">

**更多Socketbug资料请参见：**

* 官网：http://jsconsole.com/

* 项目地址：https://github.com/remy/jsconsole


## 资料参考

* Web应用调试：现在是Weinre和JSConsole，最终会是WebKit的远程调试协议：http://www.infoq.com/cn/news/2011/08/mobile-web-debugging
%
id: 20120901nodejsmarkdown
date: 2012-09-01
title: nodejs下markdown解析引擎评测
desc: markdown做为被coder广受欢迎的文档书写格式，其在各种语言版本中都有相关的引擎解析，nodejs也不例外，现收集了几款还不错的，简单做了下对比评测，解析程度还是会有差别，没有完美版。
cate: 调研
tag: markdown,nodejs
%

# nodejs下markdown解析引擎评测

markdown做为被coder广受欢迎的文档书写格式，其在各种语言版本中都有相关的引擎解析，nodejs也不例外，现收集了几款还不错的，简单做了下对比评测，解析程度还是会有差别，没有完美版。

### 1、marked
>这是唯一一款解析率非常到位，而且精确的引擎，除了在使用原生table时会产生一堆没用的br（可修改源码，将其屏蔽掉），几乎完美；

* 项目地址：https://github.com/chjj/marked
* 预览地址：<a href="./nodejs-markdown/marked.html" target="_blank">marked.html</a>

### 2、showdown
> showdown对基于的语法解析没有什么问题，对于内联式的代码块的解析会被漏掉，比如``` ````ar foo;```` ```

* 项目地址：https://github.com/coreyti/showdown

### 3、markdown
> markdown是被注册到npm里的解析包，基本语法没问题，和showdown一样，对于内联式的代码块的解析会被漏掉，比如``` ````ar foo;```` ```

* 项目地址：https://github.com/evilstreak/markdown-js

### 4、node-markdown
> markdown继承于showdown，也没能解决内联代码块的问题。

* 项目地址：https://github.com/andris9/node-markdown

### 5、CodeMirror.markdown
> 代码块，解析时没有考虑原格式的保留的需求，所有代码会集中到一行；

* 项目地址：https://github.com/marijnh/CodeMirror/tree/master/mode/markdown
* 预览地址：http://www.osctools.net/markdown
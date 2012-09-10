%
id: 20120910nodejsexec
date: 2012-09-10
title: nodejs中如何执行系统命令？??
desc: 尝试了下nodejs中如何执行系统命令。这在有时候非常有用。真的有用。
cate: 学习
tag: nodejs,sys,child_process
%


### 贴一段实例代码

```
	var sys = require('sys')
	var exec = require('child_process').exec;

	var http = require('http');
	http.createServer(function (req, res) {
	    res.writeHead(200, {'Content-Type': 'text/plain'});
	    var x = exec("forever restart server.js", function(err, stdout, stderr){
	        res.write(stdout);
	    });
	    x.addListener('exit',function(){
	        res.end();
	    });
	}).listen(8888);
```
%
id: 20120911mobileuri
date: 2012-09-11
title: 手机端URI协议
desc: PC端我们可以通过http,ftp,mailto等URI协议来完成一系列通过链接而执行的操作，在手机端通过这种方式来执行操作的需求不断增加，比如点击呼叫，发信息，保存联系人等。新的URI协议可以让我们如愿以偿。
cate: 调研,学习
tag: webapp,uri,协议
%

# 手机端URI协议
> PC端我们可以通过http,ftp,mailto等URI协议来完成一系列通过链接而执行的操作，在手机端通过这种方式来执行操作的需求不断增加，比如点击呼叫，发信息，保存联系人等。新的URI协议可以让我们如愿以偿。

## wap URI 协议列表

* tel
	- **说明：**调用呼叫电话功能；
	- **使用实例：** `<a href="tel:010xxxxxxxx">010xxxxxxxx</a>`


* sms
	- **说明：**调用短信发送功能；
	- **格式：**`sms:电话1,电话2,电话x?body=内容`
	- **使用实例：** `<a href="sms:1343642xxxx?body=Hello，小web!">发送短信</a>`


* mmsto
	- **说明：**调用彩信发送功能；
	- **格式：**`mmsto:电话1,电话2,电话x?subject=内容`
	- **使用实例：** `<a href="mmsto:1343642xxxx?subject=Hello，小web!">发送彩信</a>`


* wtai
	- **说明：**与tel类似,可以呼叫电话或添加新的联系人；
	- **格式：**
		- 呼叫：`<a href="wtai://wp/mc;13xxxxxxxxx">拨打13xxxxxxxxx</a>`
		- 添加：`<a href="wtai://wp/ap;13xxxxxxxxx">添加13xxxxxxxxx</a>`



## IOS与Android对mobile URI的支持

<table cellspacing="0" class="ADoc_table">
	<tr>
		<th> URI </th>
		<th> ios </th>
		<th> 安卓 </th>
	</tr>
	<tr>
		<td> tel </td>
		<td> Y </td>
		<td> Y </td>
		</tr>
	<tr>
		<td> wtai </td>
		<td> N </td>
		<td> N </td>
	</tr>
	<tr>
		<td> sms </td>
		<td> Y </td>
		<td> Y </td>
	</tr>
	<tr>
		<td> mmsto </td>
		<td> N </td>
		<td> Y </td>
	</tr>
</table>



## 资料参考

* URL详解：http://baike.baidu.com/view/1496.htm
* wtai协议：http://baike.baidu.com/view/955547.htm
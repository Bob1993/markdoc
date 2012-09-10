%
id: 20120903html5
date: 2012-09-03
title: html5新表单元素使用调研
desc: 详细调研了html5新forms的新特性，新内容类型和验证方面的技术信息。
cate: 调研
tag: html5,newforms
%

# html5新表单元素使用调研

##简述

html5的新表单主要有以下几点重大的改进：

* 内容类型的增强，比如时间选择控件，range滑动条，颜色选择控件，搜索框控件等；
* 提示及验证方面的增强，提示性信息(placeholder)、正则验证表达式(pattern)、是否允许为空(required)等;
* 表单元素的伪类样式设定，比如实时的验证出错伪类；

这些新的特性不仅简化了很多的开发工作，对于表单的产品设计及体验也带来了更多的灵活性和扩展性；

> 以下新特性在浏览器**chrome21**下测试通过；

##新特性简介


### 一、新增form tag

#### 1、tag: datalist

```
<input type="text" list="dataList" />
<datalist id="dataList">
	<option label="12条" value="路飞"></option>
	<option label="22条" value="罗宾"></option>
	<option label="32条" value="娜美"></option>
</datalist>
```
**测试**：<input type="text" list="dataList" placeholder="双击演示" />
<datalist id="dataList">
	<option label="12条" value="路飞"></option>
	<option label="22条" value="罗宾"></option>
	<option label="32条" value="娜美"></option>
</datalist>


### 二、新增type类型

#### 1、type = "date" 
```
<input type="date" />
```
**描述：**日期选择控件，用户点击，可弹出原生的日期选择器用来选择日期，很赞，虽然现在有非常多的UI控件提供使用,还是感觉原生的亲切；

**演示**：<input type="date" />

#### 2、type = "color" 
```
<input type="color" />
```
**描述：**颜色选择控件，用户点击，可弹出原生的颜色选择框，虽然弹出的界面很丑，相对体积庞大的UI控件来说，已经相当不错了；

**返回值**：返回值为16进制符号，如：#ff0000

**演示**：<input type="color" onchange="document.getElementById('colorValue').innerHTML=(this.value)" /><span id="colorValue">#000000</span>

#### 3、type = "number" 
```
<input type="number" max="10" min="1" step="1" />
```
**描述：**数字控件，可控制最大值，最小值及步长；

**私有属性表：**

<table>
	<thead>
		<th>属性名</th>
		<th>实例</th>
		<th>类型</th>
	</thead>
	<tr>
		<td>max</td>
		<td>max="10"</td>
		<td>数字</td>
	</tr>	
	<tr>
		<td>min</td>
		<td>min="1"</td>
		<td>数字</td>
	</tr>	
	<tr>
		<td>step</td>
		<td>step="2"</td>
		<td>数字</td>
	</tr>
</table>

**演示**：<input type="number" max="10" min="1" step="1" value="1" />

#### 4、type = "range" 
```
<input type="range" max="10" min="1" step="1" />
```
**描述：**划动条控件，可控制最大值，最小值及步长；

**私有属性表：**
<table>
	<thead>
		<th>属性名</th>
		<th>实例</th>
		<th>类型</th>
	</thead>
	<tr>
		<td>max</td>
		<td>max="10"</td>
		<td>数字</td>
	</tr>	
	<tr>
		<td>min</td>
		<td>min="1"</td>
		<td>数字</td>
	</tr>	
	<tr>
		<td>step</td>
		<td>step="2"</td>
		<td>数字</td>
	</tr>
</table>

**演示**：<input type="range" max="10" min="1" step="1" value="1" onchange="document.getElementById('rangeValue').innerHTML=(this.value)" /><span id="rangeValue">1</span>

#### 5、type = "search" 
```
<input type="search" />
```
**描述：**搜索控件，比text控制多出一可清除内容的功能，即在右侧有一个小X；

**演示**：<input type="search" value="世界树" />

#### 6、type = "email/url"
```
<input type="email" />
```
**描述：**验证类类型控件，可调用浏览器自身的检测规则验证用户的输入是否正确；

**演示**：
<form>
	邮件地址：<input type="email" required="required" /><input type="submit" value="验证" />
</form>
<form>
	URL地址：<input type="email" required="required" /><input type="submit" value="验证" />
</form>


### 新增属性
<table>
	<thead>
		<th>属性名</th>
		<th>描述</th>
		<th>可选值</th>
		<th>默认值</th>
		<th>实例</th>
		<th>演示</th>
	</thead>
	<tr>
		<td>pattern</td>
		<td>正则表达式验证规则</td>
		<td>正则表达式/不写</td>
		<td>不写</td>
		<td>`400电话：<input type="text" pattern="\d{4}-\d{3}-\d{3}" />`</td>
		<td></td>
	</tr>	
	<tr>
		<td>placeholder</td>
		<td>背景式灰色提示信息；这个太有用了；</td>
		<td>描述文字/无</td>
		<td>无</td>
		<td>`<input type="text" placeholder="姓名" />`</td>
		<td><input type="text" placeholder="姓名" /></td>
	</tr>		
	<tr>
		<td>required</td>
		<td>是否允许为空；</td>
		<td>true：不允许为空/无：可以为空</td>
		<td>无</td>
		<td>`<input type="text" required="true" />`</td>
		<td><input type="text" required="true" /></td>
	</tr>	
	<tr>
		<td>autocomplete</td>
		<td>表单自动填充功能</td>
		<td>on/off</td>
		<td>on</td>
		<td>`<input type="text" autocomplete="on" />`</td>
		<td><input type="text" autocomplete="on" /></td>
	</tr>	
	<tr>
		<td>autofocus</td>
		<td>输入型表单自动聚焦</td>
		<td>ture或不写</td>
		<td>不写</td>
		<td>`<input type="text" autocomplete="on" autofocus="true" />`</td>
		<td><input type="text" autocomplete="on" autofocus="true" /></td>
	</tr>	
	<tr>
		<td>form</td>
		<td>为表单荐指定归属的form，对应的表单项可以脱离出form的标签范围；</td>
		<td>指定form的id/不写</td>
		<td>不写</td>
		<td>`<form id="demo"></form><input type="text" form="demo" />`</td>
		<td>
			<form action="" id="demo"></form>
			<input type="text" form="demo" />
		</td>
	</tr>	
	<tr>
		<td>novalidate</td>
		<td>禁用表单的默认验证功能；</td>
		<td>用在form标签的属性里；</td>
		<td>不写</td>
		<td>`<form action="" id="demo" novalidate="true"></form>`</td>
		<td><form action="" id="demo" novalidate="true"></form></td>
	</tr>	
	<tr>
		<td>formnavalidate</td>
		<td>禁用表单的默认验证功能；</td>
		<td>用在用于提交表单的标签的属性里；</td>
		<td>不写</td>
		<td>`<input type="subimit" formnavalidate="true" />`</td>
		<td></td>
	</tr>	
	<tr>
		<td>formmethod、formenctype 、formnovalidate 和 formtarget</td>
		<td>覆盖默认的form属性</td>
		<td>用在用于提交表单的标签的属性里；</td>
		<td>不写</td>
		<td>`<input type="subimit" formmethod="get" />`</td>
		<td></td>
	</tr>
</table>


##交互验证

###一、样式控制，新伪类
<style type="text/css">
	.url+span.error{margin-left:5px;display: none;color:red;}
	.url:valid{border:1px solid green;}
	.url:invalid{border:1px solid red;}
	.url:invalid + span.error{display: inline;}
	.url:required{border:1px solid blue;}
	.urloptional{border:1px solid orange;}
</style>

* input:valid{}
> 规则验证正确状态下的样式设定；

	* DEMO：<input type="url" class="url" placeHolder="网址" />
	* **源码**：
	```
	<style type="text/css">
		.url:valid{border:1px solid green;}
	</style>
	<input type="url" class="url" placeHolder="网址" />
	```

* input:invalid{}
> 规则验证错误状态下的样式设定，配合相邻选择器可以很简单地做出实时验证的样式提示；

	* DEMO：<input type="url" class="url" value="not a url" placeHolder="网址" /><span class="error">请输入正确的URL。</span>
	* **源码**：
	```
	<style type="text/css">
		.url+span.error{display: none;}/* 常态下隐藏出错提示标签 */
		.url:invalid{border:1px solid red;}
		.url:invalid + span.error{display: inline;}/* 错误态下显示出错提示标签 */
	</style>
	<input type="url" class="url" value="not a url" placeHolder="网址" /><span class="error">请输入正确的URL。</span>
	```

* input:required{}
> 不能为空的样式设定；

	* DEMO：<input type="url" class="url" placeHolder="网址" required />
	* **源码**：
	```
	<style type="text/css">
		.url:required{border:1px solid blue;}
	</style>
	<input type="url" class="url" placeHolder="网址" required />
	```

* input:optional{}
> 与required相对，可以不为空的样式设定；

	* DEMO：<input type="url" class="url" placeHolder="网址" />
	* **源码**：
	```
	<style type="text/css">
		.url:optional{border:1px solid orange;}
	</style>
	<input type="url" class="url" placeHolder="网址" />
	```

###二、脚本控制，新的方法和属性

####方法
* checkValidity
> 根据元素自身的规则进行静态验证，若静态验证结果为真，返回true，反之返回false。

	* 适用范围：适用于所有表单元素。
	* 使用契机：一旦输入值效，触发invalid事件，即可使用该方法；
	* **实例**
	```
	var checkValue = function(e){
        var el = e.target;
        //获取验证结果
        var isvalid = el.checkValidity();
        if(isvalid){
            //如果正确，执行自定义操作
        }else{
            //如果出错，执行自定义操作
        }
        //阻止浏览器的默认操作
        e.preventDefault();
    }
	```

* setCustomValidity
> 自定义元素的验证出错提示信息。

	* **实例**
	```
	<input type="text" id="demo" />
	<script type="text/javascript">
		var demo = document.getElementById("demo");
		if(!demo.checkValidity()){
			demo.setCustomValidity("亲，您不能这么写！");
		}
	</script>
	```

##参考资料
* [全新改进的HTML5表单创建](http://www.cnbeta.com/articles/149653.htm)
* [HTML5表单及其验证](http://www.cnblogs.com/Wenwang/archive/2012/04/26/2470403.html)
* [HTML5之表单详解](http://mrthink.net/html5-newfeatures-form/)
* [Internet Explorer 10 平台预览版：HTML5表单验证](http://msdn.microsoft.com/zh-tw/ie/hh272905#_HTML5FormsVal)
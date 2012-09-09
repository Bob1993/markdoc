%
id: 20120905header
date: 2012-09-05
title: webapp中header里的新东西
desc: Apple在其移动端的safari浏览器中新加入了一些新的meta属性和link新资源引入，依赖这些新的特性，开发者可以很轻松地将网页转化为和NativeApp类似的应用程序，用户可以将其以图标的形式保存到桌面，和NativeApp一样启动，苹果将之将为webapp。
cate: 调研
tag: webapp,meta
%

# webapp中header里的新东西

Apple在其移动端的safari浏览器中新加入了一些新的meta属性和link新资源引入，依赖这些新的特性，开发者可以很轻松地将网页转化为和NativeApp类似的应用程序，用户可以将其以图标的形式保存到桌面，和NativeApp一样启动，苹果将之将为webapp。

伴随着html5及css3的日益普及，终端设备硬件性能的逐步提升，以html5+css3+javascript为主的webapp已经足可以构造出非常绚丽强大的应用程序。

借此契机，前端的开发人员有必要了解下这些新的特性。将其列入自已的技术积累。


## 一、概念：元数据及外部资源引用

### 1、元数据标签&lt;meta&gt;的定义和用法
> 摘自w3school。

* &lt;meta&gt; 元素可提供有关页面的元信息（meta-information），比如针对搜索引擎和更新频度的描述和关键词。
* &lt;meta&gt; 标签位于文档的头部，不包含任何内容。
* &lt;meta&gt; 标签的属性定义了与文档相关联的名称/值对。

**提示和注释：**

* **注释：**&lt;meta&gt; 标签永远位于 head 元素内部。
* **注释：**元数据总是以名称/值的形式被成对传递的。

**常用的属性/值**

<table>
	<tbody>
		<tr>
			<th>属性</th>
			<th>值</th>
			<th>描述</th>
		</tr>
		<tr>
			<td>http-equiv</td>
			<td>
				<ul>
					<li>content-type</li>
					<li>expires</li>
					<li>refresh</li>
					<li>set-cookie</li>
				</ul>
			</td>
			<td>把 content 属性关联到 HTTP 头部。</td>
		</tr>
		<tr>
			<td>name</td>
			<td>
				<ul>
					<li>description(页面描述)</li>
					<li>keywords(页面关键字)</li>
				</ul>
			</td>
			<td>把 content 属性关联到一个名称。</td>
		</tr>
	</tbody>
</table>

**示例**

```
<!-- 设置页面类型和编码 -->
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
```

```
<!-- 设置页面关键字 -->
<meta name="keywords" content="关键字1,关键字2,关键字3,关键字4">
```

### 2、外部资源引用标签&lt;link&gt;用法

参见：http://www.w3school.com.cn/tags/tag_link.asp


## 二、移动端新元数据设置(meta)/新资源引用类属性(link)

### 前言
在介绍新属性之前，我们有必要先了解下移动设备下的web有哪些新颖的功能点：

1. IOS版的safari支持将一个网页以快捷方式的形式保存到用户的桌面，并且支持自定义图标，启动动画，全屏浏览等特性；如此一来，我们完全可以把一个web伪造成原生的app。

2. 为了兼容传统网页及各种不同尺寸的移动设备而生的viewport属性，通过巧妙的设置可以让你的页面在不同的设备都有着舒服的效果。

### 属性介绍/用法

#### 1、viewport设置

当你在移动设备上打开网页时，默认情况下它会根据默认的viewport(980)进行缩放，让页面适应设备的浏览尺寸，但是这么影响到以尺寸定制的webapp的效果，所以我们可以通过如下设置，禁止缩放。

```
<meta name="viewport" content="user-scalable=no, width=device-width">
```

**注解**

* user-scalable=no : 禁止用户缩放；
* width=device-width ：viewport的宽度以设备为基准；

更多关于viewport介绍，请参见：http://www.xiaoweb.com/xdoc/web-viewport.text


#### 2、快捷方式设置项

用户用移动版safari浏览网站时，可以将网站保存到桌面快捷方式，下次访问时，直接点触图标就可以进入相对应的网站。

这个功能的配置项比较多，具体包括图标设置，启动动画设置，隐藏原生safari的工具栏等，通过这些项的配置，可以让我们的webapp更像一个原生程序。

**快捷方式添加示例：**

![](./20120905header/shortcuts.png)

##### 1. 图标设置

* 使用方法1

```
<link rel="apple-touch-icon" href="icon.png" />
```
**注解：**apple-touch-icon方式，iOS系统会自动将图标生成具有高光、圆角和阴影效果，如图示：

![](./20120905header/icon_demo.png)

* 使用方法2

```
<link rel="apple-touch-icon-precomposed" href="icon.png" />
```
**注解：**apple-touch-icon-precomposed方式，系统会使用你提供的原生图标为准，不会做任何的效果处理。


##### 2. 图标尺寸

由于设备的分辨率的不同，IOS展示图标的尺寸也不尽相同，可以通过sizes属性来配置不同的图标源，系统会根据sizes的设置智能地选取与系统分辨率相对应的图标尺寸。

**注：**默认是57x57，如果有针对设备而进行的图标配置，务必记得加清楚sizes属性，以免在retina屏上展示成小尺寸的图标，而出现模糊的不好体验。

**使用代码：**

```
<link rel="apple-touch-icon" sizes="114×114" href="touch-icon-iphone4.png" />
```

**IOS各设备图标尺寸一览表**

<table>
	<tr>
		<th>设备</th>
		<th>图标尺寸</th>
		<th>sizes设置</th>
	</tr>
	<tr>
		<td>iPhone、iTouch普通屏(1代、2代、3代)</td>
		<td>57x57</td>
		<td>sizes="57x57"</td>
	</tr>
	<tr>
		<td>iPhone、iTouch普通屏(4代及以上)retina屏</td>
		<td>114x114</td>
		<td>sizes="114x114"</td>
	</tr>
	<tr>
		<td>iPad(1代、2代)</td>
		<td>72x72</td>
		<td>sizes="72x72"</td>
	</tr>
	<tr>
		<td>iPad(the New pad)retina屏</td>
		<td>114x114</td>
		<td>sizes="114x114"</td>
	</tr>
</table>

##### 3、全屏设置

**使用代码：**

```
<meta name="apple-mobile-web-app-capable" content="yes" />
```

**注解：**
* 这里的全屏，实际上是隐藏了safari的工具栏，地址栏，以及其的各种可视栏。
* 对于系统级的顶部状态栏无法隐藏，在iphone/itouch设备上可以设置两种不同的展示状态。
* 全屏效果仅对通过桌面图标打开网站有效果，在safari中输入网址的访问是效的。

**IOS系统级的顶部状态栏设置**

```
<meta name="apple-mobile-web-app-status-bar-style" content="grey" />
<meta name="apple-mobile-web-app-status-bar-style" content="black" />
```

可以配合webapp自身的风格设置成灰色或黑色。**ipad无效！**

##### 4、启动画面设置

原生NativeApp在程序启动时会有一幅精美的画面，告诉用户应用正在加载，这是个非常好的体验，在webapp我们同样可以实现，通过apple-touch-startup-image配置：

**使用代码：**

```
<link rel="apple-touch-startup-image" href="Startup.png" />
```

启动画面与图标一样，会面临着为不同分辨率的设备精制不同尺寸图像的问题。

首先，我们先看下不同的设备，对应的启动画图的尺寸表，如下所示：

<table>
	<tr>
		<th>设备</th>
		<th>设备方向</th>
		<th>画面尺寸</th>
	</tr>
	<tr>
		<td>iPhone、iTouch普通屏(1代、2代、3代)</td>
		<td>纵向</td>
		<td>320X480</td>
	</tr>
	<tr>
		<td>iPhone、iTouch普通屏(1代、2代、3代)</td>
		<td>横向</td>
		<td>480x320</td>
	</tr>
	<tr>
		<td>iPhone、iTouch普通屏(4代及以上)retina屏</td>
		<td>纵向</td>
		<td>640 x 960</td>
	</tr>
	<tr>
		<td>iPhone、iTouch普通屏(4代及以上)retina屏</td>
		<td>横向向</td>
		<td>960x640</td>
	</tr>
	<tr>
		<td>iPad(1代、2代)</td>
		<td>纵向</td>
		<td>768X1027</td>
	</tr>
	<tr>
		<td>iPad(1代、2代)</td>
		<td>横向</td>
		<td>1027x768</td>
	</tr>
	<tr>
		<td>iPad(The New iPad)</td>
		<td>纵向</td>
		<td>1536X2048</td>
	</tr>
	<tr>
		<td>iPad(The New iPad)</td>
		<td>横向</td>
		<td>2048x1536</td>
	</tr>
</table>

**横向与纵向图片显示问题**

启动画面会面临着用户在横向还是纵向使用中打开应用的问题，所以需要设置不同的图片来满足用户的需求，可以通过css的Media Queries(媒体查询)来实现横纵图片的加载。

**使用代码：**

```
<link rel="apple-touch-startup-image" media="handheld and (orientation: portrait)" href="startup_1536x2048.png">
<link rel="apple-touch-startup-image" media="handheld and (orientation: landscape)" href="startup_2048x1536.png">
```

**注解：**

* Media Queries是css3针对设备选择而设定的一个媒体查询的概念，它比css2.0只支持Media Type（媒体）的基础上增加了更多对设备属性的查询获取，比如
	1. 浏览器窗口的宽和高；
	2. 设备的宽和高；
	3. 设备的手持方向，横向还是纵向；

**代码中media的注解：**

* media="handheld and (orientation: portrait)" 解释为设备要满足于手持设备and方向为纵向；
* orientation：设备方向：
	1. portrait：肖像模式，即纵向；
	2. landscape：景观模式，即横向；

所以，在以上代码中，只有满足了media设置条件才可以加载相对应的启动画面。

**PS：**可以利用media的查询条件对所有的设备设置不同的启动画面。

##### 5、标题设置

在设置桌面快捷方式时,系统会自动取document.title，并且限制在**13个字节**，多出的会自动隐藏掉，所以，如果是汉字的话，最好控制在**6个汉字**为宜。

图示：

![](./20120905header/edit_title.png)


##### 6、屏蔽iPhone下的拨号链接

默认情况下，IOS会将自动将连串数字转换为拨号超链接，触击后会进行拨号，很显然，这功能大部分情况是无用的，我们可以通过以下代码将其禁用：

```
<meta name="format-detection" content="telephone=no" />
```

## 三、具体执行方案
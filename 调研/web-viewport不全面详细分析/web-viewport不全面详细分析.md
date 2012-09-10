%
id: 20120906viewport
date: 2012-09-06
title: web-viewport不全面性详细分析
desc: 详细介绍了viewport的概念，作用及设备的使用方案，viewport是webapp布局实现的关键，对于构建通用性的app的布局有决定性作用。
cate: 调研
tag: webapp,web,viewport
%

#web-viewport不全面详细分析


##一、概念

###1、viewport是什么？ 
> viewport，从字面解释来看， 是可视区域，视口等意思。其实，在桌面端viewport的解释和visible area（可视区域）并不太大差异。大部分的viewport是小于visible area的。

> 在浏览器中是指能呈现网页的那部分区域，如下面所示：


* 示例：桌面浏览器

<img src="20120906viewport/web.png" alt="">


* 示例：手机浏览器

<img src="20120906viewport/wap-web.png" alt="">


###2、viewport用来做什么？

先说几个前端开发比较敏感的数字：

* 主流布局容器宽度：950，960，980；
* 主流显示器的宽度：1024，1280，1440；

> viewport是一个网页内容的可视区域，它的大小由用户设备的大小而定；

> 根据用户设备的大小，用户浏览网页的习惯以及浏览器的默认窗口大小，我们总结出了以950为主流宽度的标准布局方案，所有的主体web内容都被排版到950的容器内，这样可以满足几乎所有用户的浏览需求。

所以我们可以简单了得出以下结论：

1. viewport可以为前端开发提供一个主流化内容区域的大小参考；
2. 根据主流的viewport产出符合大多数用户的统一化的布局排版方案；

**以上，是桌面浏览器关于viewport的说明。**



##二、移动设备的viewport
> 常规的考虑下，用手机访问以桌面浏览器为参照而设计的网页，会出现很灾难的情况；

> 大部分的网页是采用流式布局来编排页面，在手机端狭小的可视区域下网页会发生布局混乱，你所能看到的仅限于手机分辨率大小的区块；

> 为了解决这一问题，苹果在移动版的safari中定义viewport meta标签；

> 它的作用就是在visible area（物理可视区域）创建一个虚拟的窗口(viewport)，交期分辨率设置成接近于桌面显示器，Apple将其定位为980px，配合viewport标签的缩放属性设置，用以将桌面端的web页面以更好的方式在移动端呈现给用户。

###viewport使用

```
<head>
…
<meta name=”viewport” content=”width=device-width, initial-scale=1.0, user-scalable=no”/>
…
</head>
```

* 新建一个meta标签，将其name定义为viewport，在content属性里配置相关值项就OK了。

###viewport配置说明

<table>
	<tbody>
		<tr>
			<td width="150">width</td><td>设置viewport的宽度，单位像素，默认980px，取值范围200到10000；也可以设置为device-width</td>
		</tr>
		<tr>
			<td width="150">height</td><td>设置viewport的高度，单位像素，默认值基于宽高的比例推算的。取值范围223到10000；也可以设置为device-height</td>
		</tr>
		<tr>
			<td width="150">initial-scale</td><td>这个值作为一个乘数，某人的计算方式是让网页适应visible area。取值的范围是从minimum-acale到maximum-scale。这个值是第一次初始缩放的比例，用户可以经行缩放，除非设置了禁止用户缩放"user-scalable=no"，用户缩放的范围是minimum-scale到maximum-scale。</td>
		</tr>
		<tr>
			<td width="150">minimum-scale</td><td>设置用户最小缩放比例，默认是0.25，取值范围是大于0，小于等于10</td>
		</tr>
		<tr>
			<td width="150">maximum-scale</td><td>设置用户最大缩放比例，默认是5.0，取值范围是大于0，小于等于10</td>
		</tr>
		<tr>
			<td width="150">user-scalable</td>
			<td>决定用户是否可以缩放viewport。设置no为禁止，默认为yes。如果设置为no，当在文本段输入文本的时候，还可以防止网页滚动。</td>
		</tr>
	</tbody>
</table>

示例：

```
width=960 或 device-width
height=1000 或 device-height
initial-scale=0.5
maximum-scale=2
minimum-scale=1
user-scalable=1 或 0 (yes 或 no)
```

###viewport的默认值
目前手机端以主流的浏览器内核为参考的viewport默认值如下所示：
```
Safari iPhone: 980px
Opera: 850px
Android WebKit: 800px
IE: 974px
```

###关于width=device-width

其实这个属性值很有意思，字面意应该是viewport宽度等于设备宽度，但在实际中不同的浏览器都给出了个定值：320px；这个值还是源于Apple，因为早期iphone的分辨率为320px × 480px，大量为iphone量身定制的网站都设置了viewport:width=device-width，并且按照宽度320px来设计制作，所以其他浏览器加入viewport支持时为了兼容性也将device-width定义为了320px。

**注解**

1. 除此之外不同移动浏览器厂商也有不同的解决方案，例如UCweb就是使用中间件技术。

2. 不同的浏览器厂商对于layout viewport的大小定义不同，详见”layout viewport的默认值”。

> 资料来源：http://www.iinterest.net/2011/05/02/about-viewport/

##三、可使用的方案参考


##四、资料参考
* [viewport不权威指南](http://www.iinterest.net/2011/05/02/about-viewport/)
* [Viewport简介](http://www.ocss3.com/Guide/5-viewport-1.html)
* [Viewport示例](http://www.ocss3.com/Guide/6-viewport-2.html)
* [设置Viewport](http://www.ocss3.com/Guide/7-change-viewport.html)
* [Viewport语法](http://www.ocss3.com/Guide/9-viewport-Syntax.html)

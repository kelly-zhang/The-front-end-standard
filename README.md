**引言：**

1. 规范目的：提高团队协作效率，利于前端后期维护，输出高质量代码，帮助前端人员养成好的编码习惯
1. 适用范围：新一站官网，触屏，渠道，车险等平台的前端HTML，LESS，CSS代码；
1. 执行要求：规范一旦确定，后续所有优化及新出页面按此执行。
1. 起始时间：2016年4月15日

**目录：**

**[一. HTML编码规则](#html)**

1. [通用规则](#ht1)
   
  1.1 文档模式
  
  1.2 明确字符编码，用不带BOM头的UTF-8
 
	1.3 有内容标签须闭合，无内容标签不闭合

  1.4 标签使用符合语义化
  
	1.5 标签嵌套正确

  1.6 标签一律采用小写编码 

  1.7 编码风格格式化
  
	1.8 图片
	
	1.9 结构，样式，行为分离
	
1. [性能考虑](#ht2)

  2.1 头部引用样式，底部引用脚本
  
	2.2 减少无用标签的使用
1. [注释](#ht3)
  
  3.1 布局结构注释
  
	3.2 特殊处理注释
1. [W3C验证](#ht4)

**[二. JSP操作规则](#jsp)**

**[三. CSS编码规范](#css)**

1. [通用规则](#css1)

  1.1 引用规范
  
	1.2 命名规范

  1.3 编写要求

  1.4 属性书写顺序 

  1.5 做好注释
1. [LESS语法](#css2)
1. [性能考虑](#css3)
1. [命名参考](#css4)
1. [浏览器兼容性 CSS hack](#css5)
1. [table样式定义](#css7)
1. [属性缩写](#css8)
1. [0和单位](#css9)
1. [十六进制尽可能使用3个字符](#css10)
1. [W3C验证](#css11)

**[四.WEB标准参考](#web)**

## <a name='html'>HTML编码规则</a>
### <a name='ht1'>1. 通用规则</a>

#### 1.1 文档模式
     统一采用标准模式，<!DOCTYPE html>，确保浏览器拥有一致的表现
      
#### 1.2 明确字符编码，用不带BOM头的UTF-8
    <meta charest="utf-8">

#### 1.3 有内容标签须闭合，无内容标签不闭合
```
* <div></div>,<p></p>,<ul></ul>,<ol></ol>,<h1></h1>...
* <br>,<hr>,<img>,<input>,<meta>,<link>...单标签不闭合，在Doctype: HTML 4.01 Strict:<br>是正确写法，而<br />是错误的
* HTML5标准下单标签推荐不闭合写法
```

#### 1.4 标签使用符合语义化
**html4，html5通用标签**
```
* div用于布局，无特殊含义
* span定义行内元素，【行内标签】
* a定义超链接，【行内标签】
* p定义段落，【行内标签】
* audio定义声音
* b定义粗体
* ...
```

**html5标准下标签，使用时调用html5标签重置的js，保证ie浏览器兼容**
```
* section定义文档中的区段
* article定义来自外部的源内容
* aside定义article以外的内容，aside内容与article内容相关
* header定义文档的页眉
* footer定义文档或节的页脚
* nav定义导航链接部分
* figure定义独立的流内容（图像、图表、照片、代码等等）
* figcation定义figure元素的标题
* ...
```
html标签查询地址：[http://www.w3school.com.cn/tags/tag_comment.asp](http://www.w3school.com.cn/tags/tag_comment.asp)
        
#### 1.5 标签嵌套正确
块级元素一般用来搭建网站架构、布局、承载内容

内联元素一般用来在网站内容中的某些细节或者部位，用以“强调、区分样式、上标、下标、锚点”等等
```
* 块级元素可以包含内联元素或某些块级元素，但内联元素不能包含块级元素，它只能包含其它内联元素。
* 块级元素不能放在p里面。
* 有几个特殊的块级元素只能包含内联元素，不能包含块级元素。如h1,h2,h3,h4,h5,h6,p,dt
* 块级元素与块级元素并列、内联元素与内联元素并列。//wrong <div><h2></h2><span></span></div>
 
```

```
<li>不可以单独使用，要与<ul>或<ol>配合使用
```
```
<dd>或<dt>要与<dl>配合使用
```

#### 1.6 标签一律采用小写编码 
```
<div>,<p>,<span>,<a>,<h1>,<ul>,<li>...
```
#### 1.7 编码风格格式化
块级子元素新起一行，并统一缩进四个空格（这里无需手动敲空格，设置你的IDE快捷键为4）

![](http://192.168.51.22:9999/API/wp-content/uploads/2016/03/ide-tab.jpg)

每个块元素、列表元素或表格元素都独占一行，每个子元素都相对于父元素进行缩进
```
<!-- good -->

<div class="top-container" title="让理赔更省心是我们的承诺！">
		<div class="top-btn">
				<a href="/claims/report" class="btnClaim" target="_blank" title="我要理赔">我要理赔</a>
				<a href="/claims/progress" class="btnTrackProgress" target="_blank" title="查询理赔进度">查询理赔进度</a>
		</div>
</div>
```

#### 1.8 图片
```
<!-- good -->
<img src="xxx" alt="yyy" width="150" height="50">禁止src为空，延迟加载的图片也要添加src属性值；添加alt属性；加上宽高占位；

<!-- wrong -->
<img src="xxx" alt="yyy" width="150px" height="50px">

<!-- bad -->
<img src="xxx" width="150" height="50">加上alt告诉它这个图像是干什么的，利于网站SEO优化

```

#### 1.9 结构，样式，行为分离

### <a name='ht2'>2. 性能考虑</a>
#### 2.1 头部引用样式，底部引用脚本
样式头部加载，可以逐步渲染页面
```
<!-- 放在头部引用 -->

<layout:override name="text_css">
		<focus:static src="/assets/css/skeleton.min.css" rel="stylesheet" type="text/css" ></focus:static>
		<focus:static src="/assets/css/claimsChannel.min.css" rel="stylesheet" type="text/css"></focus:static>
</layout:override>
```
脚本在文档加载完后载入，让用户有更好的体验
```
<!-- 放在底部引用 -->

<layout:override name="text_javascript">
		<script type="text/javascript" src="/script/claims/claimsChannel.js" charset="UTF-8"></script>
</layout:override>
```

#### 2.2 减少无用标签的使用
追求最简单的代码实现最复杂的功能
```
<!-- bad -->
<div><!-- 此div没有特殊意义 -->
		<ul>
				<li></li>
				<li></li>
		</ul>
</div>

<!-- good -->
<ul>
		<li></li>
		<li></li>
</ul>

```

### <a name='ht3'>3.注释</a>

#### 3.1 布局结构注释
不同布局模块之间注释
```
<!-- header/S -->
布局内容
<!-- header/E-->

<!-- main/S -->
布局内容
<!-- main/E -->

<!-- footer/S -->
布局内容
<!-- footer/E -->
```

#### 3.2 功能结构注释

功能模块JSP页面中注释
```
<%--  --%>
```

#### 3.2 特殊处理注释
特殊处理地方必须加好注释，如全局宽为1000的页面，新做页面宽度改为990
```
<!-- good -->
<div class="top-cont-bg">
		<div id="main" class="w1010 fn-clear">
				<div class="nav-bread"><a class="orign" href="/">新一站保险网</a><span>></span><a href="http://www.xyz.cn/claims/">理赔</a><span>></span>省心赔</div>
				<div class="new-w990"><%-- 页面主内容宽度990 --%>
				</div>
		</div>
</div>

```      
      
### <a name='ht4'>4.W3C结构验证</a>
官方验证-W3C HTML validator：[http://validator.w3.org/](http://validator.w3.org/)

也可以在浏览器中安装插件[FeHelper](https://chrome.google.com/webstore/detail/web前端助手fehelper/pkgccpejnmalmdinmhkkfafefagiiiad)，它可以协助检查你的html，css，js代码规范

## <a name='jsp'>JSP相关操作</a>

## <a name='css'>CSS编码规范</a>
### <a name='css1'>1.通用规则</a>

#### 1.1 引用规范
GULP编译 ：shift+鼠标右击，弹出命令行，直接gulp，即可编译LESS

官网assets>webpages下的样式分布图，**其中style下存放2012s老样式**

![](http://192.168.51.22:9999/API/wp-content/uploads/2016/03/assets-webpages.jpg)

#### 1.2 命名规范
```
* 非必须状态下少使用id进行命名

* js使用的class或id采用驼峰式命名及前面加上j-如：j-topBar,j-prodDetail
* js处理数据使用的class采用驼峰式命名及前面加上data-如：data-xxx

* 样式使用的class或id采用单词之前加-中划线，并且从命名上可看出它的具体含义。（其中广告词类除外，如banner，advertisement禁止使用，原因是会被搜索引擎屏蔽）

* span,p,ul,li这样的标签必须单独定义class，
	 避免如：ul li{xxx: xxx;}，原因是样式的解析是从右向左的，解析时会查找所有的li，这样影响性能，降低效率
```

#### 1.3 编写要求

```
* 不允许改动基础样式和公用LESS库

* 优雅降级保证用户有更好的体验，但要做到其他不兼容浏览器的可访问性

* 代码缩进一致，同html缩进保持4个空格，直接在我们的IDE中设置
 
* 属性名与值之间，冒号之后加一个空格，保证一致性

* 每个样式属性后面加上“;”

* 在JS操作DOM元素时减少行内样式的使用,例如style="display:none;"，需要的话，可以在公用样式中定义好，直接调用。
* 公用样式中已经定义好.ly-hide{display: none;}，可以直接调用.ly-hide，不必再新写
```
**特     必须改动基础样式和公用样式**，先发起所有前端人员参与评审预估风险-安排版本-通知测试人员参与测试-最终发版本上线

``` 
//good
.sxp-pop-cont{
		position: fixed;
		top: 50%;
		left: 50%;
		z-index: 10003;
		margin-left: -390px;
		margin-top: -300px;
		width: 730px;
		height: 545px;
		background: #fff;
		text-align: center;
}
``` 
			  
#### 1.4 属性书写顺序 
```
布局定位属性–>自身属性–>文本属性–>其他属性

* 布局定位属性: position（相应的top,right,bottom,left）、float（包括clear）、display、margin、padding、visibility、overflow...
* 自身属性主要包括: width 、 height 、 background 、 border
* 文本属性主要包括：font、color、text-align、text-decoration、text-indent...
* 其他属性包括: list-style、vertical-align、cursor、z-index(层叠顺序) 、zoom...
```
``` 
//good
.wechat-alert-bg{
		position: absolute;
		top: 0;
		left: 0;
		margin: 20px;
		width: 100%;
		height: 100%;
		background: #000;
		opacity: 0.6;
		filter: alpha(opacity=60);
		z-index: 10000;
}
```      

#### 1.5 做好注释，大区块必须做，小区块特殊处理部分加好注释
//这里是xxx内容，这种注释方法在编译时可以自动过滤掉

### <a name='css2'>2. LESS语法</a>
#### 2.1 LESS方法的使用
```
(1)变量：
@whiteColor: #ffffff;
.xxx{
		color: @whiteColor;
}

(2)混合：
.clearfix() {
		*zoom: 1;
		&:after {
		display: block;
		visibility: hidden;
		overflow: hidden;
		content: "";
		width: 0;
		height: 0;
		font-size: 0;
		clear: both;
   }
}

(3)定义参数使用：
.size(@width, @height) {
		width: @width;
		height: @height;
}
css3兼容写法使用
.box-shadow(@shadow) {
		-webkit-box-shadow: @shadow;
		-moz-box-shadow: @shadow;
		box-shadow: @shadow;
}

```	

### <a name='css3'>3. 性能考虑</a>      
#### 3.1 书写代码前，考虑好代码的重复利用率
#### 3.2 背景图片请尽可能使用sprite技术, 减小http请求, 考虑到多人协作开发, sprite可以按模块制作

### <a name='css4'>4. 命名参考：</a>
常用命名及缩写
```
头：header
内容：cont
父级包裹：container

导航：nav
主导航：mainbav
子导航：subnav
顶导航：topnav
左导航：leftbav
右导航：rightbav

侧栏：sidebar
左侧栏：leftsidebar
右侧栏：rightsidebar

栏目：column
控制整体布局宽度：wrapper
左右中：left right center
标志：logo
页面主体：main

热点：hot
新闻：news
下载：download
搜索：search
滚动：scroll
 
菜单：menu
子菜单：submenu

标签页：tab
文章列表：list
提示信息：msg
小技巧：tips
标题：title
加入：joinus
指南：guild
服务：service
登录：login
登录条：loginbar
注册：reg
状态：status
按钮：btn
摘要: summary
当前的: current
图标: icon
注释：note
投票：vote

页脚：footer
合作伙伴：partner
友情链接：friendlink
版权：copyright
```
### <a name='css5'>5. 浏览器兼容性 CSS hack</a>
**在按照规范编码的前提下，如果还存在ie下兼容问题，方可使用CSS HACK来解决问题**

需要用到hack的有：
（1）ie7下：触发haslayout，*zoom:1;

hack使用：
```
* IE7识别*，也能识别!important
* IE8识别0 例如：background:red\0
* IE9识别9 例如：background:red\9
* firefox识别!important
```


### <a name='css6'>6. table样式定义</a>
```
W3C标准中使用table，这样设置<table width="100%" border="0"></table>是错误的。
正确的可以在初始化表格样式时，放在reset中，.xx-table{border: 0;margin: 0;border-collapse: collapse;} 
.xx-table .th, .xx-table .td{padding: 0;}
```
       
### <a name='css7'>7. 属性缩写</a>
```      
.xxx{
    padinng: 0 20px;
    margin: 10px 0 5px;
}
```
### <a name='css8'>8. 0和单位</a>   
```
/* 非必要情况下，0后面单位省略 */ 
margin: 0;
padding: 0;
```
### <a name='css9'>9. 十六进制表示值，可以缩写3个字符的，用3个字符表示</a>   
```
.xx{
    color: #fff;//推荐
    color: #ffffff;//不推荐
}
```

### <a name='css10'>10. W3C样式验证</a>
官方验证-W3C CSS validator：[http://jigsaw.w3.org/css-validator/validator.html.zh-cn](http://jigsaw.w3.org/css-validator/validator.html.zh-cn)

也可以在浏览器中安装插件[FeHelper](https://chrome.google.com/webstore/detail/web前端助手fehelper/pkgccpejnmalmdinmhkkfafefagiiiad)，它可以协助检查你的html，css，js代码规范

## <a name='web'>四、WEB标准参考</a>
W3C国际站：[http://www.w3.org/](http://www.w3.org/)

W3C中国：[http://www.chinaw3c.org/](http://www.chinaw3c.org/)

W3C HTML5：[http://www.w3.org/TR/html5/](http://www.chinaw3c.org/)

W3C CSS21：[http://www.w3.org/TR/CSS21/](http://www.w3.org/TR/CSS21/)

W3C标准聚合：[http://www.w3.org/TR/](http://www.w3.org/TR/CSS21/)

whatwg：[http://www.whatwg.org/specs/web-apps/current-work/multipage/](http://www.whatwg.org/specs/web-apps/current-work/multipage/)

csswg：[http://dev.w3.org/csswg/](http://dev.w3.org/csswg/)

w3School:[http://www.w3school.com.cn/](http://www.w3school.com.cn/)



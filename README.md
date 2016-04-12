规范目的==========================提高团队协作效率，利于前端后期维护，输出高质量代码。

目录：

[一. HTML编码规则](#html)

[1. 通用规则](#ht1)

[2. 性能考虑](#ht2)

[3. 利于后期维护](#ht3)

[4. W3C验证](#ht4)

[二. JSP操作规则](#jsp)

[三. CSS编码规范](#css)

[1. 通用规则](#css1)

[2. LESS语法](#css2)

[3. 性能考虑](#css3)

[4. 命名参考](#css4)

[5. 浏览器兼容性 CSS hack](#css5)

[6. 通知IE采用识别的最高模式。](#css6)

[7. table样式定义](#css7)

[8. 属性缩写](#css8)

[10. W3C验证](#css9)

[四.WEB标准参考](#web)

## <a name='html'>HTML编码规则</a>
### <a name='ht1'>1. 通用规则</a>

#### 1.1 文档模式
      统一采用标准模式，<!DOCTYPE html>，确保浏览器拥有一致的表现。
      
#### 1.2 明确字符编码，用不带BOM头的UTF-8
      <meta charest="utf-8">

#### 1.3 标签须闭合
```
   *  <div></div>,<p></p>,<ul></ul>,<ol></ol>,<h1></h1>等等。
   *  <br>,<hr>,<img>,<input>,<meta>,<link>单标签不闭合，在Doctype: HTML 4.01 Strict:<br>是正确写法，而<br />是错误的。HTML5标准下推荐不闭合写法。
```

#### 1.4 标签使用符合语义化
	*  div用于布局，无特殊含义
	*  span定义行内元素，【行内标签】
	*  a定义超链接，【行内标签】
	*  p定义段落，【行内标签】
	*  audio定义声音
	*  b定义粗体
	*  section定义文档中的区段
	*  article定义来自外部的源内容
	*  aside定义article以外的内容，aside内容与article内容相关
	*  header定义文档的页眉
	*  footer定义文档或节的页脚
	*  nav定义导航链接部分
	*  figure定义独立的流内容（图像、图表、照片、代码等等）
	*  figcation定义figure元素的标题
	*  html标签定义查询地址：http://www.w3school.com.cn/tags/tag_comment.asp
        
        
#### 1.5 标签嵌套正确
       *  [内联元素不可以嵌套块级元素](#inline)
       *  <li>不可以单独使用，要与<ul>或<ol>配合使用
       *  <dd>或<dt>要与<dl>配合使用


#### 1.6 标签一律采用小写编码  
      div,p,span,a,h1,ul,li等等
#### 1.7 编码风格格式化
      *  块级元素新起一行，并统一缩进两个空格
      *  每个块元素、列表元素或表格元素都独占一行，每个子元素都相对于父元素进行缩进。
#### 1.8 图片
      *  推荐写法：<img src="xxx" alt="yyy">禁止src为空，延迟加载的图片也要添加src属性值；alt可以告诉它这个图像是干什么的
      *  <img src="xxx" alt="yyy" width="150px" height="50px">写法错误
      *  <img src="xxx" alt="yyy" width="150" height="50">正确
      
#### 1.9  <a name='inline'>内联元素不可以嵌套块级元素</a>
      *  块级元素一般用来搭建网站架构、布局、承载内容
      *  内联元素一般用来在网站内容中的某些细节或者部位，用以“强调、区分样式、上标、下标、锚点”等等。
      *  块级元素可以包含内联元素或某些块级元素，但内联元素不能包含块级元素，它只能包含其它内联元素。
      *  块级元素不能放在p里面。
      *  有几个特殊的块级元素只能包含内联元素，不能包含块级元素。如h1,h2,h3,h4,h5,h6,p,dt
      *  块级元素与块级元素并列、内联元素与内联元素并列。（错误的：<div><h2></h2><span></span></div>)

### <a name='ht2'>2. 性能考虑</a>
#### 2.1 头部引用样式，底部引用脚本
      *  样式头部加载，可以逐步渲染页面
      *  脚本在文档加载完后载入，让用户有更好的体验
      推荐写法
      
      不推荐写法
#### 2.2 减少无用标签的使用
      追求最简单的代码实现最复杂的功能
      加例子：

### <a name='ht3'>3.利于后期维护</a>
#### 3.1 结构，样式，行为分离
       实例代码---截图

#### 3.2 做好注释
      *  不同模块之间做好注释，例如：<!-- header -->，<!-- footer -->
      *  特殊处理地方必须加好注释，如整体宽为1000，而后来新页面改为990，
         例如：<%-- 页面主内容宽度990 --%>
         截图
      
### <a name='ht4'>4.W3C结构验证</a>
      W3C HTML validator：[http://validator.w3.org/](http://validator.w3.org/)

## <a name='jsp'>JSP相关操作</a>
#### 1. 完整页面编写时，确保头部存放推广代码
```
<%--推广代码 --%>
<layout:override name="title">新一站省心赔_保险快速理赔_保险省心理赔_保险理赔新标准_新一站保险网</layout:override>
<layout:override name="keywords">省心赔，快速理赔，理赔服务，轻松理赔，理赔查询</layout:override>
<layout:override name="description">新一站保险网会员专属理赔服务——“省心赔”，在线操作简单、理赔进度随时查询、理赔专家1对1为您服务，保险理赔流程的新标准，实时报案，实时受理让您的理赔更省心。
</layout:override>
```
#### 2. 引用样式选择压缩过的样式
```
<layout:override name="text_css">
  <focus:static src="/assets/css/claimsChannel.min.css" rel="stylesheet"></focus:static>
</layout:override>
```

#### 3.协助开发检查JSP标签是否嵌套正确
      之前遇到过的问题主要是jsp标签闭合的位置错误，导致静态页面兼容性问题。

#### 4. 脚本使用放入JSP标签中
```
<layout:override name="text_javascript">
  <script type="text/javascript" src="/script/jquery-1.4.2.js" charset="UTF-8"></script>
</layout:override>
```

## <a name='css'>CSS编码规范</a>
### <a name='css1'>1.通用规则</a>

#### 1.1 引用规范
       *  GULP编译  ---截图
       *  assets下的样式分布图 ---截图

#### 1.2 命名规范
      *  私有页面定义的class，应该有它具体的含义，遇到按钮可以定义如：prodListBtn或prod-list-btn;这里不允许出现.btn这样的class
      *  span,p,li这样的标签最好单独定义class，避免如：
         ul li{xxx:xxx;}，原因是样式的解析是从右向左的，解时会查找所有的li，这样影响性能，降低效率
      *  id命名简短有意义，可采用中划线命名或驼峰命名
      *  约定js使用的class使用驼峰式命名如：topBar,prodDetail
      *  样式使用单词之前加-中划线，并且命名上可看出它的含义，广告词类除外，如banner，advertisement禁止使用，原因是会被搜索引擎屏蔽
#### 1.3 编写要求
      *  尽量不随便改动基础样式和公用LESS库，如果需要，必须全站做好检查，可以在大版本发布前通知测试协助检查
      *  优雅降级可以保证用户有更好的体验，但要做到其他依然存在使用的浏览器的可访问性
      *  代码缩进一致
      *  属性名与值之间，冒号之后加一个空格，保证一致性
``` 
截图
``` 
      *  每个样式属性后面加上“;”
      *  尽量不使用行内样式,需要的话，可以在公用样式中定义好，直接调用。例如：`.ly-hide{display:none;}，可以直接调用.ly-hide，js中取出class来控制`
			  
#### 1.4 属性书写顺序 
      建议：布局定位属性–>自身属性–>文本属性–>其他属性
      * 布局定位属性主要包括: `margin、padding、float（包括clear）、position（相应的top,right,bottom,left）、display、visibility、overflow等`
      * 自身属性主要包括: `width & height & background & border`
      * 文本属性主要包括：`font、color、text-align、text-decoration、text-indent等`
      * 其他属性包括: `list-style(列表样式)、vertical-vlign、cursor、z-index(层叠顺序) 、zoom等`
``` 
截图
```      

#### 1.6 做好注释，大区块必须做，小区块特殊处理部分加好注释
       //这里是xxx内容，编译时可以过滤掉注释

### <a name='css2'>2. LESS语法</a>
#### 2.1 LESS方法的使用
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
					content: "";
					width: 0;
					height: 0;
					font-size: 0;
					clear: both;
					visibility: hidden;
					overflow: hidden;
			}
	   }
        (3)定义参数使用：
		 .size(@width, @height) {
		    width: @width;
	        height: @height;
	   }
		.box-shadow(@shadow) {
				-webkit-box-shadow: @shadow;
				-moz-box-shadow: @shadow;
				box-shadow: @shadow;
		}
	(4)嵌套：
	#id{
	    .topBar{
	        margin：0；
	        width：100px;
	        height:0;
	    }
	}
	生成：
	#id .topBar{margin：0； width：100px; height:0;}
		

### <a name='css3'>3. 性能考虑</a>      
#### 3.1 书写代码前，考虑好代码的重复利用率
#### 3.2 背景图片请尽可能使用sprite技术, 减小http请求, 考虑到多人协作开发, sprite可以按模块制作

### <a name='css4'>4. 命名参考：</a>
      （一）常用命名
       头：header
       内容：content/container
       导航：nav
       主导航：mainbav
       子导航：subnav
       顶导航：topnav
       左导航：leftsidebar
       右导航：rightsidebar
       侧栏：sidebar
       栏目：column
       页面外围控制整体布局宽度：wrapper
       左右中：left right center
       标志：logo
       页面主体：main
       热点：hot
       新闻：news
       下载：download
       菜单：menu
       子菜单：submenu
       搜索：search
       滚动：scroll
       标签页：tab
       文章列表：list
       提示信息：msg
       小技巧：tips
       栏目标题：title
       加入：joinus
       指南：guild
       服务：service
       登录：login
       登录条：loginbar
       注册：regsiter
       状态：status
       按钮：btn
       摘要: summary
       当前的: current
       小技巧：tips
       图标: icon
       注释：note
       投票：vote
       页脚：footer
       合作伙伴：partner
       友情链接：friendlink
       版权：copyright

### <a name='css5'>5. 浏览器兼容性 CSS hack</a>
       先不以为前提，看看是不是编码不符合规范，找寻其他解决办法
       标识区别：区别IE6,IE7,IE8,FF。
       1. IE都能识别*
       2. IE6能识别*，但不能识别 !important; IE6在样式前面加_
       3. IE7能识别*，也能识别!important
       4. IE8能识别9 例如：background:red\9
       5. firefox不能识别*，但能识别!important


### <a name='css7'>7. table样式定义</a>
       W3C标准中table，这样设置<table width="100%" border="0"></table>是错误的。
       正确的可以在初始化表格样式时，放在reset中，.xx-table{border: 0;margin: 0;border-collapse: collapse;} 
       .xx-table .th, .xx-table .td{padding:0;}
       
### <a name='css8'>8. 属性缩写</a>
```      
.xxx{
    padinng: 0 20px;
    margin: 10px 0 5px;
}
```
### <a name='css9'>9. 0和单位</a>   
```
/* 非必要情况下，0后面单位省略 */ 
margin: 0;
padding: 0;
```
### <a name='css10'>10. 十六进制尽可能使用3个字符</a>   
```
.xx{
    color: #fff;//推荐
    color: #ffffff;//不推荐
    
}
```

### <a name='css10'>10. W3C样式验证</a>
        W3C CSS validator：[http://jigsaw.w3.org/css-validator/validator.html.zh-cn](http://jigsaw.w3.org/css-validator/validator.html.zh-cn)

## <a name='web'>四、WEB标准参考</a>
  W3C国际站：[http://www.w3.org/](http://www.w3.org/)
  
  W3C中国：[http://www.chinaw3c.org/](http://www.chinaw3c.org/)
  
  W3C HTML5：[http://www.w3.org/TR/html5/](http://www.chinaw3c.org/)
  
  W3C CSS21：[http://www.w3.org/TR/CSS21/](http://www.w3.org/TR/CSS21/)
  
  W3C标准聚合：[http://www.w3.org/TR/](http://www.w3.org/TR/CSS21/)
  
  whatwg：[http://www.whatwg.org/specs/web-apps/current-work/multipage/](http://www.whatwg.org/specs/web-apps/current-work/multipage/)
  
  csswg：[http://dev.w3.org/csswg/](http://dev.w3.org/csswg/)
  
  w3School:[http://www.w3school.com.cn/](http://www.w3school.com.cn/)



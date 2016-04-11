规范目的==========================提高团队协作效率，利于前端后期维护，输出高质量代码。

目录：

[一. HTML编码规则](#html)
1. 通用规则
2. 性能考虑
3. 利于后期维护
4. W3C验证

[二. JSP操作规则](#jsp)

[三. CSS编码规范](#css)
1. 通用规则
2. LESS语法
3. 性能考虑
4. 命名参考
5. 浏览器兼容性 CSS hack
6. 通知IE采用识别的最高模式。
7. table样式定义

四.WEB标准参考

## <a name='html'>HTML编码规则</a>
### 1. 通用规则

#### 1.1 文档模式
      统一采用标准模式，<!DOCTYPE html>，确保浏览器拥有一致的表现。
      
#### 1.2 明确字符编码UTF-8，精简编码形式
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
		*  ...
        
        
#### 1.5 标签嵌套正确
```      
   *  内联元素不可以嵌套块级元素如：<a><div></div></a>错误；<a><span></span></a>正确
   *  <li>不可以单独使用，要与<ul>或<ol>配合使用
   *  <dd>或<dt>要与<dl>配合使用
```

#### 1.6 标签一律采用小写编码  

#### 1.7 编码风格格式化
      块级元素新起一行，并统一缩进两个空格
#### 1.8 图片需要加alt属性
      <img src="xxx" alt="yyy"/>
#### 1.9 图片html定义
      *  <img src="xxx" alt="yyy" width="150px" height="50px"/>是错误的
      *  <img src="xxx" alt="yyy" width="150" height="50"/>正确

### 2. 性能考虑
#### 2.1 头部引用样式，底部引用脚本
      *  样式头部加载可以逐步渲染页面
      *  让你的脚本在你的文档加载完成后载入，让用户有更好的体验
#### 2.2 减少无用标签的使用
      最简单的代码实现最复杂的功能

### 3.利于后期维护
#### 3.1 结构，样式，行为分离
      尽量不使用行内样式,需要的话，可以在公用样式中定义好，直接调用。

#### 3.2 做好注释
      *  不同模块之间做好注释，例如：<%-- 弹出层 --%>
      *  特殊处理地方必须加好注释，如整体宽为1000，而后来新页面改为990，例如：<%-- 页面主内容宽度990 --%>
      
### 4.W3C验证
      W3C HTML validator：http://validator.w3.org/

## <a name='jsp'>JSP操作规则</a>
#### 1. 完整页面编写时，确保头部存放推广代码
      <%--推广代码 --%>
        <layout:override name="title">新一站省心赔_保险快速理赔_保险省心理赔_保险理赔新标准_新一站保险网</layout:override>
		<layout:override name="keywords">省心赔，快速理赔，理赔服务，轻松理赔，理赔查询</layout:override>
		<layout:override name="description">新一站保险网会员专属理赔服务——“省心赔”，在线操作简单、理赔进度随时查询、理赔专家1对1为您服务，保险理赔流程的新标准，实时报案，实时受理让您的理赔更省心。
		</layout:override>  
#### 2. 引用样式调用压缩过的样式
	    <layout:override name="text_css">
		  <focus:static src="/assets/css/claimsChannel.min.css" rel="stylesheet" type="text/css"></focus:static>
		</layout:override>

#### 3.协助开发检查JSP标签是否嵌套正确
	    目的是不破坏HTML标签的完整闭合

#### 4. 脚本使用放入JSP标签中
     <layout:override name="text_javascript">
       <script type="text/javascript" src="/script/jquery-1.4.2.js" charset="UTF-8"></script>
     </layout:override>


## <a name='css'>CSS编码规范</a>
### 1.通用规则

#### 1.1 引用规范
       *  GULP编译
       *  assets下的样式分布图

#### 1.2 命名规范
      *  标签私有定义class,私有页面中不允许定义.btn这样的class
      *  span,p,li这样的标签最好单独定义class，避免如：ul li{xxx:xxx;}，原因是样式的解析是从右向左的，解释时会查找所有的li一遍，这样影响性能
      *  中划线
      *  驼峰式命名
#### 1.3 编写要求
      * 尽量不顺便改动基础样式和公用LESS库
      * 优雅降级保证用户可以有更好的体验，但要保证其他存在浏览器的可使用性
      * 代码缩进一致
      * 每个样式属性后面加上“;”
			  
#### 1.4 属性书写顺序 
      建议：布局定位属性–>自身属性–>文本属性–>其他属性
      * 布局定位属性主要包括: `margin、padding、float（包括clear）、position（相应的top,right,bottom,left）、display、visibility、overflow等
      * 自身属性主要包括: width & height & background & border
      * 文本属性主要包括：font、color、text-align、text-decoration、text-indent等
      * 其他属性包括: list-style(列表样式)、vertical-vlign、cursor、z-index(层叠顺序) 、zoom等

#### 1.5 样式表种有中文字体，务必转成unicode码, 以避免编码错误时乱码
       font-family:"microsoft yahei"; 
#### 1.6 做好注释，大区块必须做，小区块特殊处理部分加好注释
		//这里是xxx内容，编译时可以过滤掉注释

### 2. LESS语法
#### 2.1 LESS方法的使用
    (1)变量：
		 @whiteColor:#ffffff;
		 .xxx{
		    color:@whiteColor;
		 }
    (2)混合：
			.clearfix() {
			*zoom:1;
			&:after {
					display:block;
					content:"";
					width:0;
					height:0;
					font-size:0;
					clear:both;
					visibility:hidden;
					overflow:hidden;
			}
	   }
		 (3)定义参数使用，
		 .size(@width, @height) {
		    width: @width;
	        height: @height;
	   }
		.box-shadow(@shadow) {
				-webkit-box-shadow: @shadow;
				-moz-box-shadow: @shadow;
				box-shadow: @shadow;
		}
		 
		

### 3. 性能考虑      
#### 3.1 书写代码前，考虑好代码的重复利用率
#### 3.2 背景图片请尽可能使用sprite技术, 减小http请求, 考虑到多人协作开发, sprite可以按模块制作

### 4. 命名参考：
      （一）常用命名
       头：header
       内容：content/container
       尾：footer
       导航：nav
       侧栏：sidebar
       栏目：column
       页面外围控制整体布局宽度：wrapper
       左右中：left right center
       登录条：loginbar
       标志：logo
       广告：banner
       页面主体：main
       热点：hot
       新闻：news
       下载：download
       子导航：subnav
       菜单：menu
       子菜单：submenu
       搜索：search
       友情链接：friendlink
       页脚：footer
       版权：copyright
       滚动：scroll
       内容：content
       标签页：tab
       文章列表：list
       提示信息：msg
       小技巧：tips
       栏目标题：title
       加入：joinus
       指南：guild
       服务：service
       注册：regsiter
       状态：status
       投票：vote
       合作伙伴：partner
       
       
       (二)id的命名:
       (1)页面结构
       容器: container
       页头：header
       内容：content/container
       页面主体：main
       页尾：footer
       导航：nav
       侧栏：sidebar
       栏目：column
       页面外围控制整体布局宽度：wrapper
       左右中：left right center
      
       (2)导航
       导航：nav
       主导航：mainbav
       子导航：subnav
       顶导航：topnav
       边导航：sidebar
       左导航：leftsidebar
       右导航：rightsidebar
       菜单：menu
       子菜单：submenu
       标题: title
       摘要: summary
      
       (3)功能
       标志：logo
       广告：banner
       登陆：login
       登录条：loginbar
       注册：regsiter
       搜索：search
       功能区：shop
       标题：title
       加入：joinus
       状态：status
       按钮：btn
       滚动：scroll
       标签页：tab
       文章列表：list
       提示信息：msg
       当前的: current
       小技巧：tips
       图标: icon
       注释：note
       指南：guild
       服务：service
       热点：hot
       新闻：news
       下载：download
       投票：vote
       合作伙伴：partner
       友情链接：link
       版权：copyright


### 5. 浏览器兼容性 CSS hack
       标识区别：区别IE6,IE7,IE8,FF。
       1. IE都能识别* ; 标准浏览器(如FF)不能识别*；
       2. IE6能识别*，但不能识别 !important; IE6在样式前面加_
       3. IE7能识别*，也能识别!important;
       4. IE8能识别9 例如：background:red 9;
       5. firefox不能识别*，但能识别!important;

### 6. 通知IE采用识别的最高模式。(特殊情况使用，待斟酌)
       <meta http-equiv="X-UA-Compatible" content="IE=Edge">

### 7. table样式定义
       W3C标准中table，这样设置<table width="100%" border="0"></table>是错误的。
       正确的可以在初始化表格样式时，放在reset中，table{border:0;margin:0;border-collapse:collapse;} table th, table td{padding:0;}

### 8. W3C验证
        W3C CSS validator：http://jigsaw.w3.org/css-validator/validator.html.zh-cn

## WEB标准参考
  W3C国际站：http://www.w3.org/
  
  W3C中国：http://www.chinaw3c.org/
  
  W3C HTML5：http://www.w3.org/TR/html5/
  
  W3C CSS21：http://www.w3.org/TR/CSS21/
  
  W3C标准聚合：http://www.w3.org/TR/
  
  whatwg：   http://www.whatwg.org/specs/web-apps/current-work/multipage/
  
  csswg：http://dev.w3.org/csswg/



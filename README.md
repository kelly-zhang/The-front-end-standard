#新一站官网前端编码规范
 规范目的：提高团队协作效率，利于前端后期维护，输出高质量代码。

##HTML编码规则
###1. <!DOCTYPE html>。
      添加标准模式，确保浏览器拥有一致的表现。
      
###2. UTF-8编码。`<meta charest="utf-8">`

###3. 标签闭合。`<div></div>,<br>单标签不闭合`

###4. 标签使用符合语义化。
      *  每个标签元素都有符合的意义和语境。
      *  div使用于布局，
      *  span行内元素，
      *  a超链接，
      *  p定义段落，
      *  audio定义声音，
      *  b定义粗体，
      *  section定义文档中的区段，
      *  article定义来自外部的源内容，
      *  aside定义，
      *  hgroup定义，
      *  header定义，
      *  footer定义，
      *  nav定义，
      *  figure定义，
      *  figcation定义 等等 
        
        
###5. 标签嵌套正确，
      <a><div></div></a>错误；<a><span></span></a>正确
      
###6. 结构，样式，行为分离。
###7. 头部引用样式，底部引用脚本。
###8. 代码格式化。
      块级元素新起一行，并缩进两个空格
      
###9. 内联元素不能包含块级元素

###10. 可通过W3C验证你的代码
       W3C CSS validator：http://jigsaw.w3.org/css-validator/
---

##CSS编码规范
###1. 引用规范
###2. 命名规范
###3. 编写要求
      一、尽量不顺便改动基础样式和公用css库
      二、优雅降级保证用户可以有更好的体验，但要保证其他存在使用浏览器的可使用性。

###4. LESS语法
###5. 标签私有定义class
###6. 属性书写顺序 
      建议：遵循布局定位属性–>自身属性–>文本属性–>其他属性
      布局定位属性主要包括: `margin、padding、float（包括clear）、position（相应的       top,right,bottom,left）、display、visibility、overflow等；`
      `自身属性主要包括: width & height & background & border;    `             `文本属性主要包括：font、color、text-align、text-decoration、text-indent等；`
     ` 其他属性包括: list-style(列表样式)、vertical-vlign、cursor、z-index(层叠顺序) 、zoom等。`
      
###7. 书写代码前，考虑好代码的重复利用率

###8. 样式表种有中文字体，务必转成unicode码, 以避免编码错误时乱码;

###9. 背景图片请尽可能使用sprite技术, 减小http请求, 考虑到多人协作开发, sprite按模块制作;
###10. 使用table时，初始化表格样式放在reset中，`table{border:0;margin:0;border-collapse:collapse;} table th, table td{padding:0;}`
###11. 做好注释，大区块必须做，小区块特殊处理加好注释。
###12. 代码缩进一致。
###13. 命名规则：
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
       
       (二)注释的写法:
       /* Footer */
       内容区
       /* End Footer */
       
       (三)id的命名:
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
       版权：copyright\

###14. 每个样式属性后面加上“;”

###15. 浏览器兼容性 CSS hack
       一、标识区别：区别IE6,IE7,IE8,FF。1. IE都能识别* ; 标准浏览器(如FF)不能识别*；
       2. IE6能识别*，但不能识别 !important; IE6在样式前面加_
       3. IE7能识别*，也能识别!important;
       4. IE8能识别\ 9 例如：background:red \9;
       5. firefox不能识别*，但能识别!important;
       
###16. 代码写得足够标准，可以避免出现很多奇怪的问题出现。
###17. 通知IE采用识别的最高模式。
> <meta http-equiv="X-UA-Compatible" content="IE=Edge">

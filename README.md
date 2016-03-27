#新一站官网前端编码规范

> 规范目的：提高团队协作效率，利于前端后期维护，输出高质量代码。

##HTML编码规则
1. <!DOCTYPE html>。
2. UTF-8。```<meta charest="utf-8">```
3. 标签闭合。```<div></div>,<br>单标签不闭合```
4. 标签使用符合语义化。每个标签元素都有符合的意义和语境。```div使用于块级结构，span行内元素，a超链接，p定义段落，audio定义声音，b定义粗体等等```
5. 标签嵌套正确，`<a><div></div></a>`错误；`<a><span></span></a>`正确
6. 结构，样式，行为分离。
7. 头部引用样式，底部引用脚本。
8. 代码格式化。```块级元素新起一行并缩进```
9. 可通过W3C验证你的代码


##CSS编码规范
1. 引用规范
2. 命名规范
3. 编写规范
5. LESS语法
6. 标签私有定义class
7. 属性书写顺序 
建议：遵循布局定位属性–>自身属性–>文本属性–>其他属性
布局定位属性主要包括: margin、padding、float（包括clear）、position（相应的 top,right,bottom,left）、display、visibility、overflow等；自身属性主要包括: width & height & background & border; 文本属性主要包括：font、color、text-align、text-decoration、text-indent等；其他属性包括: list-style(列表样式)、vertical-vlign、cursor、z-index(层叠顺序) 、zoom等.我所列出的这些属性只是最常用到的
8. 书写代码前，考虑好代码的重复利用率
9. 样式表中中文字体，务必转成unicode码, 以避免编码错误时乱码;
10. 背景图片请尽可能使用sprite技术, 减小http请求, 考虑到多人协作开发, sprite按模块制作;
11. 使用table时，初始化表格样式放在reset中，table{border:0;margin:0;border-collapse:collapse;} table th, table td{padding:0;}
12. 做好注释，大区块必须做，小区块特殊处理加好注释。
13. 代码缩进一致。


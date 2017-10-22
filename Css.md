1.对WEB标准以及W3C的理解与认识
- 标签闭合、标签小写、不乱嵌套、提高搜索机器人搜索几率、使用外 链css和js脚本、结构行为表现的分离、文件下载与页面速度更快、内容能被更多的用户所访问、内容能被更广泛的设备所访问、更少的代码和组件，容易维 护、改版方便，不需要变动页面内容、提供打印版本而不需要复制内容、提高网站易用性；

2.xhtml和html有什么区别
- HTML是一种基本的WEB网页设计语言，XHTML是一个基于XML的置标语言，最主要的不同：
XHTML 元素必须被正确地嵌套。
XHTML 元素必须被关闭。
标签名必须用小写字母。
XHTML 文档必须拥有根元素。

3.Doctype? 严格模式与混杂模式-如何触发这两种模式，区分它们有何意义? 
- 用于声明文档使用那种规范（html/Xhtml）一般为 严格 过度 基于框架的html文档
加入XMl声明可触发，解析方式更改为IE5.5 拥有IE5.5的bug

4.行内元素有哪些?块级元素有哪些?CSS的盒模型?
- 块级元素：div p h1 h2 h3 h4 form ul
行内元素: a b br i span input select
Css盒模型:内容，border ,margin，padding

5.CSS引入的方式有哪些? link和@import的区别是?
- 内联 内嵌 外链 导入
区别 ：同时加载
前者无兼容性，后者CSS2.1以下浏览器不支持
Link 支持使用javascript改变样式，后者不可

6.CSS选择符有哪些?哪些属性可以继承?优先级算法如何计算?内联和important哪个优先级高?
- 标签选择符 类选择符 id选择符
继承不如指定 Id>class>标签选择
后者优先级高

7.前端页面有哪三层构成，分别是什么?作用是什么?
- 结构层 Html 表示层 CSS 行为层 js

8.css的基本语句构成是?
- 选择器{属性1:值1;属性2:值2;……}

9.你做的页面在哪些流览器测试过?这些浏览器的内核分别是什么?
- Ie(Ie内核) 火狐（Gecko） 谷歌（webkit） opear(Presto)

10.写出几种IE6 BUG的解决方法
- 1.双边距BUG float引起的 使用display
2.3像素问题 使用float引起的 使用dislpay:inline -3px
3.超链接hover 点击后失效 使用正确的书写顺序 link visited hover active
4.Ie z-index问题 给父级添加position:relative
5.Png 透明 使用js代码 改
6.Min-height 最小高度 ！Important 解决’
7.select 在ie6下遮盖 使用iframe嵌套
8.为什么没有办法定义1px左右的宽度容器（IE6默认的行高造成的，使用over:hidden,zoom:0.08 line-height:1px）

11.标签上title与alt属性的区别是什么?
- Alt 当图片不显示是 用文字代表。
Title 为该属性提供信息

12.描述css reset的作用和用途。
- Reset重置浏览器的css默认属性 浏览器的品种不同，样式不同，然后重置，让他们统一

13.解释css sprites，如何使用。
- Css 精灵 把一堆小的图片整合到一张大的图片上，减轻服务器对图片的请求数量

14.浏览器标准模式和怪异模式之间的区别是什么?
- 盒子模型 渲染模式的不同
使用 window.top.document.compatMode 可显示为什么模式

15.什么是语义化的HTML?
- 直观的认识标签 对于搜索引擎的抓取有好处

16.清除浮动的几种方式，各自的优缺点
- 1.使用空标签清除浮动 clear:both（理论上能清楚任何标签，，，增加无意义的标签）
2.使用overflow:auto（空标签元素清除浮动而不得不增加无意代码的弊端,,使用zoom:1用于兼容IE）
3.是用afert伪元素清除浮动(用于非IE浏览器)

17.IE与FF脚本兼容性问题
　- (1) window.event：
　　表示当前的事件对象，IE有这个对象，FF没有，FF通过给事件处理函数传递事件对象
　　(2) 获取事件源
　　IE用srcElement获取事件源，而FF用target获取事件源
　　(3) 添加，去除事件
　　IE：element.attachEvent(“onclick”, function) element.detachEvent(“onclick”, function)
　　FF：element.addEventListener(“click”, function, true) element.removeEventListener(“click”, function, true)
　　(4) 获取标签的自定义属性
　　IE：div1.value或div1[“value”]
　　FF：可用div1.getAttribute(“value”)
　　(5) document.getElementByName()和document.all[name]
　　IE;document.getElementByName()和document.all[name]均不能获取div元素
　　FF：可以
　　(6) input.type的属性
　　IE：input.type只读
　　FF：input.type可读写
　　(7) innerText textContent outerHTML
　　IE：支持innerText, outerHTML
　　FF：支持textContent
　　(8) 是否可用id代替HTML元素
　　IE：可以用id来代替HTML元素
　　FF：不可以
　　这里只列出了常见的，还有不少，更多的介绍可以参看JavaScript在IE浏览器和Firefox浏览器中的差异总结
  
18.如何添加html元素的事件,有几种方法.
- (1) 为HTML元素的事件属性赋值
　　(2) 在JS中使用ele.on*** = function() {…}
　　(3) 使用DOM2的添加事件的方法 addEventListener或attachEvent
  
 19. 为什么要使用Div+CSS布局
- 形式与内容分离
大大减少页面代码，提高页面浏览速度
结构清晰，有利于SEO
缩短改版时间， 布局更方便
一次设计，多次使用

20. Block元素的特点是什么?哪些元素默认为Block元素
- 总是在新行上开始；
高度，行高以及顶和底边距都可控制；
宽度缺省是它的容器的100%，除非设定一个宽度

21.inline元素的特点是什么?哪些元素属于inline元素?
- 和其他元素都在一行上；
高，行高及顶和底边距不可改变；
宽度就是它的文字或图片的宽度，不可改变。





  # 前端面试题 #
  一、JS闭包。
f = function() {return true;}; 
g = function() {return false;}; 
(function() { 
if (g() && [] == ![]) { 
f = function f() {return false;}; 
function g() {return true;} 
} 
})(); 
alert(f()); // true or false ? 
－－－－－－－－－－－－－－－－－－－－－－－－
答案：
(function() { 
if (g() && [] == ![]) { 
//应该看成if((g() && [] )== ![]) 
//因为g()是false后面那个&&[]就没起作用 整个都是false 
//![]也是false 所以if成立 进入if块内 
f = function f() {return false;}; 
//重新定义f 
function g() {return true;} 
//这句没用 
} 
})(); 
alert(f()); 
//false 
二、截取字符串abcdefg的efg
<p id="text">abcdefg</p>
<script type="text/javascript">
var mytext=document.getElementByIdx_x_x_x("text");
var myvalue=mytext.innerHTML;
var jiequ=myvalue.substring(myvalue.length-3,myvalue.length);
alert(jiequ)
</script>
三、写出一下运算结果
alert(typeof(null)) // object
alert(typeof(undefined)) // undefined
alert(typeof(NaN)) // number
alert(NaN==undefined) // false
alert(NaN==NaN) // false
var str="123abc";
alert(typeof(str++)) // number
alert(str) // string
四、写出函数DateDemo的返回结果，系统时间假定为今天
function DateDemo(){
var d, s="今天日期是：";
d = new Date();
s += d.getMonth() + "/";
s += d.getDate() + "/";
s += d.getYear();
return s;
}
结果：今天日期是：7/17/2010
五、写出程序运行的结果？
for(i=0, j=0; i<10, j<6; i++, j++){
k = i + j;
}
22.编写一个数组去重的方法
function oSort(arr)
{
var result ={};
var newArr=[];
for(var i=0;i<arr.length;i++)
{
if(!result[arr])
{
newArr.push(arr)
result[arr]=1
}
}
return newArr
}
数组去重：
        var s = [0,2,3,4,4,0,2];
        for(var i=0,o={},tmp=[],count=0,l=s.length;i<l;i++){
                if(o[s[i]]){
                        count++;
                }else{
                        o[s[i]]=1;
                        tmp.push(s[i])
                }
        }
        alert(count);
        alert(tmp)
12.写一个获取非行间样式的函数

function getStyle(obj,attr,value)
{
if(!value)
{
if(obj.currentStyle)
{
return obj.currentStyle(attr)
}
else
{
obj.getComputedStyle(attr,false)
}
}
else
{
obj.style[attr]=value
}
}
　1, 判断字符串是否是这样组成的，第一个必须是字母，后面可以是字母、数字、下划线，总长度为5-20
　　var reg = /^[a-zA-Z][a-zA-Z_0-9]{4,19}$/;
　　reg.test("a1a__a1a__a1a__a1a__");
　　2，截取字符串abcdefg的efg
　　var str = "abcdefg";
　　if (/efg/.test(str)) {
　　var efg = str.substr(str.indexOf("efg"), 3);
　　alert(efg);
　　}
　　3，判断一个字符串中出现次数最多的字符，统计这个次数
　　//将字符串的字符保存在一个hash table中，key是字符，value是这个字符出现的次数
　　var str = "abcdefgaddda";
　　var obj = {};
　　for (var i = 0, l = str.length; i < l; i++) {
　　var key = str[i];
　　if (!obj[key]) {
　　obj[key] = 1;
　　} else {
　　obj[key]++;
　　}
　　}
　　/*遍历这个hash table，获取value最大的key和value*/
　　var max = -1;
　　var max_key = "";
　　var key;
　　for (key in obj) {
　　if (max < obj[key]) {
　　max = obj[key];
　　max_key = key;
　　}
　　}
　　alert("max:"+max+" max_key:"+max_key);
　　4，IE与FF脚本兼容性问题
　　(1) window.event：
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
　　5，规避javascript多人开发函数重名问题
　　(1) 可以开发前规定命名规范，根据不同开发人员开发的功能在函数前加前缀
　　(2) 将每个开发人员的函数封装到类中，调用的时候就调用类的函数，即使函数重名只要类名不重复就ok
　　6，javascript面向对象中继承实现
　　javascript面向对象中的继承实现一般都使用到了构造函数和Prototype原型链，简单的代码如下：
　　function Animal(name) {
　　this.name = name;
　　}
　　Animal.prototype.getName = function() {alert(this.name)}
　　function Dog() {};
　　Dog.prototype = new Animal("Buddy");
　　Dog.prototype.constructor = Dog;
　　var dog = new Dog();
　　7，FF下面实现outerHTML
　　FF不支持outerHTML，要实现outerHTML还需要特殊处理
　　思路如下：
　　在页面中添加一个新的元素A，克隆一份需要获取outerHTML的元素，将这个元素append到新的A中，然后获取A的innerHTML就可以了。
　　SPANDIV
　　SPAN
　　P
　　8，编写一个方法 求一个字符串的字节长度
　　假设：
　　一个英文字符占用一个字节，一个中文字符占用两个字节
　　function GetBytes(str){
　　var len = str.length;
　　var bytes = len;
　　for(var i=0; i
　　if (str.charCodeAt(i) > 255) bytes++;
　　}
　　return bytes;
　　}
　　alert(GetBytes("你好,as"));
　　9，编写一个方法 去掉一个数组的重复元素
　　var arr = [1 ,1 ,2, 3, 3, 2, 1];
　　Array.prototype.unique = function(){
　　var ret = [];
　　var o = {};
　　var len = this.length;
　　for (var i=0; i
　　var v = this[i];
　　if (!o[v]){
　　o[v] = 1;
　　ret.push(v);
　　}
　　}
　　return ret;
　　};
　　alert(arr.unique());
　　10，写出3个使用this的典型应用
　　(1)在html元素事件属性中使用，如
　　(2)构造函数
　　function Animal(name, color) {
　　this.name = name;
　　this.color = color;
　　}
　　(3)
　　(4)CSS expression表达式中使用this关键字
　　div element
　　12，如何显示/隐藏一个DOM元素?
　　el.style.display = "";
　　el.style.display = "none";
　　el是要操作的DOM元素
　　13，JavaScript中如何检测一个变量是一个String类型?请写出函数实现
　　String类型有两种生成方式：
　　(1)Var str = “hello world”;
　　(2)Var str2 = new String(“hello world”);
　　function IsString(str){
　　return (typeof str == "string" || str.constructor == String);
　　}
　　var str = "";
　　alert(IsString(1));
　　alert(IsString(str));
　　alert(IsString(new String(str)));
　　14，网页中实现一个计算当年还剩多少时间的倒数计时程序，要求网页上实时动态显示“××年还剩××天××时××分××秒”
　　15，补充代码，鼠标单击Button1后将Button1移动到Button2的后面
　　16，JavaScript有哪几种数据类型
　　简单：Number，Boolean，String，Null，Undefined
　　复合：Object，Array，Function
　　17，下面css标签在JavaScript中调用应如何拼写，border-left-color，-moz-viewport
　　borderLeftColor
　　mozViewport
　　18，JavaScript中如何对一个对象进行深度clone
　　function cloneObject(o) {
　　if(!o || 'object' !== typeof o) {
　　return o;
　　}
　　var c = 'function' === typeof o.pop ? [] : {};
　　var p, v;
　　for(p in o) {
　　if(o.hasOwnProperty(p)) {
　　v = o[p];
　　if(v && 'object' === typeof v) {
　　c[p] = Ext.ux.clone(v);
　　}
　　else {
　　c[p] = v;
　　}
　　}
　　}
　　return c;
　　};
　　19，如何控制alert中的换行
　　\n alert(“p\np”);
　　20，请实现，鼠标点击页面中的任意标签，alert该标签的名称.(注意兼容性)
<script type="text/javascript">
document.onclick=function(e){
     var e=(e||event);
     var o=e["target"]||e["srcElement"];
     alert(o.tagName.toLowerCase());
}
</script>　　
21，请编写一个JavaScript函数 parseQueryString，它的用途是把URL参数解析为一个对象，如：
　　var url = “http://witmax.cn/index.php?key0=0&key1=1&key2=2″;
　　function parseQueryString(url){
　　var params = {};
　　var arr = url.split("?");
　　if (arr.length <= 1)
　　return params;
　　arr = arr[1].split("&");
　　for(var i=0, l=arr.length; i
　　var a = arr[i].split("=");
　　params[a[0]] = a[1];
　　}
　　return params;
　　}
　　var url = "http://witmax.cn/index.php?key0=0&key1=1&key2=2";
　　var ps = parseQueryString(url);
　　alert(ps["key1"]);
　　22，ajax是什么? ajax的交互模型? 同步和异步的区别? 如何解决跨域问题?
　　Ajax是多种技术组合起来的一种浏览器和服务器交互技术，基本思想是允许一个互联网浏览器向一个远程页面/服务做异步的http调用，并且用收到的数据来更新一个当前web页面而不必刷新整个页面。该技术能够改进客户端的体验。包含的技术：
　　XHTML：对应W3C的XHTML规范，目前是XHTML1.0。
　　CSS：对应W3C的CSS规范，目前是CSS2.0
　　DOM：这里的DOM主要是指HTML DOM，XML DOM包括在下面的XML中
　　JavaScript：对应于ECMA的ECMAScript规范
　　XML：对应W3C的XML DOM、XSLT、XPath等等规范
　　XMLHttpRequest：对应WhatWG的Web Applications1.0规范(http://whatwg.org/specs/web-apps/current-work/)
　　AJAX交互模型
　　
 
 
　　同步：脚本会停留并等待服务器发送回复然后再继续
　　异步：脚本允许页面继续其进程并处理可能的回复
　　跨域问题简单的理解就是因为JS同源策略的限制，a.com域名下的JS无法操作b.com或c.a.com下的对象，具体场景如下：
　　
 
 
　　PS：(1)如果是端口或者协议造成的跨域问题前端是无能为力的
　　(2) 在跨域问题上，域仅仅通过URL的首部来识别而不会尝试判断相同的IP地址对应的域或者两个域是否对应一个IP
　　前端对于跨域的解决办法：
　　(1) document.domain+iframe
　　(2) 动态创建script标签
　　23，什么是闭包?下面这个ul，如何点击每一列的时候alert其index?
　　这是第一条
　　这是第二条
　　这是第三条
　　内部函数被定义它的函数的外部区域调用的时候就产生了闭包。
　　(function A() {
　　var index = 0;
　　var ul = document.getElementById("test");
　　var obj = {};
　　for (var i = 0, l = ul.childNodes.length; i < l; i++) {
　　if (ul.childNodes[i].nodeName.toLowerCase() == "li") {
　　var li = ul.childNodes[i];
　　li.onclick = function() {
　　index++;
　　alert(index);
　　}
　　}
　　}
　　})();
　　24，请给出异步加载js方案，不少于两种
　　默认情况javascript是同步加载的，也就是javascript的加载时阻塞的，后面的元素要等待javascript加载完毕后才能进行再加载，对于一些意义不是很大的javascript，如果放在页头会导致加载很慢的话，是会严重影响用户体验的。
　　异步加载方式：
　　(1) defer，只支持IE
　　(2) async：
　　(3) 创建script，插入到DOM中，加载完毕后callBack，见代码：
　　function loadScript(url, callback){
　　var script = document.createElement("script")
　　script.type = "text/javascript";
　　if (script.readyState){ //IE
　　script.onreadystatechange = function(){
　　if (script.readyState == "loaded" ||
　　script.readyState == "complete"){
　　script.onreadystatechange = null;
　　callback();
　　}
　　};
　　} else { //Others: Firefox, Safari, Chrome, and Opera
　　script.onload = function(){
　　callback();
　　};
　　}
　　script.src = url;
　　document.body.appendChild(script);
　　}
　　25，请设计一套方案，用于确保页面中JS加载完全。
　　var n = document.createElement("script");
　　n.type = "text/javascript";
　　//以上省略部分代码
　　//ie支持script的readystatechange属性(IE support the readystatechange event for script and css nodes)
　　if(ua.ie){
　　n.onreadystatechange = function(){
　　var rs = this.readyState;
　　if('loaded' === rs || 'complete'===rs){
　　n.onreadystatechange = null;
　　f(id,url); //回调函数
　　}
　　};
　　//省略部分代码
　　//safari 3.x supports the load event for script nodes(DOM2)
　　n.addEventListener('load',function(){
　　f(id,url);
　　});
　　//firefox and opera support onload(but not dom2 in ff) handlers for
　　//script nodes. opera, but no ff, support the onload event for link
　　//nodes.
　　}else{
　　n.onload = function(){
　　f(id,url);
　　};
　　}
　　26，js中如何定义class,如何扩展prototype?
　　Ele.className = “***”; //***在css中定义，形式如下：.*** {…}
　　A.prototype.B = C;
　　A是某个构造函数的名字
　　B是这个构造函数的属性
　　C是想要定义的属性的值
　　27，如何添加html元素的事件,有几种方法.
　　(1) 为HTML元素的事件属性赋值
　　(2) 在JS中使用ele.on*** = function() {…}
　　(3) 使用DOM2的添加事件的方法 addEventListener或attachEvent
　　28，documen.write和 innerHTML的区别
　　document.write只能重绘整个页面
　　innerHTML可以重绘页面的一部分
　　29，多浏览器检测通过什么?
　　(1) navigator.userAgent
　　(2) 不同浏览器的特性，如addEventListener
　　30，js的基础对象有那些, window和document的常用的方法和属性列出来
　　String,Number,Boolean
　　Window:
　　方法：setInterval,setTimeout,clearInterval,clearTimeout,alert,confirm,open
　　属性：name,parent,screenLeft,screenTop,self,top,status
　　Document
　　方法：createElement,execCommand,getElementById,getElementsByName,getElementByTagName,write,writeln
属性：cookie,doctype,domain,documentElement,readyState,URL,

1. 要动态改变层中内容可以使用的方法有（AB ）
a)innerHTML
b)innerText
c)通过设置层的隐藏和显示来实现
d)通过设置层的样式属性的display属性

2. 当按键盘A时，使用onKeyDown事件打印event.keyCode的结果是（A ）
a)65
b)13
c)97
d)37

3. 在javascript里，下列选项中不属于数组方法的是（B）；
a)sort()
b)length()
c)concat()
d)reverse()
4. 下列哪一个选项可以用来检索被选定的选项的索引号?(B)
a)disabled
b)selectedIndex
c)option
d)multiple

5. 希望图片具有”提交”按钮同样的功能,该如何编写表单提交?(A )
a)在图片的onClick事件中手动提交
b)在图片上添加onSubmit事件
c)在图片的onSubmit事件中手动提交
d)在表单中自动提交

6. 使div层和文本框处在同一行的代码正确的是(D );
a)
b)
c)
d)
7. 下列选项中,描述正确的是(选择两项) 。( AD )
a)options.add(new Option(‘a’,'A’))可以动态添加一个下拉列表选项
b)option.add(new Option(‘a’,'A’))可以动态添加一个下拉列表选项
c)new Option(‘a’,'A’)中’a'表示列表选项的值,’A'用于在页面中显示
d)new Option(‘a’,'A’)中’A'表示列表选项的值,’a'用于在页面中显示

8. 、 var emp = new Array(3);
for(var i in emp)
以下答案中能与for循环代码互换的是: （选择一项）。(D )
A for(var i =0; i
B for(var i =0; i
C for(var i =0; i
D for(var i =0; i

9. 制作级联菜单功能时调用的是下拉列表框的（A ）事件。
a)onChange
b)onFocus
c)selected
d)onClick

10. 下列声明数组的语句中，错误的选项是（ C ）。
a)Var arry= new Array()
b)Var arry=new Array(3)
c)Var arry[]=new Array(3)(4)
d)Var arry=new Array(‘3’,’4’)

11. 下列属性哪一个能够实现层的隐藏?（C ）
a)display:fals
b)display:hidden
c)display:none
d)display:” ”

12. 下列哪一个选项不属于document对象的方法?（D ）
a)focus()
b)getElementById()
c)getElementsByName()
d)bgColor()

13. 下列哪项是按下键盘事件(AB )
a)onKeyDown
b)onKeyPress
c)keyCode
d)onMouseOver
14. javascript进行表单验证的目的是（B ）
a)把用户的正确信息提交给服务器
b)检查提交的数据必须符合实际
c)使得页面变得美观、大方
d)减轻服务器端的压力
15. 、 display属性值的常用取值不包括(C )
a)inline
b)block
c)hidden
d)none

16. 以下有关pixelTop属性与top属性的说法正确的是。(D )
a)都是Location对象的属性
b)使用时返回值都是字符串
c)都是返回以像素为单位的数值
d)以上都不对

17. 使用open方法打开具有浏览器工具条,地址栏,菜单栏的窗口，下列选项正确的是__D__
a)open("x.html","HI","toolbas=1,scrollbars=1,status=1");
b)open("HI","scrollbars=1,location=1,status=1");
c)open("x.html","status=yes,menubar=1,location=1");
d)open("x.html","HI","toolbas=yes,menubar=1,location=1");

18. 下面关闭名为mydiv的层的代码正确的是(C )
a)document.getElementByIdx_x_x_x(mydiv).style.display="none";
b)document.getElementByIdx_x_x_x("mydiv").style.display=none;
c)document.getElementByIdx_x_x_x("mydiv").style.display="none";
d)document.getElementByIdx_x_x_x("mydiv").style.display=="none";
19. 为什么要使用Div+CSS布局
形式与内容分离
大大减少页面代码，提高页面浏览速度
结构清晰，有利于SEO
缩短改版时间， 布局更方便
一次设计，多次使用

20. Block元素的特点是什么?哪些元素默认为Block元素
总是在新行上开始；
高度，行高以及顶和底边距都可控制；
宽度缺省是它的容器的100%，除非设定一个宽度
是块元素的有：,,
,
, 和21. 、 inline元素的特点是什么?哪些元素属于inline元素?
和其他元素都在一行上；
高，行高及顶和底边距不可改变；
宽度就是它的文字或图片的宽度，不可改变。

是inline元素的有：, , ,
, , 
和。 

22. 、 javascript中表达式parseInt(“X8X8”)+paseFloat(‘8’)的结果是什么?( C)
a)8+8
b)88
c)16
d)“8”+’8

23. String对象的方法不包括(C )
a)charAt()；
b)substring()
c)length
d)toUpperCase()

24. 关于setTimeout(“check”,10)中说法正确的是( D)
a)程序循环执行10次
b)Check函数每10秒执行一次
c)10做为参数传给函数check
d)Check函数每10毫秒执行一次

25. 以下哪个单词不属于javascript关键字：（C）
a)with
b)parent
c)class
d)void

　   1、DOM结构 —— 两个节点之间可能存在哪些关系以及如何在节点之间任意移动。

    2、DOM操作  ——如何添加、移除、移动、复制、创建和查找节点等。

    3、事件    —— 如何使用事件，以及IE和标准DOM事件模型之间存在的差别。

    4、XMLHttpRequest —— 这是什么、怎样完整地执行一次GET请求、怎样检测错误。

    5、严格模式与混杂模式 —— 如何触发这两种模式，区分它们有何意义。

    6、盒模型 —— 外边距、内边距和边框之间的关系，及IE8以下版本的浏览器中的盒模型

    7、块级元素与行内元素 —— 怎么用CSS控制它们、以及如何合理的使用它们

    8、浮动元素——怎么使用它们、它们有什么问题以及怎么解决这些问题。

    9、HTML与XHTML——二者有什么区别，你觉得应该使用哪一个并说出理由。

    10、JSON  —— 作用、用途、设计结构。


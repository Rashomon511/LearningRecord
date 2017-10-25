1.什么是内存泄露
- 内存泄漏指任何对象在您不再拥有或需要它之后仍然存在。
垃圾回收器定期扫描对象，并计算引用了每个对象的其他对象的数量。如果一个对象的引用数量为 0(没有其他对象引用过该对象)，或对该对象的惟一引用是循环的，那么该对象的内存即可回收。
setTimeout 的第一个参数使用字符串而非函数的话，会引发内存泄漏。
闭包、控制台日志、循环(在两个对象彼此引用且彼此保留时，就会产生一个循环)。
[链接](http://www.cnblogs.com/chuaWeb/p/5196330.html)
[链接](http://web.jobbole.com/91080/)

2.JSON是什么？(JSON和JavaScript对象有什么区别？)如何把JS对象转化为JSON字符串，又如何把JSON字符串转化为JavaScript对象？
- JSON （JavaScript Object Notation）一种简单的数据格式，比xml更轻巧。 JSON 是 JavaScript 原生格式，这意味着在JavaScript 中处理 JSON 数据不需要任何特殊的 API 或工具包。JSON的规则很简单： 对象是一个无序的“名称/值”对集合。一个对象以“{”（左括号）开始，“}”（右括号）结束。每个“名称”后跟一个“:”（冒号）；“名称/值”对之间使用“,”（逗号）分隔。
```javascript
var obj2={};//这只是JS对象
var obj3={width:100,height:200};/*这跟JSON就更不沾边了,只是JS的 对象 */
var obj4={'width':100,'height':200};/*这跟JSON就更不沾边了,只是JS的对象 */
var obj5={"width":100,"height":200,"name":"rose"}; /*我们可以把这个称做：JSON格式的JavaScript对象 */
var str1='{"width":100,"height":200,"name":"rose"}';/*我们可以把这个称做：JSON格式的字符串 */
var a=[
 {"width":100,"height":200,"name":"rose"},
 {"width":100,"height":200,"name":"rose"},
 {"width":100,"height":200,"name":"rose"},
 ];
 /*这个叫JSON格式的数组，是JSON的稍复杂一点的形式 */
var str2='['+
 '{"width":100,"height":200,"name":"rose"},'+
 '{"width":100,"height":200,"name":"rose"},'+
 '{"width":100,"height":200,"name":"rose"},'+
 ']' ;
 /* 这个叫稍复杂一点的JSON格式的字符串 */
```
json字符串转json对象,调用parse方法：
```javascript
var b='{"name":"2323","sex":"afasdf","age":"6262"}'//json字符串
var bToObject=JSON.parse(b);
console.log(bToObject.name);//2323
```
json对象转为json字符串：
```javascript
var a={"name":"tom","sex":"男","age":"24"}//json对象
var aToString=JSON.stringify(a);
console.log(aToString);//{"name":"tom","sex":"男","age":"24"}
```
- Json转化为js对象：
1,JSON.parse(jsonstring);(不兼容ie7)
2,Jsobj=eval("("+jsonstring+")")；
(兼容所有浏览器，但不安全，会执行json里面的表达式?)
- Js对象转换为Json：
JSON.stringify(jsobj);(不兼容ie7)
$.toJSON的用法或把数组转换成json类型 

3.图解http
- [链接](http://www.cnblogs.com/xing901022/p/4309840.html)

4.移动端自适应方案
- [解决方案](http://www.html-js.com/article/Mobile-terminal-H5-mobile-terminal-HD-multi-screen-adaptation-scheme%203041)

5.mvvm和mvc的区别
- 在MVC里，View是可以直接访问Model的！从而，View里会包含Model信息，不可避免的还要包括一些业务逻辑。 MVC模型关注的是Model的不变，所以，在MVC模型里，Model不依赖于View，但是 View是依赖于Model的。不仅如此，因为有一些业务逻辑在View里实现了，导致要更改View也是比较困难的，至少那些业务逻辑是无法重用的。

　　MVVM在概念上是真正将页面与数据逻辑分离的模式，它把数据绑定工作放到一个JS里去实现，而这个JS文件的主要功能是完成数据的绑定，即把model绑定到UI的元素上。

　　有人做过测试：使用Angular（MVVM）代替Backbone（MVC）来开发，代码可以减少一半。

　　此外，MVVM另一个重要特性，双向绑定。它更方便你同时维护页面上都依赖于某个字段的N个区域，而不用手动更新它们。
  [链接](http://www.cnblogs.com/guwei4037/p/5591183.html)

 

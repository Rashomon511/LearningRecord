1.javascript的typeof返回哪些数据类型
- Object number function boolean underfind

2.例举3种强制类型转换和2种隐式类型转换?
- 强制（parseInt,parseFloat,number）
隐式（== – ===）

3.split() join() 的区别
- 前者是切割成数组的形式，后者是将数组转换成字符串

4.数组方法pop() push() unshift() shift()
- Push()尾部添加 pop()尾部删除
Unshift()头部添加 shift()头部删除

5.事件绑定和普通事件有什么区别
- 普通事件中的onclick是DOM0级事件只支持单个事件，会被其他onclick事件覆盖，而事件绑定中的addEventListener是DOM2级事件可以添加多个事件而不用担心被覆盖

6.IE和DOM事件流的区别
- 1.执行顺序不一样、
2.参数不一样
3.事件加不加on
4.this指向问题

7.IE和标准下有哪些兼容性的写法
- Var ev = ev || window.event
document.documentElement.clientWidth || document.body.clientWidth
Var target = ev.srcElement||ev.target

8.ajax请求的时候get 和post方式的区别
- 一个在url后面 一个放在虚拟载体里面
有大小限制
安全问题
应用不同 一个是论坛等只需要请求的，一个是类似修改密码的

9.call和apply的区别
- Object.call(this,obj1,obj2,obj3)
Object.apply(this,arguments)

10.ajax请求时，如何解释json数据
- 使用eval parse 鉴于安全性考虑 使用parse更靠谱

11.b继承a的方法
```javascript
function A(name){
    this.name = name;
    this.sayHello = function(){alert(this.name+” say Hello!”);};
}

function B(name,id){
    this.temp = A;
    this.temp(name);        //相当于new A();
    delete this.temp;       
     this.id = id;   
    this.checkId = function(ID){alert(this.id==ID)};
}
```

12.写一个获取非行间样式的函数
```javascript
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
```

13.事件委托是什么
- 让利用事件冒泡的原理，让自己的所触发的事件，让他的父元素代替执行！

14.闭包是什么，有什么特性，对页面有什么影响
- 闭包就是能够读取其他函数内部变量的函数。
http://blog.csdn.net/gaoshanwudi/article/details/7355794 此链接可查看（问这个问题的不是一个公司）

15.如何阻止事件冒泡和默认事件
- canceBubble return false

16.添加 删除 替换 插入到某个接点的方法
- obj.appendChidl()
obj.innersetBefore
obj.replaceChild
obj.removeChild

17.解释jsonp的原理，以及为什么不是真正的ajax
- 动态创建script标签，回调函数
Ajax是页面无刷新请求数据操作

18.javascript的本地对象，内置对象和宿主对象
- 本地对象为array obj regexp等可以new实例化
内置对象为gload Math 等不可以实例化的
宿主为浏览器自带的document,window 等

19.document load 和document ready的区别
- Document.onload 是在结构和样式加载完才执行js
Document.ready原生种没有这个方法，jquery中有 $().ready(function)

20.”==”和“===”的不同
- 前者会自动转换类型
后者不会

21.javascript的同源策略
- 一段脚本只能读取来自于同一来源的窗口和文档的属性，这里的同一来源指的是主机名、协议和端口号的组合

22.编写一个数组去重的方法
```javascript
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
```
23.写出一下运算结果
```javascript
alert(typeof(null)) // object
alert(typeof(undefined)) // undefined
alert(typeof(NaN)) // number
alert(NaN==undefined) // false
alert(NaN==NaN) // false
var str="123abc";
alert(typeof(str++)) // number
alert(str) // string
```
24.判断一个字符串中出现次数最多的字符，统计这个次数
```javascript
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
```
25.写出3个使用this的典型应用
- (1)在html元素事件属性中使用，如
　　(2)构造函数
　　function Animal(name, color) {
　　this.name = name;
　　this.color = color;
　　}
　　(3)CSS expression表达式中使用this关键字
  
26.JavaScript中如何检测一个变量是一个String类型?请写出函数实现
```javascript
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
```
27.JavaScript有哪几种数据类型
- 简单：Number，Boolean，String，Null，Undefined
　　复合：Object，Array，Function
  
28.JavaScript中如何对一个对象进行深度clone
  ```javascript
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
  ```
  
  29.请编写一个JavaScript函数 parseQueryString，它的用途是把URL参数解析为一个对象，如：
  ```javascript
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
```
30.ajax是什么? ajax的交互模型? 同步和异步的区别? 如何解决跨域问题?
- Ajax是多种技术组合起来的一种浏览器和服务器交互技术，基本思想是允许一个互联网浏览器向一个远程页面/服务做异步的http调用，并且用收到的数据来更新一个当前web页面而不必刷新整个页面。该技术能够改进客户端的体验。包含的技术：
　　XHTML：对应W3C的XHTML规范，目前是XHTML1.0。
　　CSS：对应W3C的CSS规范，目前是CSS2.0
　　DOM：这里的DOM主要是指HTML DOM，XML DOM包括在下面的XML中
　　JavaScript：对应于ECMA的ECMAScript规范
　　XML：对应W3C的XML DOM、XSLT、XPath等等规范
  
31.documen.write和 innerHTML的区别
- document.write只能重绘整个页面
　　innerHTML可以重绘页面的一部分
  
32.js的基础对象有那些, window和document的常用的方法和属性列出来
- String,Number,Boolean
　　Window:
　　方法：setInterval,setTimeout,clearInterval,clearTimeout,alert,confirm,open
　　属性：name,parent,screenLeft,screenTop,self,top,status
　　Document:
　　方法：createElement,execCommand,getElementById,getElementsByName,getElementByTagName,write,writeln
    属性：cookie,doctype,domain,documentElement,readyState,URL,
    
  33.React 常用面试题目与分析 React数据获取为什么一定要在componentDidMount里面调用？
  1.获取数据肯定是以异步方式进行，不会阻碍组件渲染（只会耽误请求发送这个时间），然后接着渲染，等异步返回数据后，如果成功再进行setState操作，setState是将更新的状态放进了组件的__pendingStateQueue队列，react不会立即响应更新，会等到组件挂载完成后，统一的更新脏组件（需要更新的组件）。放在constructor或者componentWillMount里面反而会更加有效率。
2.再说说React-Redux，要想让组件更新，必须要有用connect(...)(yourComponent)封装的容器（高阶）组件，这个组件会监听store变化，内部调用setState触发你的组件更新。数据处理都是通过dispatch(action)进行,自己并不会在组件的声明周期内直接ajax获取取数据。使用redux这个问题就成为了再组件声明周期的哪个节阶段dispatch(action)获取数据才合理？
总结：
我认为原因有：
1.跟服务器端渲染（同构）有关系，如果在componentWillMount里面获取数据，fetch data会执行两次，一次在服务器端一次在客户端。在componentDidMount中可以解决这个问题。
2.在componentWillMount中fetch data，数据一定在render后才能到达，如果你忘记了设置初始状态，用户体验不好。
3.react16.0以后，componentWillMount可能会被执行多次
  https://zhuanlan.zhihu.com/p/24856035







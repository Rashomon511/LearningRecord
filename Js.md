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

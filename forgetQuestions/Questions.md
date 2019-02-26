 #  易忘的问题 #

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

 6.数据驱动的原理
 - 数据驱动是vuejs最大的特点。在vuejs中，所谓的数据驱动就是当数据发生变化的时候，用户界面发生相应的变化，开发者不需要手动的去修改dom。

比如说我们点击一个button，需要元素的文本进行是和否的切换。在jquery刀耕火种的年代中，对于页面的修改我们一般是这样的一个流程，我们对button绑定事件，然后获取文案对应的元素dom对象，然后根据切换修改该dom对象的文案值。

而对于vuejs实现这个功能的流程，只需要在button元素上指明事件，同时声明对应文案的属性，点击事件的时候改变属性的值，对应元素的文本就能够自动的进行切换，我们不需要像以前那样手动的操作dom。

简而言之，就是vuejs帮我们封装了数据和dom对象操作的映射，我们只需要关心数据的逻辑处理，数据的变化就能够自然的通知页面进行页面的重新渲染。

这样做的确实给我们带来的好处，我们不需要再在代码中频繁地去操作dom了，在实际项目中，我们有很大部分代码都是在数据修改以后，手动操作重新渲染页面元素，当页面越来越复杂的时候，页面代码组织会越来难以维护。同时，js对dom的频繁操作，会使得页面代码的出错概率高，页面的视图展示会融合在js代码中，对于页面视图显示的升级也不友好。

那么vuejs是如何实现这种数据驱动的呢？

MVVM框架

Vuejs的数据驱动是通过MVVM这种框架来实现的。MVVM框架主要包含3个部分:model、view和 viewmodel。

Model:指的是数据部分，对应到前端就是javascript对象

View:指的是视图部分，对应前端就是dom

Viewmodel:就是连接视图与数据的中间件
[链接](http://www.cnblogs.com/caizhenbo/p/6418284.html)

7.new  vue之后发什么了什么
- new vue 是新建 vue 对象，需要绑定元素的。 vue.extend 是新建 vue 组件，使用依赖于 vue 对象。

8.从回调函数到Promises到Generators到Async/awit –
- http://zcfy.cc/article/es-5-6-7-from-callbacks-to-promises-to-generators-to-async-await-medium-1786.html?t=new

9.三种对象合并方法
 方法1：使用JQuery的extend方法
 如果不指定target，则给jQuery命名空间本身进行扩展。这有助于插件作者为jQuery增加新方法。 如果第一个参数设置为true，则jQuery返回一个深层次的副本，递归地复制找到的任何对象(递归合并)。否则的话，副本会与原对象共享结构。 未定义的属性将不会被复制，然而从对象的原型继承的属性将会被复制。
 ```javascript
o3 = $.extend(o1, o2)  // 合并 o1 和 o2， 将结果返回给 o3. 注意： 此时，o1 == o3! 即 o1 被修改
// 或
o3 = $.extend({}, o1, o2) // 合并 o1 和 o2， 将结果返回给 o3. 注意： 此时，o1 ！= o3! 即 o1 没有被修改
```
方法2：用 Object.assign();
```javascript
var o1 = { a: 1 };
var o2 = { b: 2 };
var o3 = { c: 3 };

var obj = Object.assign(o1, o2, o3);
console.log(obj); // { a: 1, b: 2, c: 3 }
console.log(o1);  // { a: 1, b: 2, c: 3 }, 注意目标对象自身也会改变。
```
方法3：遍历赋值法
```javascript
var extend=function(o,n){
   for (var p in n){
        if(n.hasOwnProperty(p) && (!o.hasOwnProperty(p) ))
            o[p]=n[p];
    }
};
```
10.redux中间件异步流程
http://www.jianshu.com/p/e84493c7af35
redux-thunk 的缺点：
（1）action 虽然扩展了，但因此变得复杂，后期可维护性降低；
（2）thunks 内部测试逻辑比较困难，需要mock所有的触发函数；
（3）协调并发任务比较困难，当自己的 action 调用了别人的 action，别人的 action 发生改动，则需要自己主动修改；
（4）业务逻辑会散布在不同的地方：启动的模块，组件以及thunks内部。
 redux-saga 的优点：
（1）声明式 Effects：所有的操作以JavaScript对象的方式被 yield，并被 middleware 执行。使得在 saga 内部测试变得更加容易，可以通过简单地遍历 Generator 并在 yield 后的成功值上面做一个 deepEqual 测试。
（2）高级的异步控制流以及并发管理：可以使用简单的同步方式描述异步流，并通过 fork 实现并发任务。
（3）架构上的优势：将所有的异步流程控制都移入到了 sagas，UI 组件不用执行业务逻辑，只需 dispatch action 就行，增强组件复用性。
11. 函数式组件
```javascript
export function Header (options) {
    return (Comp) => {
        const finalOptions = {
            ...options
        };
        const { title } = finalOptions;
        class HeaderComponent extends Component {
            close = () => {
                ipcRenderer.send('close', ['login']);
            };
            render () {
                return (
                    <div className={style.allWrap}>
                        <div className={style.dragBox}>
                            <div className={style.wrap}>
                                <div className={style.icon}>
                                    <Icon type='close' className={style.closeIcon} onClick={this.close} />
                                </div>
                            </div>
                            <div className={style.header}>
                                <div className={style.headTitle}><span>{title}</span></div>
                                <div className={style.logoPic}>
                                    < img src={logo} alt='' />
                                </div>
                                <div className={style.headName}><p>元数通</p ></div>
                            </div>
                        </div>
                        <div classname={style.Wrap}>
                            <div className={style.content}>
                                <Comp
                                    {...this.props}
                                />
                            </div>
                        </div>
                    </div>
                );
            }
        }
        return HeaderComponent;
    }
}
```
12 日期转换
new Date().format("YYYY-MM-DD HH:mm:ss")

13.JavaScript:(a==1 && a==2 && a==3)能输出ture么？
可以，改写valueOf
a.valueOf = function() {
  return this.num += 1;
}

主要是用到>隐式转换
object的valueOf函数

14.你如何对网站的文件和资源进行优化?期待的解决方案包括：
- 文件合并
文件最小化/文件压缩
使用CDN托管
缓存的使用

15.性能优化经验

16.热加载怎么实现

17.JS事件循环
异步任务放在一个队列里，Promise的任务呢











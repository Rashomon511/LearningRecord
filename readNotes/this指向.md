# this指向

this的绑定和函数声明的位置没有任何关系，只取决于函数的调用方式,this的绑定方式有四种，要判断this的绑定，只需要找到函数的调用位置，根据规则判断即可判断this
的指定对象

## 默认绑定
> 独立函数调用，在全局模式下，全局对象将无法使用默认绑定
```
function foo() {
console.log( this.a ); // this指向window
}
var a = 2; 
foo(); // 2 调用位置为全局
```
在本例中，this.a被解析成全局变量，因为函数调用时应用了this的默认绑定，因此指向全局对象

## 隐式绑定
> 调用位置是否有上下文对象，或者说是否被某个对象拥有或者包含,对象属性引用链中只有最顶层或者说最后一层会影响调用位置
```
function foo(){
console.log(this.a)
}
var obj={
a:2,
foo:foo
}
obj.foo();//2
```

上面调用foo()时this被绑定到obj,因此this.a和obj.a是一样的，因为隐式绑定规则会把函数调用中的this绑定到这个上下文对象

## 显示绑定
 > 利用call,apply方法可以直接指定 this 的绑定对象
```
function foo(){
console.log(this.a)
}
var obj={
a:2,
}
foo.call(obj); //2
```
通过foo.call(…)我们可以把调用foo时强制把他的this绑定到obj上，在显示绑定的基础上还有硬绑定，这是显示绑定的变种
* 1.硬绑定: 强制把 foo 的 this 绑定到了 obj,js内置bind(..) 会返回一个硬编码的新函数，它会把参数设置为 this 的上下文并调用原始函数
```
function foo() {
console.log( this.a );
}
var obj = { a:2};
var bar = function() {
foo.call( obj );
};
bar(); // 2
setTimeout( bar, 100 ); // 2
// 硬绑定的 bar 不可能再修改它的this 
bar.call( window ); // 2
```
创建了bar函数，在内部强制把this绑定到obj上面，之后无论如何调用bar，都不能改变this指向。apply和bind同样可以实现硬绑定
* API调用的“上下文”： 提供了一 个可选的参数，通常被称为“上下文”(context)，其作用和 bind(..) 一样
```
function foo(el) {
console.log( el, this.id );
}
var obj = {
id: "awesome"
};
// 调用 foo(..) 时把 this 绑定到 obj [1, 2, 3].forEach( foo, obj );
// 1 awesome 2 awesome 3 awesome
```
## 软绑定
> 相对于硬绑定来说，在实现硬绑定效果的同时，可以保留隐式绑定或者显式绑定修改 this 的能力
## new绑定
>使用 new 来调用 foo(..) 时，我们会构造一个新对象并把它绑定到 foo(..) 调用中的 this 上。new 是最后一种可以影响函数调用时 this 绑定行为的方法，我们称之为 new 绑定
```
function foo(){
this.a=a
}
var bar=new foo(2);
console.log(bar.a)//2
```
发生函数构造时或者使用new来调用函数，会自动执行下面的操作：
 * 1. 创建(或者说构造)一个全新的对象。
 * 2. 这个新对象会被执行[[原型]]连接。
 * 3. 这个新对象会绑定到函数调用的this。
 * 4. 如果函数没有返回其他对象，那么new表达式中的函数调用会自动返回这个新对象。
## 优先级问题

> new绑定>显示绑定>隐式绑定>默认绑定

> 特例：箭头函数不使用 this 的四种标准规则，而是根据外层(函数或者全局)作用域来决定this。箭头函数会继承外层函数调用的 this 绑定(无论 this 绑定到什么)。这 其实和 ES6 之前代码中的 self = this 机制一样

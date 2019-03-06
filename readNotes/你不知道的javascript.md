# 你不知道的javascript

> 作用域是一套用于确定在何处及如何查找变量的规则
  * LHS查询目的是对变量进行赋值
  * RHS查询目的是获取变量对值
 
> 词法作用域就说定义在词法阶段对作用域，作用域是由书写代码时函数声明对位置决定对
  * eval(...)和with可以进行欺骗词法，但是对代码优化和性能有影响，因此最好不用，在严格模式下两者不起作用
 
> 函数声明和变量声明都会被提升，但是函数会被首先提升

> 闭包就是一个函数可以访问另一个函数的作用域，这样就形成了闭包，换句话说当函数可以记住并访问所在当词法作用域这时就产生了闭包
> 模块的两个主要特征
 * 为创建内部作用域而调用一个包装函数
 * 包装函数的返回值必须至少包括一个对内部函数对引用，这样就会创建涵盖整个包装函数内部作用域对闭包
 
> js并不存在动态作用域，只有词法作用域，词法作用域关注函数在何处声明，动态作用域关注函数在何处调用

>  为什么使用this? this 提供了一种更优雅的方式来隐式“传递”一个对象引用
>this 是在运行时进行绑定的，并不是在编写时绑定，它的上下文取决于函数调 用时的各种条件。this 的绑定和函数声明的位置没有任何关系，只取决于函数的调用方式

> this的绑定规则
 * 默认绑定： 独立函数调用，在全局模式下，全局对象将无法使用默认绑定
 ```
 function foo() {
 console.log( this.a ); // this指向window
 }
 var a = 2; 
 foo(); // 2 调用位置为全局
 ```
 * 隐式绑定：调用位置是否有上下文对象，或者说是否被某个对象拥有或者包含,对象属性引用链中只有最顶层或者说最后一层会影响调用位置
 ```
 function foo() {
  console.log( this.a );
 }
var obj = {
 a: 2,
 foo: foo 
};
obj.foo(); // 2
 ```
 * 显式绑定: 利用call,apply方法可以直接指定 this 的绑定对象
 ```
 function foo() {
 console.log( this.a );
 }
var obj = {
  a:2
 };
foo.call( obj ); // 2 //foo.apply(obj)
 ```
  - 1.硬绑定: 强制把 foo 的 this 绑定到了 obj,js内置bind(..) 会返回一个硬编码的新函数，它会把参数设置为 this 的上下文并调用原始函数
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
// 硬绑定的 bar 不可能再修改它的
this bar.call( window ); // 2
```
 2. API调用的“上下文”： 提供了一 个可选的参数，通常被称为“上下文”(context)，其作用和 bind(..) 一样
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
 * new绑定
 ```
 function foo(a) { this.a = a;}
var bar = new foo(2); 
console.log( bar.a ); // 2
```
使用 new 来调用 foo(..) 时，我们会构造一个新对象并把它绑定到 foo(..) 调用中的 this 上。new 是最后一种可以影响函数调用时 this 绑定行为的方法，我们称之为 new 绑定

> 优先级：new绑定>显示绑定>隐式绑定>默认绑定
> 特例：箭头函数不使用 this 的四种标准规则，而是根据外层(函数或者全局)作用域来决 定 this。
 
 
 
 
 
 
 
 
 
 
 
 

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

>  为什么使用this? this 提供了一种更优雅的方式来隐式“传递”一个对象引用[详解](https://github.com/LuoShengMen/StudyNotes/blob/master/readNotes/this%E6%8C%87%E5%90%91.md)
> this 是在运行时进行绑定的，并不是在编写时绑定，它的上下文取决于函数调 用时的各种条件。this 的绑定和函数声明的位置没有任何关系，只取决于函数的调用方式

> 对象可以通过两种形式定义:声明(文字)形式和构造形式。
> js的内置对象：String,Number,Boolean, Object,Function,Array,Date,RegExp,Error
> 属性描述 Object.getOwnPropertyDescriptor( myObject, "a" );
> 新增或修改属性：  Object.defineProperty(..)
```
Object.defineProperty( myObject, "a", {
         value: 2,
         writable: true, //决定是否可以修改属性的值。
         configurable: true, //只要属性是可配置的，就可以使用 defineProperty(..) 方法来修改属性描述符,会禁止delete属性
         enumerable: true //属性是否会出现在对象的属性枚举中
     } );
```
> 对象常量: 结合 writable:false 和 configurable:false,禁止扩展:  Object.prevent Extensions(..):密封:Object.seal(..) 冻结: Object.freeze(..) 

> in操作符会检查属性是否在对象及其[[Prototype]] 原型链中(只包含可枚举属性)，hasOwnProperty(..)只会检查属性是否在该对象中,

> Object.keys(..)(只包含可枚举属性)和 Object.getOwnPropertyNames(..)都只会查找对象直接包含的属性

>in操作符会检查属性是否在对象及其[[Prototype]] 原型链中，hasOwnProperty(..)只会检查属性是否在该对象中,Object.keys(..)和 Object.getOwnPropertyNames(..)都只会查找对象直接包含的属性

> for...in 来遍历无法直接获取属性值的，对于对象只能获取属性，对于数组获取下标，for...of遍历对象获得属性值，遍历数组获取值(for..of 循环首先会向被访 问对象请求一个迭代器对象，然后通过调用迭代器对象的 next() 方法来遍历所有返回值)

> 多态的一方面是任何方法都可以引用继承层次中高层的方法(无论高层的方法名和当前方法名是否相同)，另一个方面是，在继承链的不同层次中一个方法名可以被多次定义

> 混入模式(无论显式还是隐式)可以用来模拟类的复制行为，但是通常会产生丑陋并且脆 弱的语法

> 对象(和函数!别忘了函数也 是对象)只能复制引用，无法复制被引用的对象或者函数本身

> JavaScript 中的对象有一个特殊的 [[Prototype]] 内置属性，其实就是对于其他对象的引用

> 发生屏蔽的三种情况
  > * 1. 如果在[[Prototype]]链上层存在名为foo的普通数据访问属性(参见第3章)并且没 有被标记为只读(writable:false)，那就会直接在 myObject 中添加一个名为 foo 的新 属性，它是屏蔽属性。
  > * 2. 如果在[[Prototype]]链上层存在foo，但是它被标记为只读(writable:false)，那么 无法修改已有属性或者在 myObject 上创建屏蔽属性。如果运行在严格模式下，代码会 抛出一个错误。否则，这条赋值语句会被忽略。总之，不会发生屏蔽。
  > * 3. 如果在[[Prototype]]链上层存在foo并且它是一个setter(参见第3章)，那就一定会 调用这个 setter。foo 不会被添加到(或者说屏蔽于)myObject，也不会重新定义 foo 这 个 setter。

> 所有的函数默认都会拥有一个 名为 prototype 的公有并且不可枚举的属性

> Object.create(..) 会凭空创建一个“新”对象并把新对象内部的 [[Prototype]] 关联到你 指定的对象

> Bar.prototype = Foo.prototype 并不会创建一个关联到 Bar.prototype 的新对象，它只 是 让 Bar.prototype 直 接 引 用 Foo.prototype 对 象

> Bar.prototype = new Foo() 的确会创建一个关联到 Bar.prototype 的新对象。但是它使用 了 Foo(..) 的“构造函数调用”，如果函数 Foo 有一些副作用(比如写日志、修改状态、注 册到其他对象、给 this 添加数据属性，等等)的话，就会影响到 Bar() 的“后代

> setPrototypeOf关联原型对像：把 Bar.prototype 关联到 Foo.prototype 的方法Object.setPrototypeOf( Bar.prototype, Foo.prototype );

> isPrototypeOf判断两个对象(比如 a 和 b)之间是否通过 [[Prototype]] 链关联

> Object.getPrototypeOf直接获取一个对象的 [[Prototype]] 链

> Object.create(null) 会 创 建 一 个 拥 有 空( 或 者 说 null)[[Prototype]] 链接的对象

> 对象之间的关系不是复制而是委托










 
 
 
 
 
 
 
 
 
 
 

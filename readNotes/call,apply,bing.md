### js基础之call,apply,bind的用法和区别

# 2019-2-js基础之call,apply,bind的用法和区别

apply()和 call()这两个方法的用途都是在特定的作 用域中调用函数，实际上等于设置函数体内 this 对象的值。bind()方法会创建一个函数的实例，其 this 值会被绑定到传给 bind()函数的值。总的来说是用来改变函数运行时this的指向。

call()用法：需要参数按顺序传递进去
```
function sum(num1, num2){

    return num1 + num2;

}

function callSum(num1, num2){

    return sum.call(this, num1, num2);

}

alert(callSum(10,10));   //20
```

apply()方法接收两个参数:一个 是在其中运行函数的作用域，另一个是参数数组，第二个参数可以是 Array 的实例，也可以是 arguments 对象
```
function sum(num1, num2){
    return num1 + num2;
}

function callSum1(num1, num2){
    return sum.apply(this, arguments);
}

function callSum2(num1, num2){
    return sum.apply(this, [num1, num2]);
}

alert(callSum1(10,10));   //20
alert(callSum2(10,10));   //20
```
其中 this 是你想指定的上下文，他可以是任何一个 JavaScript 对象(JavaScript 中一切皆对象)
apply()和 call()的用法，接受参数的方式不一样，使用 call()(或 apply())来扩充作用域的最大好处，就是对象不需要与方法有任何耦合关系，如果你传的 context 就 null 或者 undefined，那么 window 对象就是默认的 context（严格模式下默认 context 是 undefined)。

bind()用法：第一个参数是this的指向，从第二个参数开始是接收的参数列表
```
window.color = "red";

var o = { color: "blue" };

function sayColor(){

    alert(this.color);

}

var objectSayColor = sayColor.bind(o);

objectSayColor();    //blue
```

call、apply和bind函数存在的区别:<br />bind()不会立即执行，而是返回一个改变了上下文 this 后的函数, 便于稍后调用； apply, call则是立即调用.

需要注意的一点的是：
* 在 ES6 的箭头函数下, call 和 apply 将失效, 对于箭头函数来说箭头函数体内的 this 对象, 就是定义时所在的对象。
* 箭头函数不可以当作构造函数，也就是说不可以使用 new 命令, 否则会抛出一个错误
* 箭头函数不可以使用 arguments 对象,，该对象在函数体内不存在

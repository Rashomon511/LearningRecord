
* let 和const定义对变量在window上面找不到
```
    let a = 1;
    var b = 2
    let Object = {
      a: 3,
      d: function () {
        console.log(this.b)
        console.log(this.a)
      },
    }
    let ed = Object.d;
    ed() // 2, undefined
```
* 原型链：每一个对象内部都有一个__proto__属性，当访问该对象当某个属性或方法时，如果该对象内部不存在，那么他就会去个__proto__里找，如果又无法找到，又回去个__proto__的个__proto__找，于是就这样 一直找下去，最终会找到Object.prototype._proto__里,这就是原型链的概念。原型对象最终指向null
```
var Person = function () {};
Person.prototype.Say = function () {
  alert("Person say");
}
Person.prototype.Salary = 50000;
var Programmer = function () {};
Programmer.prototype = new Person();
Programmer.prototype.WriteCode = function () {
    alert("programmer writes code");
};
Programmer.age = 333;
Programmer.prototype.Salary = 500;
var p = new Programmer();
// p.Say();    /*Person say*/
// p.WriteCode();  /*programmer writes code*/
// alert(p.Salary);    /*500*/

console.log(p.__proto__ === Programmer.prototype) // true
console.log(Programmer.prototype.__proto__ === Person.prototype) // true
console.log(Programmer.prototype.isPrototypeOf(p)) //true
console.log(Object.getPrototypeOf(p) === Programmer.prototype) //true
console.log(Person.prototype.__proto__ === Object.prototype); //true
console.log(Object.prototype.__proto__) //null
````
 > * 只有构造函数才有prototype属性
 > * 构造函数的prototype，默认情况下就是一个new Object()还额外添加了一个constructor属性
 > * 除了Object.prototype这个对象，其他所有的对象也会有__proto__属性
    
    
    
    
    

    

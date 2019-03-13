typeof null === "object"; // true
```
 var a;
 a //undefined
 b //ReferenceError: b is not defined undeclared
 typeof a; // "undefined"
 typeof b; // "undefined"
 ```
 
 ```
 var a = [ ];
 a["13"] = 42; //字符串键值被强制类型转换为十进制数字
 a.length; // 14
```

0.1 + 0.2 === 0.3; // false 二进制浮点数中的 0.1 和 0.2 并不是十分精确

void 0、void 1 和 undefined 之间并没有实质上的区别

```
 var a = 2 / "foo";      // NaN
 typeof a === "number";  // true
 a == NaN;   // false
 a === NaN;  // false
 NaN === NaN //falsew
```

零值
```
var a = 0 / -3;
a.toString();     // "0"
a + "";      // "0"
String( a );     // "0"
// JSON也如此，很奇怪 
JSON.stringify( a );// "0"
+"-0";              // -0
Number( "-0" );     // -0
JSON.parse( "-0" ); // -0
-0 == 0;// true
a === b;// true
-0 === 0;// true
0 > -0; // false
a > b; // false
```

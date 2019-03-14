
* JavaScript 有 七 种 内 置 类 型: String,Number,Object,Array,null,undefined,Symbol
* 变量没有类型，但它们持有的值有类型。类型定义了值的行为特征
* undefined 是变量未被复值。undeclared 则表示变量还没有被声明过，typeof都返回undefind
* 使用 Object.create(null) 创建的对象 [[Prototype]] 属性为 null，并且没 有 valueOf() 和 toString() 方法
* 简单值(即标量基本类型值，scalar primitive)总是通过值复制的方式来赋值 / 传递，包括 null、undefined、字符串、数字、布尔和 ES6 中的 symbol,复合值(compound value)——对象(包括数组和封装对象，参见第 3 章)和函数，则总 是通过引用复制的方式来赋值 / 传递
* 数字类型有几个特殊值，包括 NaN(意指“not a number”，更确切地说是“invalid number”)、+Infinity、-Infinity 和 -0
* void 运算符返回 undefined
* Array 构造函数只带一个数字参数的时候，该参数会被作为数组的预设长度(length)，而 非只充当数组中的一个元素
* Function.prototype 是一个函数，RegExp.prototype 是一个正则表达式，而 Array. prototype 是一个数组。
* JSON.stringify(..) 在对象中遇到 undefined、function 和 symbol 时会自动将其忽略，统一返回undefined,在
数组中则会返回 null
* 一元运算 + 被普遍认为是显式强制类型转换
* 解析允许字符串中含有非数字字符，解析按从左到右的顺序，如果遇到非数字字符就停 止。而转换不允许出现非数字字符，否则会失败并返回 NaN
* 布尔值隐式强制类型转换。
 * (1)if (..)语句中的条件判断表达式。
 * (2)for ( .. ; .. ; .. )语句中的条件判断表达式(第二个)。
 * (3) while (..) 和 do..while(..) 循环中的条件判断表达式。
 * (4)? :中的条件判断表达式。
 * (5) 逻辑运算符 ||(逻辑或)和 &&(逻辑与)左边的操作数(作为条件判断表达式)。
* ES6 允许 从符号到字符串的显式强制类型转换，然而隐式强制类型转换会产生错误
* == 允许在相等比较中进行强制类型转换，而 === 不允许

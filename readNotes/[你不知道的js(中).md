
* JavaScript 有 七 种 内 置 类 型: String,Number,Object,Array,null,undefined,Symbol
* 变量没有类型，但它们持有的值有类型。类型定义了值的行为特征
* undefined 是变量未被复值。undeclared 则表示变量还没有被声明过，typeof都返回undefind
* 简单值(即标量基本类型值，scalar primitive)总是通过值复制的方式来赋值 / 传递，包括 null、undefined、字符串、数字、布尔和 ES6 中的 symbol,复合值(compound value)——对象(包括数组和封装对象，参见第 3 章)和函数，则总 是通过引用复制的方式来赋值 / 传递
* 数字类型有几个特殊值，包括 NaN(意指“not a number”，更确切地说是“invalid number”)、+Infinity、-Infinity 和 -0
* void 运算符返回 undefined
* Array 构造函数只带一个数字参数的时候，该参数会被作为数组的预设长度(length)，而 非只充当数组中的一个元素
* Function.prototype 是一个函数，RegExp.prototype 是一个正则表达式，而 Array. prototype 是一个数组。

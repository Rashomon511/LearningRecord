
let 和const定义对变量在window上面找不到
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

#instanceof运算符的使用

instanceof：对象与构造函数在原型链上是否有关系或者说对象与构造函数是否在同一个原型链上
```
function Aaa(){

}

var a1 = new Aaa();

alert(a1 instanceof Aaa);       // true
alert(a1 instanceof Object);    // true
alert(a1 instanceof Array);     // false
```

使用instanceof做类型判断
```
var arr = [];
var str = '';
alert(arr instanceof Array);    // true
alert(str instanceof Array);    // false
```
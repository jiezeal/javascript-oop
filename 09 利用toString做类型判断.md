#利用toString做类型判断

toString()在哪？
```
var arr = [];
alert( arr.toString );      // function toString() { [native code] }

function Aaa(){

}
var a1 = new Aaa();
alert( a1.toString );       // function toString() { [native code] }
```

通过下面的例子可以看出，系统对象下面toString是自带的，自定义对象下面则是通过原型链找Object对象
```
var arr = [];
alert( arr.toString == Object.prototype.toString );     // false

function Aaa(){

}
var a1 = new Aaa();
alert( a1.toString == Object.prototype.toString );      // true
```
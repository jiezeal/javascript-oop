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

```
var arr = [];
alert( arr.toString == Object.prototype.toString );     // false

function Aaa(){

}
var a1 = new Aaa();
alert( a1.toString == Object.prototype.toString );      // true
```
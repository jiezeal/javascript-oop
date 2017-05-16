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


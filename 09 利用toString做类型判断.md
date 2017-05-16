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

通过下面的例子可以看出，系统对象下面toString是自带的，自定义对象下面toString则是通过原型链找Object对象
```
var arr = [];
alert( arr.toString == Object.prototype.toString );     // false

function Aaa(){

}
var a1 = new Aaa();
alert( a1.toString == Object.prototype.toString );      // true
```

toString()作用：把对象转成字符串
```
var arr = [1,2,3];
alert( typeof arr.toString() );         // string
alert( arr.toString() );                // 1,2,3
```

按照自定义规则将对象转成字符串
```
var arr = [1,2,3];

Array.prototype.toString = function(){
    return this.join('+');
};

alert( typeof arr.toString() );         // string
alert( arr.toString() );                // 1+2+3
```

进制转换
```
var num = 255;
alert( num.toString(16) );         // 将255转成16进制 ff
```

利用toString做类型判断 (推荐使用这种方法来做类型判断)
```
var arr = [];
alert( Object.prototype.toString.call(arr) );       // [object Array]
alert( Object.prototype.toString.call(arr) == '[object Array]' );       // true
```

通过constructor和instanceof也可以用来做类型判断，在大多数情况下是没有问题的，可以在一些特殊情况下这两种方法就会失效
```
window.onload = function(){
    var oF = document.createElement('iframe');
    document.body.appendChild( oF );

    var ifArray = window.frames[0].Array;

    var arr = new ifArray();

    alert( arr.constructor == Array );      // false
    alert( arr instanceof Array);       // false
    alert( Object.prototype.toString.call(arr) == '[object Array]' );       // true
};
```



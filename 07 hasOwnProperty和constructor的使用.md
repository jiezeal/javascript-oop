#hasOwnProperty和constructor的使用

![](image/screenshot_1494593539769.png)

hasOwnProperty 看是不是对象自身下面的属性
```
var arr = [];
arr.num = 10;
Array.prototype.num2 = 20;

alert( arr.hasOwnProperty('num') );     // true
alert( arr.hasOwnProperty('num2') );    // false
```


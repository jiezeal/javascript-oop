#JS面向对象及组件开发

###面向对象编程的特点
抽象：抓住核心问题
封装：只能通过对象来访问方法
继承：从已有对象上继承出新的对象
多态：多对象的不同形态

###工厂方式与构造函数
```
function CreatePerson(name){
    var obj = new Object();
    obj.name = name;
    obj.showName = function(){
        alert(this.name);
    };
    return obj;
}

var p1 = new CreatePerson('小明');
p1.showName();
var p2 = new CreatePerson('小强');
p2.showName();
```

当new去调用一个函数：这个时候函数中的this就是创建出来的对象，而且函数的返回值直接就是this(隐式返回)，也就是说最后一句 return obj 可以不写。上面的函数可以优化成如下：

```
function CreatePerson(name){
    this.name = name;
    this.showName = function(){
        alert(this.name);
    }
}

var p1 = new CreatePerson('小明');
p1.showName();
var p2 = new CreatePerson('小强');
p2.showName();
```

new后面调用的函数：叫做构造函数

###对象引用是什么和它的问题
```
function CreatePerson(name){
    this.name = name;
    this.showName = function(){
        alert(this.name);
    }
}

var p1 = new CreatePerson('小明');
var p2 = new CreatePerson('小强');

alert(p1.showName == p2.showName);      // false
```

```
var a = [1,2,3];
var b = [1,2,3];
alert(a == b);  //false
```

```
var a = 5;
var b = a;
b += 3;
alert(b);   // 8
alert(a);   // 5  基本类型：赋值的时候只是值的复制
```

```
var a = [1,2,3];
var b = a;
b.push(4);
alert(b);   // 1,2,3,4
alert(a);   // 1,2,3,4  对象类型：赋值不仅是值的复制，而且也是引用的传递
```

```
var a = [1,2,3];
var b = a;
b = [1,2,3,4];  // 赋值操作会在内存中新开一块空间
alert(b);   // 1,2,3,4
alert(a);   // 1,2,3
```

```
var a=5;
var b=5;
alert(a == b);  // 基本类型：值相同就为真
```

```
var a = [1,2,3];
var b = [1,2,3];
alert(a==b);    //false   对象类型：值和引用都相同才为真
```

```
var a = [1,2,3];
var b = a;
alert(a==b);    //true
```

这就是为什么 p1.showName == p2.showName 为false的原因， 每次new都会创建一个对象，都会在内存中新开一块空间。虽然两次创建的对象都有一个showName方法，但他们的引用地址却是不相同的，所以为false。那么这个false和true对我们这个程序有什么影响呢？我们现在是创建了两个对象，那么如果我们创建了200个对象或者说2000对象，那么showName是不是在内存中就存在200或者说2000份，这样的话就会极大的消耗内存。如果说让它为真的话，也就是说值相同而且引用也相同，引用相同就说明showName方法在内存中只有一份，怎么样让这个地方变成true呢，让内存中同样的方法只存在一份，这就是接下来要说的一个东西 - 原型。

原型：原型的作用就是去改写对象下面公用的方法或者属性，让公用的方法或者属性在内存中只存在一份，这样就可以提高性能

###面向对象之原型学习
```
// arr1数组求和
var arr1 = [1, 2, 3, 4, 5];

arr1.sum = function () {
    var result = 0;
    for (var i = 0; i < this.length; i++) {
        result += this[i];
    }
    return result;
};

alert(arr1.sum());       // 15


// arr2数组求和
var arr2 = [2, 3, 4, 5, 6];

arr2.sum = function () {
    var result = 0;
    for (var i = 0; i < this.length; i++) {
        result += this[i];
    }
    return result;
};

alert(arr2.sum());      // 20
```

用原型改写：
```
// 原型：prototype：要写在构造函数的下面
var arr1 = [1, 2, 3, 4, 5];
var arr2 = [2, 3, 4, 5, 6];

Array.prototype.sum = function () {
    var result = 0;
    for (var i = 0; i < this.length; i++) {
        result += this[i];
    }
    return result;
};

alert(arr1.sum());		// 15
alert(arr2.sum());		// 20
```

普通方式与原型的优先级 (普通方式的优先级高)
```
var arr = [];
arr.number = 10;
Array.prototype.number = 20;

alert(arr.number);  // 10
```





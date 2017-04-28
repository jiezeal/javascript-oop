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

这就是为什么 p1.showName == p2.showName 为true的原因





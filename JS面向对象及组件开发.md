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


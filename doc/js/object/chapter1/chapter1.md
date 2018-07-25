# 创建对象三种方式
> 方式: 直接量{} 、关键字new 和Object.create()

- 直接量 {}
```js
    var empty = {}; //空对象
    var point = { x: 0, y: 0} //这是两个属性的对象

   // 注意：ES5 保留字可以用做不带引号的属性名，ES3使用保留字作为属性名必须使用引号引起来;
```
- new 创建对象
>new 运算符创建并初始化一个新对象，构造函数用以初始化一个新创建的对象。

    js语言核心中的原始类型都包含内置构造函数。new Object();new Array(); new Date();new RegExp();
```js
    var obj = new Base();
    //new 操作什么
    var obj = {}; //创建空对象
    obj.__proto__ = Base.prototype; //将空对象的__proto__ 指向Base函数的prototype成员对象
    Base.call(obj);  
    //call apply用法
    //求数组的最大值
    //Math.max.apply(null,[1,2,3,5,11,44,11,33]);

```

    每一个js对象(null除外)都和原型关联，对象都从继承属性； 所有通过对象直接量创建的对象都具有一个同
    一个对象原型，Oject.prototype；通过new和构造函数调用创建的对象的原型就是构造函数的prototype的
    值；因此 {}和new Object()创建的对象也继承自Object.prototype
 
- Object.create()
> 语法：Object.create(prototype, descriptors) prototype: 原型对象、descriptors为属性(一个多个)描述符
> return: 一个具有指定内部原型且包含指定的属性的新对象

    ES5定义名为Object.create(param1,param2)， param1创建对象的原型，param2用以对对象的属性进行进一步描述；
    Object.create()是一个静态函数，使用它的方法很简单，只需要传入原型即可；var o1 = Object.create({x:1,y:2});
    
    注意：param1 = null 时,创建了一个没有原型的新对象，新对象不继承任何东西，甚至不包括基础方法 如：toString(),也就是说它将不能和“+”一起工作了；

    创建普通的空对象 传入Object.prototype var o3 = Object.create(Object.prototype);可以通过任意原型创建新对象（换句话说，可以使任意对象可继承）；

```js   
    //思考题
    var a = {x:1};
    var b = Object.create(a);
    b.prototype === a //值
    Object.getPrototypeOf(b) === a //值

```

```js
    function inherit(p){
        if(p==null) throw TypeError();
        if(Object.create)
            return Object.create(p);
        var t = typeof p;
        if(t !=='object' && t !== 'function') throw TypeError();
        var f = function(){};
        f.prototype = p;
        return new f();
    }

    //防止库函数无意间修改那些不受你控制的对象
```

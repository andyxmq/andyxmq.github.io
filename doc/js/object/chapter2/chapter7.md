# 对象的三个属性

包括：prototype、class、extensible attribute
```
    1.原型属性
    对象的原型属性是用来继承的，这个属性如此重要、以至于我们经常把o的原型属
    性直接叫o的原型；
    原型属性是在实例对象创建之初就设置好了的，直接量创建的对象使用
    Object.prototype为他们的原型，new 创建的对象使用构造函数的prototype属
    性作为它们的原型,通过Object.create()创建对象使用第一个参数作为它们的原型；

    Object.getPrototypeOf() //查询函数的原型  ES3 o.constructor.prototype来检测一个对象的原型

    通过new表达式创建的对象，通常继承一个constructor属性，这个属性指创建这
    个对象的构造函数；通过对象直接量或Object.create()创建对象包含一个名为
    constructor的属性，这个属性指Object()构造函数，因此，
    Constructor.prototype才是真正的原型；

    要检测一个对象是否是另一个对象的原型，isPrototypeOf()方法


    2.类属性
    
    对象的类属性是一个字符串，用以表示对象的类型信息， ES3 ES5都未提供设置
    这个属性方法，并只有一种间接方法可以查询它，toString()
    （继承自Object.prototype）返回如下字符串 [object class]

    因此 要想获得对象类，可以调用对象的toString()方法

    function classOf(o){
        if(o===null) return "Null";
        if(o===undefined) return "Undefined";
        return Object.prototype.toString.call(o).slice(8,-1)
    }

    3.可扩展属性
    表示是否可以给对象添加新的属性。所有内置对象和自定义对象都是显式可扩展
    的；宿主对象的扩展性是js引擎定义的，ES5中，所有的内置对象和自定义对象都
    是可扩展的；同理 宿主对象的可扩展性也是js引擎定义的；

    ES5定义用来查询或设置对象可扩展性的函数，Object.esExtensible()来判断
    该对象是否是可扩展的，转化成不可扩展的Object.preventExtensions()；
    
    注意：一旦转换成不可扩展的，就不能转化回去；preventExtensions() 
    只影响到对象本身的扩展性，不影响对象的原型
```
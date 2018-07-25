# 检测属性

```
    js对象可以看做属性的结合，判断某个属性是否存在于某个对象中： in运算符、
    hasOwnProperty()、propertyISEnumerable()方法,甚至仅通过属性查询也可
    以下做到这一点； 

        in： 自有属性或继承属性中包含这个属性则返回true
        hasOwnProperty ： 检测是否为对象的自有属性；
        propertyIsEnumerable： 检测是自有属性且这个属性的可枚举为true时才
        返回true;注意： 某些内置属性是不可枚举的，通常由js创建的属性是可枚
        举的，除非es5使用特殊的方法改变属性的可枚举性；
    例子：
        var o = inherit({y:2});
        o.x = 1;
        console.log(o.propertyIsEnumerable("x")); //true
        console.log(o.propertyIsEnumerable("y")); //false
        console.log(Object.prototype.propertyIsEnumerable("toString")); //false
    除了in之外，另一种简单的方法 !== 判断一个属性是否为undefined

    in可以区分不存在的属性和存在值为undefined的属性

    注意：!== 可以区分undefined和null
```
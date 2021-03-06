# 查询和设置

## 获取属性值
>方式
- .运算符
- [] 运算符 
```
    object.property object["property"] 表达式的值相同
    .像结构体，[]像数组，区别在于这个数组元素是通过字符串索引而非数
    字索引,这种数组就关联数组，也叫散列、映射或字典；js对象都是关联数组；
```

```
    注意:
    1. 标识符不是数据类型,因此对象不能修改他们，[]来访问对象的属性，属性名
    是通过字符串来表示，字符串是js的数据类型，因此在运行程序时创建和修改他们 
    
    2. 对于.来说，右侧必须是一个以属性名称命名的简单标识符; 对于[]来说：
    是一个计算结果为字符串的表达式或者是一个可以转换为字符串的值；
    
    3. es3中 .运算符后的标识符不能是保留字；只能通过[]去访问他们  es5放宽了限制；

```

> 继承
```
    js对象属性两种：1.自有属性 2. 原型对象继承而来的 ;
    属性赋值操作首先检查原型链，以此判断是否允许赋值操作;如果o 继承一个只读
    属性x,那么赋值操作是不允许的
```

>属性 访问错误
```
    属性访问并不总是返回或设置一个值
    查询一个不存在的属性不会报错,如果在对象o自身的属性或继承的属性中均为
    找到属性x,访问o 返回undefined;
    
    如果对象不存在，那么属性就会报错，null、undefined值没有属性；
    var len = undefined;
    if(book){
        if(book.subtitle) len = book.subtitle.length;
    }

    var len = book && book.subtitle && book.subtitle.length;

    注意：给null和undefined设置属性也会报类型错误，有一些属性是只读的，
    不能重新复制；有一些对象不允许新增属性；意外的是设置这些属性失败操作
    不会报错；

    //内置构造函数的原型式只读的
    Object.prototype = o;//赋值失败，但没有报错这个bug 在es5的严格模式
    中已经修复，严格模式中，任何失败的属性设置操作都会抛出一个类型错误异常；

    以下场景给对象o设置属性p会失败：
    1. 属性p只读，不能给只读属性重新赋值
    2. 属性p是继承属性，且它是只读：不能通过同名的自有属性覆盖只读的继承属性。
    3. o不存在自有属性p: o没有使用setter方法继承属性p,并且o的可扩展性是false;
```
# 属性的特性
```
 属性除了名字、值外、一组特性：可写、可枚举、可配置特性 ES3中无法设置这些特
 性，ES3程序创建的属性都是可写的、可枚举的、可配置的，且无法对这些特性做修
 改；

  ES5提供修改这些特性的API：
  1. 通过这些API给原型对象添加方法，将这些方法设置成不可枚举的，让他们看起来
  更像内置的方法；
  2. API给对象属性定义不能修改或删除的属性，借此锁定这个对象

  数据属性包含一个名字是个特性：value、writable、enumerable、configurable
  存取器属性不具有value、writable,可写性由setter方法是否存在决定，四个属
  性：get 、set、可枚举、可配置；

  ES5实现属性特性的查询和设置操作、ES5定义了一个名为“属性描述符”的对象，这
  个对象代表四个特性(value、writable、enumerable、configurable),存取器属
  性(set,get、enumerable、configurable)

  Object.getOwnPropertyDescriptor(); 获取某个对象的属性描述符

  注意：对于继承属性和不存在的属性，返回undefined

  //设置属性特性
  Object.defineProperty(o,"prop",{value,writable,numerable,
  configurable}),对于新创建的属性来说，默认的特性值是false或undefined;
  Object.defineProperties({},{x:{},y:{}});

  规则如下：
  如果对象是不可扩展的，则可以编辑已有的自有属性，但不能给它添加新属性
  如果属性是不可配置的, 则不能修改它的可配置性和可枚举性
  如果存取器属性是不可配置的，则不能修改其getter、setter方法，也不能将它转化为数据属性。
  如果数据属性是不可配置的,则不能将她转化为存取器属性
  如果数据属性是不可配置的，则不能将她的可写性从false修改为true,但是可以从true到false
  如果数据属性是不可配置且不可写，则不能修改它的值,然而可配置但不可写属性的值是可以修改；

  Object.defineProperty(Object.prototype,"extend",{
    writable: true,
    enumerable: false,
    configurable: true,
    value: function(o){
        //得到所有自有属性，包括不可枚举属性
        var names = Object.getOwnPropertyNames(o);
        //遍历
        for(var i=0;i<names.length;i++){
            //如果属性已经存在，则跳过
            if(names[i] in this) continue;
            var desc = Object.getOwnPropertyDescriptor(o,names[i]);
            Object.defineProperty(this,names[i],desc);
        }
    }
})
```


# 属性的getter和setter
```
 对象的属性：名字、值、一组特性构成；ES5中，属性值可以用一个方法或两个方法替
 代，getter和setter;由getter和setter定义的属性称作 存取器属性(assessor
 property)，不同于数据属性(data property)。数据属性只有一个简单的值；

    当程序查询存取器属性的值时，js调用getter方法（无参数），返回值就是属性
    存取表达式的值；设置存取器属性的值时，js调用setter方法，将赋值表达式右
    侧的值当做参数传入setter 可以忽略setter的方法；

    注意：和数据属性不同，存取器属性不具有可写性;同时具有getter、setter方
    法，即为一个读写属性，只有getter方法 只读属性，setter方法，只写属性(数
    据属性中有一些例外)，读取只写属性总是返回undefined

    定义：

    var o = {
        data_prop: value,//普通的数据属性
        //存取器属性都是成对定义的函数
        get accessor_prop(){},
        set accessor_prop(){}
    };

    accessor属性定义为一个或两个同名的函数，是用set和get

    var p = {
        //普通的可读写的数据属性
        x: 1.0,
        y: 1.0,

        //r是可读写的存取器属性 getter和setter
        get r(){return Math.sqrt(this.x*this.x+this.y*this.y)},
        set r(newValue){
            var oldValue = Math.sqrt(this.x*this.x+this.y*this.y);
            var radio = newValue/oldValue;
            this.x *= radio;
            this.y *= radio;
        },
        //theta是只读存取器属性，只有getter方法
        get theta(){
            return Math.atan2(this.y,this.x);
        }
    };

    注: 和数据属性一样，存取器属性是可以继承的
    var q = inherit(p);
    q.x = 2,q.y=2;

    //严格自增的序列号
    var serialnum = {
        //数据属性包含下一个序列号
        //$符号暗示这个属性是私有属性
        $n: 0,
        //返回当前值 然后自增
        get next(){return this.$n++;},
        //给n设置新的值，但只有当它比当前值大时 才能设置成功
        set next(n){
            if(n >= this.$n) this.$n = n;
            else throw "序列号值不能小于当前值"
        }
    };

    //使用getter实现一种神奇的属性

    //这个对象有一个返回随机数的存取器属性
    //random.octet 产生一个随机数，每次产生的随机数在0~255
    var random = {
        get octet(){return Math.floor(Math.random()*256)},
        get unit16(){return Math.floor(Math.random()*65536)},
        get int16(){return Math.floor(Math.random()*65536)-32768}
    };
```



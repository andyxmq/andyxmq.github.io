# 实例

## Object.create：返回值 一个具有指定内部原型且包含指定的属性的新对象
```js
    var newObj = Object.create(null, {
        size: {
            value: "large",
            enumerable: true
        },
        shape: {
            value: "round",
            enumerable: true
        }
    });
    console.log(newObj,Object.getPrototypeOf(newObj));
    //newObj：newObj    {size: "large", shape: "round"}
    //null

    var firstLine = { x: undefined, y: undefined };

    var secondLine = Object.create(Object.prototype, {
        x: {
                value: undefined, 
                writable: true, 
                configurable: true, 
                enumerable: true
        },
        y: {
            value: undefined, 
            writable: true, 
            configurable: true, 
            enumerable: true
        }
});

```
![Image text](../image/QQ截图20180716234706.png)

```js
    class Point {
    }
    class ColorPoint extends Point {
    }

    //babel 编译后

    "use strict";

    function _possibleConstructorReturn(self, call) { 
        if (!self) { 
            throw new ReferenceError("this hasn't been initialised - super() hasn't been called"); 
        } 
        return call && (typeof call === "object" || typeof call === "function") ? call : self; 
    }

    function _inherits(subClass, superClass) { 
        if (typeof superClass !== "function" && superClass !== null) { 
            throw new TypeError("Super expression must either be null or a function, not " + typeof superClass);     
        } 
        
        subClass.prototype = Object.create(superClass && superClass.prototype, { 
            constructor: { 
                value: subClass, 
                enumerable: false, 
                writable: true, 
                configurable: true } 
            }); 
            if (superClass) 
                Object.setPrototypeOf ? 
                Object.setPrototypeOf(subClass, superClass) : subClass.__proto__ = superClass; 
    }

    function _classCallCheck(instance, Constructor) {
        if (!(instance instanceof Constructor)) { 
            throw new TypeError("Cannot call a class as a function"); 
        } 
    }

    var Point = function Point() {
        _classCallCheck(this, Point);
    };

    var ColorPoint = function (_Point) {
        _inherits(ColorPoint, _Point);

        function ColorPoint() {
            _classCallCheck(this, ColorPoint);

            return _possibleConstructorReturn(this, 
                (ColorPoint.__proto__ || Object.getPrototypeOf(ColorPoint)).apply(this, arguments));
        }
        return ColorPoint;
    }(Point);
```


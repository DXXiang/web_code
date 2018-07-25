# Concatenating functions

标签（空格分隔）： kata5

---

> 这个看起来很简单，但是其中对于map函数参数的传入和原型链上的使用必须要有足够的了解才行，嘛，总的来说是很简单就对了

```javascript
var addOne = function(e) {return e + 1;};
var square = function(e) {return e * e;};
Function.prototype.pipe = function (x) {
    var tem = this;
    return function (e) {
      return x(tem(e))
    };
};
alert([1,2,3,4,5].map(addOne.pipe(square)));

```

###简单写法(emmm,bind)，因为有bind所以可以直接把this传进去
```javascript
Function.prototype.pipe = function(fun) {
  return function(param) {
    return fun(this(param));
  }.bind(this);
};
```

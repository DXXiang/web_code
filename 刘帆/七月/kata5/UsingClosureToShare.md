# Using closures to share class state

标签（空格分隔）： kata5

---

> 闭包和原型链再加上error抛出复杂的一逼，先学习

```javascript
// Let's make a Cat constructor!
var Cat = (function () {
  var cats = {
    count: 0,
    totalWeight: 0,
    avgWeight: 0
  }
  
  function Cat (name, weight) {
    if (!name || !weight) {
      throw new Error('Both `name` and `weight` should be provided');
    }
    cats.count++;
    this.name = name;

    Object.defineProperty(this, 'weight', {
      get: function () {
        return this._weight || 0;
      },
      set: function (val) {
        cats.totalWeight = cats.totalWeight - this.weight + val;
        cats.avgWeight =  cats.totalWeight / cats.count;
        return this._weight = val;
      }
    });

    this.weight = weight;
  }
  
  Cat.averageWeight = function () {
    return cats.avgWeight;
  }
  
  return Cat;
  
}());
```





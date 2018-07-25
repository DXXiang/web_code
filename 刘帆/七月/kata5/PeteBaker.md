# Pete,the baker

标签（空格分隔）： kata5

---

> 烤面包，不同配方，不同材料，求最少的个数，简单，只不过用的是对象，注意一下

```javascript
function cakes(recipe, available) {
    var arr = [];// TODO: insert code
    var arr1 = [];
    for(let i in recipe)
        arr.push(i);
    for(let i = 0;i<arr.length;i++)
    {
        let temp = arr[i];
        if(!available[temp])
            return 0;
        let temp1 = available[temp]/recipe[temp];
         arr1.push(Math.floor(temp1));
    }
    arr1 = arr1.sort(function (a, b) { return a-b });
    return arr1[0];
}
```
### 简单写法（为什么这些人每次都能五行解决）
```javascript
function cakes(recipe, available) {
  return Object.keys(recipe).reduce(function(val, ingredient) {
    return Math.min(Math.floor(available[ingredient] / recipe[ingredient] || 0), val)
  }, Infinity)  
}
```






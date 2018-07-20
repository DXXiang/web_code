# Number that are a power of their sum of digits

标签（空格分隔）： kata5

---

> 意思比较难懂的一道题，但是读懂后只要注意一下边界即可做出

```javascript
function powerSumDigTerm(n) {
    var arr = [];// your code
    for(var i = 2;i<100;i++)
    {
        for(var j = 2;j<100;j++)
        {
            var num = Math.pow(i,j);
            if(num>100000000000000000000)
                break;
            var test = eval((num+"").split("").join("+"));
            if(test === i)
                arr.push(num);
        }
    }
    return arr.sort(function (a, b) { return a-b })[n-1];
}
```

### 简单写法
```javascript
let series = [0];
for (let a = 2; a < 100; a++) {
  for (let b = 2; b < 42; b++) {
    let c = Math.pow(a, b);
    if (c.toString().split('').reduce((x,y) => x + parseInt(y), 0) === a) {
      series.push(c);
    }
  }
}
series = series.sort((a, b) => a - b);
var powerSumDigTerm = n => series[n];
```
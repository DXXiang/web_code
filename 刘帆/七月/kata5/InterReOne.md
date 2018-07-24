# Integers: Recreation One

标签（空格分隔）： kata5

---

>这是一道数学题
```javascript
function listSquared(m, n) {
    var arr = [];// your code
    var arr1 = [];
    for (var i = m;i<=n;i++)
    {
        for(var j = 1;j<=i;j++)
            if(i%j === 0)
                arr.push(j);
        arr = arr.map(function (value) { return value*value });
        var sum = eval(arr.join("+"));
        for (var k = 0;k*k<=sum; k++)
            if (k * k === sum)
                arr1.push([i,sum]);
        arr = [];
    }
    return arr1;
}
```

###数学写法
```javascript
function listSquared(m, n) {
  var arr = [];
  for (var i = m; i <= n; i++){
    var temp = 0;
    for (var j = 1; j <= i; j++) {
      if ( i % j == 0) temp += j*j;  
    };
    if ( Math.sqrt(temp) % 1 == 0) arr.push([i, temp]);
  };
  return arr;
}
```
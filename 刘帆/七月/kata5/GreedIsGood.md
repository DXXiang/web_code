# Greed is good 

标签（空格分隔）： kata5

---
> 骰子游戏，三个相同数字可以得到一个超大分数，不同数字有不同分数，有的数字则没有分数


```javascript
function score( dice ) {
    var ops = {
        1: 1000, 6: 600, 5: 500, 4: 400,
        3: 300, 2: 200, "a": 100, "b": 50
    };// Fill me in!
    var num = 0,sum=0;
    var arr1 = [];
    for (var i = 1; i < 7; i++)
        for (var j = 0; j < 5; j++) {
            if (i === dice[j])
                num++;
            if (j === 4) {
                arr1.push(num);
                num = 0;
            }
        }
    if(arr1[0]>2)
    {
        sum=ops[1]+(arr1[0]-3)*ops["a"];
        if(arr1[4])
            sum+=arr1[4]*ops["b"];
        return sum;
    }
    if(arr1[4]>2)
    {
        sum=ops[5]+(arr1[4]-3)*ops["b"];
        if(arr1[0])
            sum+=arr1[0]*ops["a"];
        return sum;
    }
    if(arr1[0])
        sum+=arr1[0]*ops["a"];
    if(arr1[4])
        sum+=arr1[4]*ops["b"];
    for (var k = 0;k<6;k++)
    {
        if(arr1[k]>=3)
            sum+=ops[k+1];
    }
    return sum;
}
```
--- 
### 简单写法
```javascript
function score( dice ) {
  var dc = [0,0,0,0,0,0];
  var tdr = [1000,200,300,400,500,600];
  var sdr = [100,0,0,0,50,0];
  dice.forEach(function(x){ dc[x-1]++; });
  return dc.reduce(function(s,x,i){ 
    return s + (x >= 3? tdr[i] : 0) + sdr[i]*(x % 3);
  },0);
}
```
### 方便理解写法（推荐，表扬）
```javascript
function score( dice ) {
  var six=0, five=0, four=0, three=0, too=0, one=0;
  var i = 0;
  while (i < 5) {
    if (dice[i] == 6) { six++; }
    if (dice[i] == 5) { five++; }
    if (dice[i] == 4) { four++; }
    if (dice[i] == 3) { three++; }
    if (dice[i] == 2) { too++; }
    if (dice[i] == 1) { one++; }
    i++;
  }
  var r = 0;
  if (one > 2) { r += 1000; one -= 3;}
  if (six > 2) { r += 600; }
  if (five > 2) { r += 500; five -= 3;}
  if (four > 2) { r += 400; }
  if (three > 2) { r += 300; }
  if (too > 2) { r += 200; }
  r += one * 100;
  r += five * 50;
  return r;
}
```
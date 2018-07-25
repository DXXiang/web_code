# Fibo akin

标签（空格分隔）： kata5

---

> 想复杂了，反而浪费了时间，读题还真是有趣啊，这个阶段是真的神奇，上可以编码解码代码几百行，下可以数组对象轻松解

```javascript
function lengthSupUK(n, k) {
    var arr = [1,1],num = 0;// your code
    for(var i = 3;i<=n;i++)
        arr.push(arr[i-arr[i-2]-1]+arr[i-arr[i-3]-1]);
    arr.map(function (value) {if(value>=k) num++;});
    return num;
}
function comp(n) {
    var arr = [1,1],num = 0;// your code
    for(var i = 3;i<=n;i++)
        arr.push(arr[i-arr[i-2]-1]+arr[i-arr[i-3]-1]);
    for(i = 0;i<n;i++)
    {
        var j = i+1;
        if(arr[i]>arr[j])num++;
    }
    return num;
}
```
###简单写法（哦，好像我的更好看哦）
```javascript
function u1(n) {
    var memu = [1, 1];
    var i = 2;
    while (i < n) {
        memu.push(memu[i - memu[i - 1]] + memu[i - memu[i - 2]]);
        i++;
    }
    return memu;
}

function lengthSupUK(n, k) {
    return u1(n).filter(function (x) { return (x >= k); }).length;
}

function comp(n) {
    var memu = u1(n);
    var prev = 1, cnt = 0, i = 1;
    while (i < n) {
        var cur = memu[i];
        if (cur < prev)
            cnt++;
        prev = cur;
        i++;
    }
    return cnt;
}
```





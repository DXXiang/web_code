# What's a Perfect Power anyway?

标签（空格分隔）： kata5

---
> 题意是求得 m<sup>k</sup> = n中的m和k，要注意时间

利用Math.pow，减少算法复杂度的话是i*i < n，代码如下

```javascript
var isPP = function(n){
    let arr = [];
    for(let i = 2;i*i<=n;i++)
        for(let j = 2;j<n;j++)
        {
            let num = Math.pow(i,j);
            if(num>n)
                break;
            if(num === n)
            {
                arr.push(i);
                arr.push(j);
            }
        }
        if(arr.length)
            return arr;
    return null; // fix me
};
```

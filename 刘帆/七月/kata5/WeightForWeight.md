# Weight for weight

标签（空格分隔）： kata5

---

> 我升段啦！这个题目首先数字的权重弄了我半天，"weight"，原来不是加权的权重，是数字相加，然后排序是按字母排序，比较简单，但是要注意输入，用正则挑出数字就好，还会有输入null的情况，也要个if

```javascript
function orderWeight(strng) {
    let reg = /[0-9]+/g;// your code
    let arr = [];
    arr = strng.match(reg);
    if(!arr)
        return ;
    arr = arr.sort(function (a, b) {
        if(a === b)
            return 0;
        var a1 = eval((a+"").split("").join("+"));
        var b1 = eval((b+"").split("").join("+"));
        if(a1 === b1)
        {
            var arr = [a,b].sort();
            if(arr[0]===a)
                return -1;
            else
                return 1;
        }
        return a1-b1;
    });
    return arr.join(" ");
}
```

### 简单写法（用了es6）
```javascript
function orderWeight(str) {
  const sum = x => x.split('').reduce((res, cur) => (res + +cur), 0);
  return str.split(' ').sort((a, b) => {
    const diff = sum(a) - sum(b);
    return diff == 0 ? (a > b ? 1 : -1) : diff;
  }).join(' ');
}
```
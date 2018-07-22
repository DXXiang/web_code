# Find the smallest

标签（空格分隔）：kata5 

---

> 牛逼，这题真鸡儿难，某个数移动位置求出移动后的最小，但是要带上下标，同时还要注意会有10000这样的多个最小情况，就是这个下标这个磨人的小妖精，最后我用二维数组加Math.min.apply求最小分别搞定下标和最小，( •̀ ω •́ )y

```javascript
function smallest(n) {
    var arr = (n+"").split("");// Your code
    var arr1 = [],arr2=[];
    for (var i = 0;i<arr.length;i++)
        for(var j = 0;j<arr.length;j++)
        {
            arr1.push(swap(arr,i,j));
            arr1.push(swap(arr,j,i));
        }
        for (var k = 0;k<arr1.length;k++)
            arr2.push(arr1[k][0]);
        var min = Math.min.apply(null,arr2);
        for ( k = 0;k<arr1.length;k++)
        {
            if(arr1[k][0] === min)
            {
                var index = k;
                break;
            }
        }
    return arr1[index];
}
function swap(arr1,a,b){
    var arr = arr1;
    var temp = arr[a];
    arr.splice(a,1);
    arr.splice(b,0,temp);
    return [+arr.join(""),a,b]
}

```

### 简单写法（哈哈哈，这次他们也不简单）
```javascript
function smallest(n) {
    var s = n.toString(), tmp = s, mem = [-1, -1, -1];
    var l = s.length;
    for (var i = 0; i < l; i++) {
        var c = s.charAt(i);
        var str1 = s.substring(0, i) + s.substring(i+1, l);
        for (var j = 0; j < l; j++) {
            var str2 = str1.substring(0, j) + c + str1.substring(j, str1.length);
            var cmp = str2.localeCompare(tmp);
            if (cmp < 0) {
                tmp = str2;
                mem[0] = parseInt(tmp);  mem[1] = i; mem[2] = j;
            }
        }
    }
    if (mem[0] === -1) {
      mem[0] = n;  mem[1] = 0; mem[2] = 0;
    }
    return mem;
}
```

> 补充，幸亏先把删除与插入写成一个函数，不然真鸡儿蛋疼，虽然已经很蛋疼就是了





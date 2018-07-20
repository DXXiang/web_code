# Directions Reduction

标签（空格分隔）： kata5

---

> 对于["NORTH", "SOUTH", "EAST", "WEST"]的排列规则，如果其中某两个是符合规则的话，便能够通过，不是的话被留出，要注意这中间可能有无数符合规则的排列，用了一种简单易懂的递归

```javascript
function dirReduc(arr){

    function compare(a,b)
    {
        if(a+b==="NORTHSOUTH"||a+b==="SOUTHNORTH")
            return true;
        if(a+b === "EASTWEST"||a+b ==="WESTEAST")
            return true;
        return false
    }
    beZero(arr);
    function beZero(ar) {
        for (var j = 0; j < ar.length; j++) {
            if (compare(ar[j],ar[j+1])) {
                ar.splice(j,2);
                beZero(ar);
                break;
            }
        }
    }
    return arr;
}
```





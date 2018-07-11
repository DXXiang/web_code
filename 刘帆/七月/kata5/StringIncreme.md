# String incrementer

标签（空格分隔）： kata5

---

> 分情况讨论，在不同情况下字符串最后一位加个1，总共if大约需要三个

``` javascript
function incrementString (strng) {
   let reg = /[0-9]+$/;
   if(reg.test(strng))
   {
        let num = strng.match(reg);
        let reg0 = /^0/;
        num = (num+"").split("");
        let str = strng.slice(0,strng.length-num.length);
        if(reg0.test(num+""))
        {
            let arr = "";
            for(let i = 0;i<num.length;i++)
            {
                if (i === num.length - 1)
                {
                    arr += num[i];
                    break;
                }
                if(num[i]!=="0") {
                    arr += num[i];
                }
            }
            let reg1 = /0$/;
            let arr_num = parseInt(arr)+1;
            let k = [];
            for(let i = 0;i<num.length-arr.length;i++)
                k.push("0");
            if(reg1.test(arr_num+"")&&num.length !== arr.length)
            {
                k = k.slice(0,k.length-1).join("");
                return str+(k+arr_num);
            }
            k = k.join("");
            return str+(k+arr_num);
        }
        return str+(parseInt(num.join(""))+1);
   }
   return strng+"1";
}
```
### 简单写法
```javascript
function incrementString(input) {
  if(isNaN(parseInt(input[input.length - 1]))) return input + '1';
  return input.replace(/(0*)([0-9]+$)/, function(match, p1, p2) {
    var up = parseInt(p2) + 1;
    return up.toString().length > p2.length ? p1.slice(0, -1) + up : p1 + up;
  });
}
```
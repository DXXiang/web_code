# Resistor color 2

标签（空格分隔）： kata5

---

> 根据字符串解析得到数字后得到代表的颜色，注意单位

```javascript
function encodeResistorColors(ohmsString) {
    var arr = ohmsString.split(" "),arr1 = [];
    var parts = ohmsString.match(/^(\d+(\.\d+)?)([kM]?)/)
    console.log(parts) //match牛逼啊
    var obj = {0: "black", 1: "brown", 2: "red", 3: "orange", 4: "yellow", 5: "green", 6: "blue", 7: "violet", 8:"gray", 9: "white","5%":"gold","10%":"silver"};
    var num = arr[0].indexOf("k")>-1?arr[0].replace(/k/,"")*1000:arr[0]; //这里可以同样用对象搞定
    num = arr[0].indexOf("M")>-1?arr[0].replace(/M/,"")*1000000:num;
    var ten = -1;var num1 = num;
    while((/(^[0-9]*[1-9][0-9]*$)/.test(num1+"")))//这么多实际上就等于 ten = num.length-2
    {
        if(/^[0-9]0$/.test(num1))
        {
            ten++;
            break;
        }
        num1/=10;
        ten++;
    }
    num = num/Math.pow(10,ten);
    arr = (num+"").split("");
    arr1.push(obj[arr[0]]);arr1.push(obj[arr[1]]);arr1.push(obj[ten]);
    return arr1.join(" ")+" gold";
    // your code here
}
```
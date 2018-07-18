# Resistor color

标签（空格分隔）： kata5

---

> 根据字符串解析得到颜色后得到代表的数字，注意单位M,k

```javascript
function decodeResistorColors(bands) {
    var arr = bands.split(" ");
    var obj = {"black": 0, "brown": 1, "red": 2, "orange": 3, "yellow": 4, "green": 5, "blue": 6, "violet": 7, "gray": 8, "white": 9,"gold":"5%","silver":"10%"};
    var num = "";
    for(var i = 0;i<3;i++)
    {
        if(i === 2)
        {
            num = num * Math.pow(10, obj[arr[i]]);
            break;
        }
        num += obj[arr[i]]+"";
    }
    num = parseInt(num)>=1000?(parseInt(num)>=1000000?(num/1000000)+"M":parseInt(num)/1000+"k"):num;
    if(arr[3])
        num += " ohms, "+obj[arr[3]];
    else
        num +=" ohms, "+"20%";
    return num;
}
```
# Rot13

标签（空格分隔）： kata5

---

> 非常简单的加密算法，和另外一道题来说简直不值一提

```javascript
function rot13(message){
    let arr = message.split("");//your code here
    arr = arr.map(function (value) {
        value = value.charCodeAt();
        if(value<=122&&value>=97||value<=90&&value>=65)
        {
            if(value+13>90&&value<97)
            {
                value = value - 13;
            }
            else if(value+13>122)
                value = value - 13;
            else
                value = value + 13;
        }
        return String.fromCharCode(value);
    });
    return arr.join("");
}
```

### 简单写法

``` javascript
function rot13(message) {
  var a = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ"
  var b = "nopqrstuvwxyzabcdefghijklmNOPQRSTUVWXYZABCDEFGHIJKLM"
  return message.replace(/[a-z]/gi, c => b[a.indexOf(c)])
}
```





# Battle ships

标签（空格分隔）： kata5

---

> 此题过难，告辞，开玩笑的
> 实际上还是有比较清晰的解决思路的，但是对数据结构的不了解，没用map真心太伤，首先用三维数组记录出不同船的坐标组，然后用攻击的坐标去掉这些坐标中被攻击的，最后检查得出摧毁，损坏以及所得分数情况，这简直就是一个小游戏了

前两步的代码如下
```javascript
for(let i = 0;i<board.length;i++)//the battle starts here!
        for(let j = 0;j<board[i].length;j++)
        {
            var board_num = board[i][j];
            let temp = [i,j];
            switch (board_num){
                case 1:
                    arr[0].push(temp);break;
                case 2:
                    arr[1].push(temp);break;
                case 3:
                    arr[2].push(temp);break;
            }
        }
        for(let i = 0;i<attacks.length;i++)
            for(let j = 0;j<arr.length;j++)
                for(let k = 0;k<arr[j].length;k++)
                {
                    let a = attacks[i].toString();
                    let b = arr[j][k].toString();
                    if(a===b)
                        arr[j][k] = 0;
                }
```
> 完整实现 

```javascript
function damagedOrSunk (board, attacks){

  let ships = {}
  board.map((x, i) => x.map((y, j) => {
    let cell = board[i][j]
    if (cell) {
      ships[cell] = ++ships[cell] || 1
    }
  }))

  let state = Object.assign({}, ships)
  for (let [x, y] of attacks) {
    let cell = board[board.length-y][x-1]
    if (cell && state[cell]) {
      state[cell] -= 1
    }
  }

  let sunk = Object.keys(state).filter(x => state[x] == 0).length;
  let damaged = Object.keys(state).filter(x => state[x] != ships[x]).length - sunk
  let notTouched = Object.keys(ships).length-sunk-damaged

  return {sunk,damaged,notTouched,points: sunk-notTouched+damaged*0.5}
}
```

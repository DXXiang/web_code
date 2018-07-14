# Battle ships

标签（空格分隔）： kata5

---

> 此题过难，告辞，开玩笑的
> 实际上还是有比较清晰的解决思路的，但是对数据结构的不了解，没用map真心太伤，首先用三维数组记录出不同船的坐标组，然后用攻击的坐标去掉这些坐标中被攻击的，最后检查得出摧毁，损坏以及所得分数情况，这简直就是一个小游戏了


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





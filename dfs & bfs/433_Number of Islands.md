# 433 : Number of Islands

### Company

`Microsoft`, `Facebook`, `Amazon`, `Google`, `Zenefits`, `Uber`

### Tags

`Breadth First Search/BFS`, `Union Find`

### 문제 설명

---

#### Description

Given a boolean 2D matrix, 0 is represented as the sea, 1 is represented as the island. If two 1 is adjacent, we consider them in the same island. We only consider up/down/left/right adjacent.

Find the number of islands.
asdfasdfasdfasdfasdf

#### Example

Example 1:

```
Input:
[
  [1,1,0,0,0],
  [0,1,0,0,1],
  [0,0,0,1,1],
  [0,0,0,0,0],
  [0,0,0,0,1]
]
Output:
3
```

Example 2:

```
Input:
[
  [1,1]
]
Output:
1
```

<br>

### 나의 풀이

---

- The first solution seems to return the result that I want, but it caused a runtime error.

```js
export class Solution {
  /**
   * numIslands
   *
   * @param grid: a boolean 2D matrix
   * @return: an integer
   */
  numIslands(grid) {
    let count = 0;

    function bfs(row, col, matrix) {
      matrix[row][col] = 0;

      let right = grid[row][col + 1];
      left = grid[row][col - 1];
      down = grid[row + 1] ? grid[row + 1][col] : undefined;
      up = grid[row - 1] ? grid[row - 1][col] : undefined;

      if (right === 1) return bfs(row, col + 1, matrix);
      else if (left === 1) return bfs(row, col - 1, matrix);
      else if (down === 1) return bfs(row + 1, col, matrix);
      else if (up === 1) return bfs(row - 1, col, matrix);
      else if (!up && !down && !right && !left) {
        count++;
        return matrix;
      }
    }

    for (let row = 0; row < grid.length; row++) {
      for (let col = 0; col < grid[row].length; col++) {
        if (grid[row][col] === 1) grid = bfs(row, col, grid);
      }
    }

    return count;
  }
}
```

- Second trial on [LeetCode](https://leetcode.com/problems/number-of-islands/)

```js
/**
 * @param {character[][]} grid
 * @return {number}
 */
var numIslands = function(grid) {
    let count = 0;

    function isIsland(row, col) {
        if(
            row >=0 && row < grid.length &&
            col >=0 && col < grid[0].length
            grid[row][col] === '1'
        ) {
            grid[row][col] = '0'

            isIsland(row+1, col)
            isIsland(row-1, col)
            isIsland(row, col+1)
            isIsland(row, col-1)
        }
    }

    for(let i=0; i < grid.length; i++) {
        for(let j=0; j < grid[0].length; j++) {
            if(grid[i][j] === '1') {
                isIsland(i, j);
                count++;
            }
        }
    }

    return count;
};
```

<br>

### 다른 사람 풀이

---

- It's neatly written.
- We don't need to pass the grid as an argument for the function bfs/dfs because the problem doesn't consider various paths of going through the island.

```js
const numIslands = (grid) => {
  const isIsland = (i, j) =>
    i >= 0 &&
    i < grid.length &&
    j >= 0 &&
    j < grid[i].length &&
    grid[i][j] === "1";

  const bfs = (i, j) => {
    const queue = [[i, j]];

    while (queue.length) {
      const [i, j] = queue.shift();

      grid[i][j] = "0";

      if (isIsland(i + 1, j)) queue.push([i + 1, j]);
      if (isIsland(i, j + 1)) queue.push([i, j + 1]);
      if (isIsland(i - 1, j)) queue.push([i - 1, j]);
      if (isIsland(i, j - 1)) queue.push([i, j - 1]);
    }
  };

  let counter = 0;

  for (let i = 0; i < grid.length; i += 1) {
    for (let j = 0; j < grid[i].length; j += 1) {
      if (grid[i][j] === "1") {
        counter += 1;
        bfs(i, j);
      }
    }
  }

  return counter;
};
```

<br>

### Record

---

Leetcode

- Runtime: 88 ms, faster than 65.54% of JavaScript online submissions for Number of Islands.
- Memory Usage: 41.4 MB, less than 67.46% of JavaScript online submissions for Number of Islands.

#### Level

`medium`

<br>

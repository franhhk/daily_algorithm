1225 · Island Perimeter
===
### Company
`Google`

### Tags
`Breadth First Search/BFS`, `Enumerate`

### 문제 설명
---
#### Description
You are given a map in form of a two-dimensional integer grid where 1 represents land and 0 represents water. Grid cells are connected horizontally/vertically (not diagonally). The grid is completely surrounded by water, and there is exactly one island (i.e., one or more connected land cells). The island doesn't have "lakes" (water inside that isn't connected to the water around the island). One cell is a square with side length 1. The grid is rectangular, width and height don't exceed 100. Determine the perimeter of the island.

#### Example
Example 1:
```
[[0,1,0,0],
 [1,1,1,0],
 [0,1,0,0],
 [1,1,0,0]]

Answer: 16
```

<br>

### 나의 풀이
---
```js
export class Solution {

  /**
   * islandPerimeter
   *
   * @param grid: a 2D array
   * @return: the perimeter of the island
   */
  islandPerimeter(grid) {
      let perimeter = 0;
    function count(row, col) {
        if(row === 0 ||grid[row-1][col] === 0) perimeter++;
        if(row === grid.length - 1 || grid[row+1][col] === 0) perimeter++;
        if(col === 0 ||grid[row][col-1] === 0) perimeter++;
        if(col === grid[0].length - 1 || grid[row][col+1] === 0) perimeter++;
    }

    for(let i = 0; i < grid.length; i++) {
        for(let j = 0; j < grid[0].length; j++) {
            if(grid[i][j] === 1) count(i, j);
        }
    }

    return perimeter;
  }

}
```
<br>

### 다른 사람 풀이
---

```
<br>

### Record
---
- `101 ms` time cost
- `9.70 MB` memory cost
- Your submission beats `100.00%` Submissions
- `easy`

<br>

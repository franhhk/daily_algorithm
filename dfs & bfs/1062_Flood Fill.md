1062 · Flood Fill
===
### Company
`Uber`

### Tags
`Breadth First Search/BFS`, `Depth First Search/DFS`

### 문제 설명
---
#### Description
An image is represented by a 2-D array of integers, each integer representing the pixel value of the image (from 0 to 65535).

Given a coordinate (sr, sc) representing the starting pixel (row and column) of the flood fill, and a pixel value newColor, "flood fill" the image.

To perform a "flood fill", consider the starting pixel, plus any pixels connected 4-directionally to the starting pixel of the same color as the starting pixel, plus any pixels connected 4-directionally to those pixels (also with the same color as the starting pixel), and so on. Replace the color of all of the aforementioned pixels with the newColor.

At the end, return the modified image.

The length of image and image[0] will be in the range [1, 50].
The given starting pixel will satisfy 0 <= sr < image.length and 0 <= sc < image[0].length.
The value of each color in image[i][j] and newColor will be an integer in [0, 65535].

#### Example
Example 1:
```
Input: 
image = [[1,1],[0,0]]
sr = 0, sc = 0, newColor = 2
Output: [[2,2],[0,0]]
```
Example 2:
```
Input: 
image = [[1,1,1],[1,1,0],[1,0,1]]
sr = 1, sc = 1, newColor = 2
Output: [[2,2,2],[2,2,0],[2,0,1]]
Explanation: 
From the center of the image (with position (sr, sc) = (1, 1)), all pixels connected 
by a path of the same color as the starting pixel are colored with the new color.
Note the bottom corner is not colored 2, because it is not 4-directionally connected
to the starting pixel.
```

<br>

### 나의 풀이
---
- Learned quickly from the previous problem I solved, thus wrote a much cleaner code.
- I missed out on the exception. Should take more caution next time!
```js
export class Solution {

  /**
   * floodFill
   *
   * @param image: a 2-D array
   * @param sr: an integer
   * @param sc: an integer
   * @param newColor: an integer
   * @return: the modified image
   */
  floodFill(image, sr, sc, newColor) {
    if(image[sr][sc] === newColor) {
        return image;
    }
    function bfs(row, col, curColor) {
        if(
            row >= 0 && row < image.length &&
            col >= 0 && col < image[0].length &&
            image[row][col] === curColor
        ) {
            image[row][col] = newColor

            bfs(row+1, col, curColor)
            bfs(row-1, col, curColor)
            bfs(row, col+1, curColor)
            bfs(row, col-1, curColor)
        }
    }

    bfs(sr, sc, image[sr][sc]);

    return image
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
- `8.77 MB` memory cost
- Your submission beats `100.00%` Submissions
- `easy`

<br>

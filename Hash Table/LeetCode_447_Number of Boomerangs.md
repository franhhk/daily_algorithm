447 . Number of Boomerangs
===
### Link
https://leetcode.com/problems/number-of-boomerangs/

### Company
`Google`

### Tags
`Hash Table`

### 문제 설명
---
#### Description
You are given n points in the plane that are all distinct, where points[i] = [xi, yi]. A boomerang is a tuple of points (i, j, k) such that the distance between i and j equals the distance between i and k (the order of the tuple matters).

Return the number of boomerangs.

#### Example
Example 1:
```
Input: points = [[0,0],[1,0],[2,0]]
Output: 2
Explanation: The two boomerangs are [[1,0],[0,0],[2,0]] and [[1,0],[2,0],[0,0]].
```
Example 2:
```
Input: points = [[1,1],[2,2],[3,3]]
Output: 2
```
Example 3:
```
Input: points = [[1,1]]
Output: 0
```
<br>

### 나의 풀이
---
- This solution works but has a high time complexity thus time limit exceeded.
```js
/**
 * @param {number[][]} points
 * @return {number}
 */
var numberOfBoomerangs = function(points) {
    let count = 0;

      function makeTuple(arr1, arr2) {
          if(arr1.length === 3) {
              let a = arr1[0][0] - arr1[1][0]
              let b = arr1[0][1] - arr1[1][1]
              let distance = Math.sqrt(a*a + b*b);

              a = arr1[0][0] - arr1[2][0]
              b = arr1[0][1] - arr1[2][1]
              let candi = Math.sqrt(a*a + b*b);
              if(distance === candi) count++
          } else {
              for(let i=0; i < arr2.length; i++) {
                    let copyArr2 = arr2.slice()
                    copyArr2.splice(i, 1)
                    makeTuple([...arr1, arr2[i]], copyArr2)
                }
          }
          
      }

      makeTuple([], points)
      return count;
};
```
<br>

### 다른 사람 풀이
---
```js
var numberOfBoomerangs = function(p) {
    let n = p.length; 
    let res =0;
    for(let i = 0 ; i < n ;i++) {
        let map = {};
        for(let j = 0; j < n ; j++) {
            let dist = (p[i][0] - p[j][0]) * (p[i][0] - p[j][0]) + 
                (p[i][1] - p[j][1]) * (p[i][1] - p[j][1]);
            map[dist] = ~~map[dist] + 1;
        }
        Object.keys(map).forEach(key => {
            if(map[key] > 1) {
                res += map[key] *( map[key]-1);
            }
        })
    }
    return res;
     
};
```
<br>

### Record
---
- `medium`

<br>

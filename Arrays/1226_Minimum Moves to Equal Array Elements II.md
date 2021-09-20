1226 · Minimum Moves to Equal Array Elements II
===
### Level
`medium`

### Tags
`Array`,
`Quick Select`,
`Sort`

### 문제 설명
---
#### Description
Given a non-empty integer array, find the minimum number of moves required to make all array elements equal, where a move is incrementing a selected element by 1 or decrementing a selected element by 1.

The array can contain up to 10000 elements.
#### Example
Example 1:
```
Input:
[1,2,3]

Output:
2

Explanation:
Only two moves are needed (remember each move increments or decrements one element):

[1,2,3]  =>  [2,2,3]  =>  [2,2,2]
```
Example 2:
```
Input:
[1,2]

Output:
1

Explanation:
Only one move is needed (remember each move increments or decrements one element):

[1,2]  =>  [2,2]
```
<br>

### 나의 풀이
---
<br>

```js
export class Solution {

  /**
   * minMoves2
   *
   * @param nums: an array
   * @return: the minimum number of moves required to make all array elements equal
   */
  minMoves2(nums) {
    // 잘못된 접근
    // let avg = nums.reduce((a,c) => a+c, 0) / nums.length
    // return nums.reduce((a,c) => a + Math.abs(c - parseInt(avg)), 0)

    function countMoves(target) {
        return nums.reduce((a,c) => a = a + Math.abs(c - target), 0)
    }

    nums.sort((a,b) => a-b);
    
    let midIdx = parseInt((nums.length - 1)/2)
    let target = nums[midIdx]
    
    if(nums.length % 2 === 0) {
        let Idx = midIdx + 1
        let tempTarget = nums[Idx]

        return Math.min(countMoves(tempTarget), countMoves(target))
    } else {
        return countMoves(target)
    }
  }

}
```
<br>

### Reference Code
---
- `~~ (double tilde operator)` : same usage as `Math.floor()`
<br>

```js
var minMoves2 = function(nums) {
    nums.sort((a,b) => a - b)
    let ans = 0, median = nums[~~(nums.length / 2)]
    for (let i = 0; i < nums.length; i++) ans += Math.abs(median - nums[i])
    return ans
}
```
- Time Complexity: O(N * log N) where N is the length of nums, for sorting nums
- Space Complexity: O(1)

### 유사 문제
---
- LeetCode_1551. Minimum Operations to Make Array Equal [](https://leetcode.com/problems/minimum-operations-to-make-array-equal/)
- 긱스포긱스 : Minimum Increment / decrement to make array elements equal
<br>

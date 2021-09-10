리트코드 : Minimum Increment to Make Array Unique
===
### 링크
https://leetcode.com/problems/minimum-increment-to-make-array-unique/

<br>

### 문제 설명
---
You are given an integer array nums. In one move, you can pick an index i where 0 <= i < nums.length and increment nums[i] by 1.

Return the minimum number of moves to make every value in nums unique.

### Example 1:
```
Input: nums = [1,2,2]
Output: 1
Explanation: After 1 move, the array could be [1, 2, 3].
```
### Example 2:
```
Input: nums = [3,2,1,2,1,7]
Output: 6
Explanation: After 6 moves, the array could be [3, 4, 1, 2, 5, 7].
It can be shown with 5 or less moves that it is impossible for the array to have all unique values.
```

### Constraints:
```
1 <= nums.length <= 105
0 <= nums[i] <= 105
```
<br>

### 나의 풀이
---
<br>
-시간 복잡도: O(N)

```js
const minIncrementForUnique = function(nums) {
    let set = new Set()
    let duplicates = [];
    let answer = 0;
    
    for(let i = 0; i < nums.length; i++) {
        set.has(nums[i])? duplicates.push(nums[i]): set.add(nums[i])
    }
    
    while(duplicates.length) {
        let node = duplicates.shift()
        set.has(node + 1)? duplicates.push(node + 1): set.add(node + 1)
        answer++
    }
    
    return answer;
};
```
### 유사 문제
---

<br>

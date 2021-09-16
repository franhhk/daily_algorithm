1334 : Rotate Array
===
### Company
`Microsoft`, `Bloomberg`, `Amazon`

### Tags
`Array`

### 문제 설명
---
#### Description
Given an array, rotate the array to the right by k steps, where k is non-negative.

#### Example
Example 1:
```
Input: [1,2,3,4,5,6,7], k = 3
Output: [5,6,7,1,2,3,4]
Explanation:
rotate 1 steps to the right: [7,1,2,3,4,5,6]
rotate 2 steps to the right: [6,7,1,2,3,4,5]
rotate 3 steps to the right: [5,6,7,1,2,3,4]
```
Example 2:
```
Input: [-1,-100,3,99], k = 2
Output: [3,99,-1,-100]
Explanation: 
rotate 1 steps to the right: [99,-1,-100,3]
rotate 2 steps to the right: [3,99,-1,-100]
```
#### Challenge
1.Try to come up as many solutions as you can, there are at least 3 different ways to solve this problem. ✅

2.Could you do it in-place with O(1) extra space? ✅
<br>

### 나의 풀이
---
<br>

```js
//풀이(1)
export class Solution {

  /**
   * rotate
   *
   * @param nums: an array
   * @param k: an integer
   * @return: rotate the array to the right by k steps
   */
  rotate(nums, k) {
    let steps = k % nums.length;
    return [...nums.slice(nums.length - steps), ...nums.slice(0, nums.length-steps)]
  }

}
```
- 위의 풀이로 깔끔하게 통과했지만 재귀적으로도 풀어보고 싶었다.
```
//풀이(2)
export class Solution {

  /**
   * rotate
   *
   * @param nums: an array
   * @param k: an integer
   * @return: rotate the array to the right by k steps
   */
  rotate(nums, k) {
    if(k ===0) return nums;

    let answer = new Solution();
    return answer.rotate([nums.pop(), ...nums], k-1);
    
    // 또는
    //function rec(arr, n) {
    //    if(n ===0) return arr;
    //    
    //    return rec([arr.pop(), ...arr], n-1);
    //}
    //return rec(nums, k)
  }

}
```
- 풀리긴 하지만 확실히 메모리를 많이 잡아먹는다 (`150 ms` time cost | `41.72 MB` memory cost)
<br>

### Reference Code
---
<br>

### Record
---
풀이 (1)
- `101 ms` time cost
- `9.71 MB` memory cost
- Your submission beats `100.00%` Submissions
- `easy`

<br>

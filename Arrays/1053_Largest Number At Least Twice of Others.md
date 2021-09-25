1053 · Largest Number At Least Twice of Others
===
### Company
`Google`

### Tags
`Simulation`

### 문제 설명
---
#### Description
In a given integer array nums, there is always exactly one largest element.

Find whether the largest element in the array is at least twice as much as every other number in the array.

If it is, return the index of the largest element, otherwise return -1.

nums will have a length in the range [1, 50].
Every nums[i] will be an integer in the range [0, 99].

#### Example
Example 1:
```
Input: nums = [3, 6, 1, 0]
Output: 1
Explanation: 6 is the largest integer, and for every other number in the array x,
6 is more than twice as big as x.  The index of value 6 is 1, so we return 1.
```
Example 2:
```
Input: nums = [1, 2, 3, 4]
Output: -1
Explanation: 4 isn't at least as big as twice the value of 3, so we return -1.
```
<br>

### 나의 풀이
---
<br>

```js
export class Solution {

  /**
   * dominantIndex
   *
   * @param nums: a integer array
   * @return: the index of the largest element
   */
  dominantIndex(nums) {
    let max = Math.max(...nums)
    let answer;

    for(let i=0; i < nums.length; i++) {
        if(nums[i] === max) answer = i
        else if(nums[i] * 2 > max) return -1
    }

    return answer;
  }

}
```
<br>

### Reference Code
---

### Records
---
- `101 ms` time cost
- `8.91 MB` memory cost
- Your submission beats `100.00 %` Submissions
<br>

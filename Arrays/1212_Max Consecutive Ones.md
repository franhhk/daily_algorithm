1212 · Max Consecutive Ones
===
### Company
`Google`

### Tags
`Enumerate`,
`String`,
`Array`

### 문제 설명
---
#### Description
Given a binary array, find the maximum number of consecutive 1s in this array.

The input array will only contain 0 and 1.
The length of input array is a positive integer and will not exceed 10,000

#### Example
Example 1:
```
Input: [1,1,0,1,1,1]
Output: 3
Explanation: The first two digits or the last three digits are consecutive 1s.
    The maximum number of consecutive 1s is 3.
```
Example 2:
```
Input: [1]
Output: 1
```
<br>

### 나의 풀이
---
<br>

```js
export class Solution {

  /**
   * findMaxConsecutiveOnes
   *
   * @param nums: a binary array
   * @return:  the maximum number of consecutive 1s
   */
  findMaxConsecutiveOnes(nums) {
    let answer = 0;
    let candi = 0;
    
    for(let el of nums) {
        if(el === 1) candi++;
        else {
            answer = Math.max(candi, answer);
            candi = 0;
        }
    }
    
    return Math.max(candi, answer);
  }

}
```
<br>

### Reference Code
---

### Records
---
- `101 ms` time cost
- `9.47 MB` memory cost
- Your submission beats `100.00 %` Submissions
<br>

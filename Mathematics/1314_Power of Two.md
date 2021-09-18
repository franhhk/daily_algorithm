1314 · Power of Two
===
### Company
`Google`

### Tags
`Mathematics`, `Binary`

### 문제 설명
---
#### Description
Given an integer, write a function to determine if it is a power of two.

#### Example
Example 1:
```
Input: n = 3
Output: false
```

<br>

### 나의 풀이
---
```js
export class Solution {

  /**
   * isPowerOfTwo
   *
   * @param n: an integer
   * @return: if n is a power of two
   */
  isPowerOfTwo(n) {
    let sol = new Solution()
    if(n === 1) return true;

    if(n % 2 || n < 1) {
        return false;
    } else {
        return sol.isPowerOfTwo(n/2)
    }
  }

}
```
<br>

### Reference Code
---

<br>

### Record
---
- `101 ms` time cost
- `9.14 MB` memory cost
- Your submission beats `100.00 %` Submissions
- `easy`

<br>

1294 · Power of Three
===
### Company
`Google`

### Tags
`Mathematics`

### 문제 설명
---
#### Description
Given an integer, write a function to determine if it is a power of three.

#### Example
Example1
```
Input: n = 0
Output: False
```
Example2
```
Input: n = 9
Output: True
```
#### Challenge
Could you do it without using any loop / recursion?

<br>

### 나의 풀이
---
- The solution for `Power of Two` could be used for this problem
- Thus I decided to accept the challenge and solve it without using any loop / recursion.
- First, I thought of using log. (ex) `n = 3^i => log(n) = log(3) * i`
```js
// solution (1)
export class Solution {

  /**
   * isPowerOfThree
   *
   * @param n: an integer
   * @return: if n is a power of three
   */
  isPowerOfThree(n) {
    let i = Math.log(n) / Math.log(3)
    return +i.toFixed(10) === parseInt(i)

  }
}
```
- Second, I got a hint whilst browsing other people's codes.
- Hint: 3^19 = 1162261467 is the largest power of 3 number fits in a 32 bit integer.
```js
// solution (2)
export class Solution {

  /**
   * isPowerOfThree
   *
   * @param n: an integer
   * @return: if n is a power of three
   */
  isPowerOfThree(n) {
    return n > 0 && (Math.pow(3, 19) % n === 0)
  }
}
```
- Time Complexity : O(1), space complexity: O(1)
<br>

### Reference Code
---
<br>

### Record
---
solution (1)
- `101 ms` time cost
- `9.46 MB` memory cost
- Your submission beats `100.00 %` Submissions

solution (2)
- `101 ms` time cost
- `9.25 MB` memory cost
- Your submission beats `100.00 %` Submissions

`easy`

<br>

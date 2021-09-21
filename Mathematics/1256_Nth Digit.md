1256 · Nth Digit
===
### Company
`Google`

### Tags
`Mathematics`

### 문제 설명
---
#### Description
Find the nth digit of the infinite integer sequence 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, ...

n is positive and will fit within the range of a 32-bit signed integer (n < 2^31).

#### Example
Example 1:
```
Input：3
Output：3
```
Example 2:
```
Input：11
Output：0
Explanation：The 11th digit of the sequence 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, ... is a 0, which is part of the number 10.
```

<br>

### 나의 풀이
---
```js
// Solution (1)
export class Solution {

  /**
   * addDigits
   *
   * @param num: a non-negative integer
   * @return: one digit
   */
  addDigits(num) {
    num = '' + num
    
    if(num.length === 1) return +num;

    let sum = num.split('').reduce((a,c) => a + Number(c), 0)
    let solution = new Solution();
    return solution.addDigits(sum)
  }

}
```
- This time I accepted the challenge and wrote the code with time complexity of O(1).
- Besides 0, there are only 1~9 digits you could actually use. So anything beyond those numbers, it will circulate within those nine numbers. This is where I got the idea of finding the remains after dividing the given number by 9.
- The code looks much more simple, but the time / memory cost weren't as ideal as I expected.
```js
// Solution (2)
export class Solution {

  /**
   * addDigits
   *
   * @param num: a non-negative integer
   * @return: one digit
   */
  addDigits(num) {
    return num % 9 === 0 ? (num === 0? 0 : 9) : num % 9;
  }

}
```
<br>

### Reference Code
---
<br>

### Record
---
Solution (1)
- `101 ms` time cost
- `8.83 MB` memory cost
- Your submission beats `100.00 %` Submissions

Solution (2)
- `123 ms` time cost
- `9.10 MB` memory cost
- Your submission beats `94.29 %` Submissions

Level
- `easy`

<br>

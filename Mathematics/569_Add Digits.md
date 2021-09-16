569 : Add Digits
===
### Company
`Microsoft`, `Adobe`

### Tags
`Mathematics`, `Simulation`

### 문제 설명
---
#### Description
Given a non-negative integer num, repeatedly add all its digits until the result has only one digit.

#### Example
Example 1:
```
Input:
num=38
Output:
2
Explanation:
The process is like: 3 + 8 = 11, 1 + 1 = 2. Since 2 has only one digit, return 2.
```
Example 2:
```
Input:
num=9
Output:
9
Explanation:
9<10,return 9.
```
#### Challenge
Could you do it without any loop/recursion in O(1) runtime?

<br>

### 나의 풀이
---
- This is how you get your soul number! yeah, fun!
- As a recusion-lover, I first used recursion to solve the problem. Of course, you can use a loop.
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

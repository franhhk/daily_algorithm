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
- As for the first approach, the logic worked but it caused a runtime error
- `Your code cost too much memory than we expected. Check your space complexity.`
```js
// Solution (1)
export class Solution {

  /**
   * findNthDigit
   *
   * @param n: a positive integer
   * @return: the nth digit of the infinite integer sequence
   */
  findNthDigit(n) {
     let num = '';
     let i = 1;

     while(num.length < n) {
         num += i;
         i++;
     }

     return +num[n-1];
  }

}
```
- 
```js
// Solution (2)

```
<br>

### Reference Code
---
```js
const findNthDigit = (num = 1) => {
   let start = 1;
   let len = 1;
   let count = 9;
   while(num > len * count) {
      num -= len * count;
      len++; count *= 10;
      start *= 10;
   };
   start += Math.floor((num-1)/len);
   let s = String(start);
   return Number(s[(num-1) % len]);
};
```
- `101 ms` time cost
- `9.20 MB` memory cost
- Your submission beats `100.00 %` Submissions

<br>

### Record
---
Level
- `easy`

<br>

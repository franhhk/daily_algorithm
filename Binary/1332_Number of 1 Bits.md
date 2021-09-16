1332 : Number of 1 Bits
===
### Company
`Microsoft`, `Apple`

### Tags
`Binary`

### 문제 설명
---
#### Description
Write a function that takes an unsigned integer and returns the number of ’1' bits the corresponding binary number has (also known as the Hamming weight).

#### Example
Example 1:
```
Input：n = 11
Output：3
Explanation：11(10) = 1011(2), so return 3
```
Example 2:
```
Input：n = 7
Output：3
Explanation：7(10) = 111(2), so return 3
```

<br>

### 나의 풀이
---
- 2진수 변환 문제를 풀어본 적이 있어서 빠르게 풀었다

```js
export class Solution {

  /**
   * hammingWeight
   *
   * @param n: an unsigned integer
   * @return: the number of ’1' bits
   */
  hammingWeight(n) {
    let answer = ''
    while(n > 0) {
        answer = n % 2 + answer;
        n = parseInt(n/2)
    }
    return answer.split('').reduce((a,c) => a + Number(c), 0)
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
- `8.81 MB` memory cost
- Your submission beats `100.00%` Submissions
- `easy`

<br>

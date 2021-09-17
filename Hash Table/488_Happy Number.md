488 · Happy Number
===
### Company
`Uber`, `Twitter`, `Airbnb`

### Tags
`Simulation`

### 문제 설명
---
#### Description
Write an algorithm to determine if a number is happy.

A happy number is a number defined by the following process: Starting with any positive integer, replace the number by the sum of the squares of its digits, and repeat the process until the number equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1. Those numbers for which this process ends in 1 are happy numbers.


#### Example
Example 1:
```
Input:19
Output:true
Explanation:

19 is a happy number

    1^2 + 9^2 = 82
    8^2 + 2^2 = 68
    6^2 + 8^2 = 100
    1^2 + 0^2 + 0^2 = 1
```
Example 2:
```
Input:5
Output:false
Explanation:

5 is not a happy number

25->29->85->89->145->42->20->4->16->37->58->89
89 appears again.
```

<br>

### 나의 풀이
---
```js
export class Solution {

  /**
   * isHappy
   *
   * @param n: An integer
   * @return: true if this is a happy number or false
   */
  isHappy(n) {
    let hash = []

    while(!hash[n]) {
        hash[n] = 1

        n = String(n)
            .split('')
            .reduce((a,c) => {
                a += Math.pow(+c, 2)
                return a
            }, 0)
        
        if(n === 1) return true
    }

    return false;
  }

}
```
<br>

### 다른 사람 풀이
---
<br>

### Record
---
- `102 ms` time cost
- `9.00 MB` memory cost
- Your submission beats `98.65%` Submissions
- `easy`

<br>

1880 : Largest Number X Which Occurs X Times
===
### Company
`Microsoft`

### Tags
`Hash Table`, `Enumerate`

### 문제 설명
---
#### Description
Given an array A consisting of N integers, you should return the biggest value X, which occurs in A exactly X times. If there is no such value, you should return 0.

N is an integer within the range [1..100,000];
each element of array A is an integer within the range [1..1,000,000,000].

#### Example
Example 1:
```
Input: 
[3, 8, 2, 3, 3, 2]
Output: 
3
Explanation: 
The value 2 occurs exactly two times and the value 3 occurs exactly three times. Meanwhile, the maximum of 2 and 3 is 3 so the answer is 3.
```
Example 2:
```
Input: 
[3, 1, 4, 1, 5]
Output: 
0
Explanation: 
There is no value which meets the task conditions so the answer is 0.
```

<br>

### 나의 풀이
---
풀면서 놓쳤던 부분:
- max = 0으로 초기화함으로써 조건에 부합하는 값이 없을 경우 0을 리턴한다
- 객체의 key는 문자열 타입이므로 숫자로 바꿔서 반환해줘야 한다
- max 와 candi를 비교할 때도 string 타입이 아닌 숫자 타입인 상태에서 비교를 해야한다

<br>

```js
export class Solution {

  /**
   * findX
   *
   * @param arr: an array of integers
   * @return: return the biggest value X, which occurs in A exactly X times.
   */
  findX(arr) {
    let record = {}

    for(let el of arr) {
        record[el] = record[el]? record[el] + 1: 1;
    }

    let max = 0;
    for(let key in record) {
        let candi;
        if(record[key] === +key) candi = key;
        if(+max < +candi) max = candi;
    }

    return +max;
  }
}
```
<br>

### Reference Code
---
<br>

### Record
---
- `487 ms` time cost
- `33.85 MB` memory cost

<br>

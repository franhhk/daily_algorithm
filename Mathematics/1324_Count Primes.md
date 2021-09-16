1324 : Count Primes
===
### Company
`Microsoft`, `Amazon`

### Tags
`Mathematics`

### 문제 설명
---
#### Description
Count the number of prime numbers less than a non-negative number, n.

#### Example
Example 1:
```
Input: n = 2
Output: 0
```
Example 2:
```
Input: n = 4
Output: 2
Explanation：2, 3 are prime number
```

<br>

### 나의 풀이
---
- 주석처리된 방법으로 풀면 time limit exceeded 에러가 뜬다. (`1106 ms` time cost | `9.32 MB` memory cost)
- 나누는 수의 범위를 제곱근을 이용해 좁히는 이유는, 수를 나눌 때 몫과 나누는 수, 둘 중 하나는 반드시 N의 제곱근 이하이기 때문이다.
```js
export class Solution {

  /**
   * countPrimes
   *
   * @param n: a integer
   * @return: return a integer
   */
  countPrimes(n) {
    let answer = 0;
    
    if(n > 2) answer++
    
    for(let i = 3; i < n; i = i + 2) {
        let isPrime = true;
        for(let j = 3; j <= Math.sqrt(i); j = j+2) {
        //for(let j = 3; j < i; j = j+2) {
            if(i % j === 0) {
                isPrime = false;
                break;
            }
        }
        if(isPrime) answer++;
    }

    return answer;
  }

}
```
<br>

### Reference Code
---
- `223 ms` time cost | `77.07 MB` memory cost | Your submission beats `96.67 %` Submissions
- 모든 소수 후보에 대해 반복문을 돌리지 않아서 소요되는 시간 소요가 훨씬 줄어든다.
```js
var countPrimes = function(n) {
    let flagArray = [],
        result = 0;
    for(let i = 2; i < n; i++){
        if(flagArray[i] === undefined){
            // is Primes
            flagArray[i] = 1;
            result++;
            // rm it's multiples
            let j = 2;
            while(i * j < n){
                flagArray[i * j] = 0;
                j++;
            }
        }
    }
    return result;
};
```
<br>

### Record
---
- `506 ms` time cost
- `9.43 MB` memory cost
- Your submission beats `60.00 %` Submissions
- `easy`

<br>

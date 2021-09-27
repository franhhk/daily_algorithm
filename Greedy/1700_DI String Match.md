1700 · DI String Match
===
### Company
`Google`, `Amazon`

### Tags
`Greedy`, `Mathematics`

### 문제 설명
---
#### Description
Given a string S that only contains "I" (increase) or "D" (decrease), let N = S.length.

Return any permutation A of [0, 1, ..., N] such that for all i = 0, ..., N-1:

If S[i] == "I", then A[i] < A[i+1]
If S[i] == "D", then A[i] > A[i+1]
1 <= S.length <= 10000
S only contains characters "I" or "D".
#### Example
Example 1:
```
Input："IDID"
Output：[0,4,1,3,2]
Explanation：according to "IDID",0<4,4>1,1<3,3>2.
```
Example 2:
```
Input："III"
Output：[0,1,2,3]
Explanation：according to "III",0<1,1<2,2<3.
```

<br>

### 나의 풀이
---
- 푸는데 시간이 오래 걸렸다. 잘 기억해둬야겠다.
```js
export class Solution {

  /**
   * diStringMatch
   *
   * @param S: 
   * @return: 
   */
  diStringMatch(S) {
    let max = S.length;
    let min = 0
    let answer = []

    for(let i = 0; i < S.length; i++) {
        if(S[i] === 'I') {
            answer.push(min)
            min++
        } else {
            answer.push(max)
            max--
        }

        if(i === S.length-1) {
            S[i] === 'I'? answer.push(max): answer.push(min);
        }
    }
    return answer;
  }
}
```
- Second trial on [LeetCode](https://leetcode.com/problems/di-string-match/)
- Realized that it doesn't matter if I push max or min in the end.
- Thus wrote a cleaner code without previous lines 62 - 64.
```js
/**
 * @param {string} s
 * @return {number[]}
 */
var diStringMatch = function(s) {
    let min = 0;
    let max = s.length;
    let answer = [];
    
    for(let el of s) {
        if(el === 'I') {
            answer.push(min);
            min++;
        } else {
            answer.push(max);
            max--;
        }
    }
    
    return [...answer, min] //or max, it doesn't matter
};
```
- Runtime: 96 ms, faster than 68.13% of JavaScript online submissions for DI String Match.
- Memory Usage: 43 MB, less than 32.42% of JavaScript online submissions for DI String
<br>

### 다른 사람 풀이
---

<br>

### Record
---
- 사이트 테스트 상 오류로 확인 불가
- `easy`

<br>

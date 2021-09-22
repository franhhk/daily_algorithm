1227 · Repeated Substring Pattern
===
### Company
`Google`, `Amazon`

### Tags
`String`

### 문제 설명
---
#### Description
Given a non-empty string check if it can be constructed by taking a substring of it and appending multiple copies of the substring together. You may assume the given string consists of lowercase English letters only and its length will not exceed 10000.

#### Example
Example 1:
```
Input: "abab"

Output: True

Explanation: It's the substring "ab" twice.
```
Example 2:
```
Input: "aba"

Output: False
```
Example 3:
```
Input: "abcabcabcabc"

Output: True

Explanation: It's the substring "abc" four times. (And the substring "abcabc" twice.)
```
<br>

### 나의 풀이
---
<br>

```js
export class Solution {

  /**
   * repeatedSubstringPattern
   *
   * @param s: a string
   * @return: return a boolean
   */
  repeatedSubstringPattern(s) {
    // 길이가 홀수면 한 가지 알파벳으로만 이루어져 있어야 함
    // 짝수일 경우 가운데로 나눴을 때 양 옆이 같아야 한다

    if(s.length % 2) {
        for(let i = 0 ; i < s.length - 1; i++) {
            if(s[i] !== s[i+1]) return false;
        }
        return true;
    } else {
        let len = s.length/2
        for(let i = 0; i < len; i++) {
            if(s[i] !== s[i+len]) return false;
        }
        return true;
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
- `9.87 MB` memory cost
- Your submission beats `100.00%` Submissions

`easy`

<br>

1540 · Can Convert
===
### Company
`Google`

### Tags
 `Same Direction Two Pointers`, `Two Pointers`, `String`

### 문제 설명
---
#### Description
Given two string S and T, determine if S can be changed to T by deleting some letters (including 0 letter)

#### Example
Example 1
```
Input: S = "lintcode" and T = "lint"
Output: true
```
Example 2
```
Input: S = "lintcode" and T = "ide"
Output: true
```
Example 3
```
Input: S = "adda" and T = "aad"
Output: false
Explanation: You can not change "adda" to "aad" by deleting one 'd'.
```
<br>

### 나의 풀이
---
- s, t가 null로 들어오는 테스트 케이스가 있었다. 이런 예외 사항에 대해 미리미리 생각하는 습관을 들이자!
<br>

```js
export class Solution {

  /**
   * canConvert
   *
   * @param s: string S
   * @param t: string T
   * @return: whether S can convert to T
   */
  canConvert(s, t) {
    if(!s || !t) return false;

    s = s.split('')
    for(let i=0; i < s.length; i++) {
        if(!t.includes(s[i])) {
            s.splice(i, 1)
            i--
        }
    }

    return s.join('') === t;
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
- `8.98 MB` memory cost
- Your submission beats `100.00%` Submissions
- `easy`

<br>

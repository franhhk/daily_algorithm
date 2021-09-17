916 · Palindrome Permutation
===
### Company
`Uber`, `Google`

### Tags
`Hash Table`, `String`, `Enumerate`

### 문제 설명
---
#### Description
Given a string, determine if a permutation of the string could form a palindrome.

#### Example
Example 1:
```
Input: s = "code"
Output: False
Explanation: 
No solution
```
Example 2:
```
Input: s = "aab"
Output: True
Explanation: 
"aab" --> "aba"
```

Example3
 ```
Input: s = "carerac"
Output: True
Explanation: 
"carerac" --> "carerac"
```
<br>

### 나의 풀이
---
- 일일이 palindrome을 만들어보며 확인할 뻔했다. 휴.
- palindrome을 만드려면 가운데 글자를 중심으로 양쪽에 같은 알파벳이 하나씩 있어야 한다는 것을 이용했다.

```js
export class Solution {

  /**
   * canPermutePalindrome
   *
   * @param s: the given string
   * @return: if a permutation of the string could form a palindrome
   */
  canPermutePalindrome(s) {
      let hash = s.split('').reduce((a,c) => {
          a[c] = a[c]? a[c] + 1: 1
          return a
      }, {})

      let skip = s.length % 2? 1: 0;

      for(let key in hash) {
          if(hash[key] % 2) {
              if(skip) {
                  skip--
              } else {
                  return false
              }
          }
      }

      return true;
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
- `9.25 MB` memory cost
- Your submission beats `100.00%` Submissions
- `easy`

<br>

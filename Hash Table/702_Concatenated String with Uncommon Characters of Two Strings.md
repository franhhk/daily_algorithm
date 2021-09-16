702 : Concatenated String with Uncommon Characters of Two Strings
===
### Company
`Microsoft`

### Tags
`Hash Table`, `String`

### 문제 설명
---
#### Description
Two strings are given and you have to modify 1st string such that all the common characters of the 2nd strings have to be removed and the uncommon characters of the 2nd string have to be concatenated with uncommon characters of the 1st string.
#### Example
Example 1:
```
Input : s1 = "aacdb", s2 = "gafd"
Output : "cbgf"
```
Example 2:
```
Input : s1 = "abcs", s2 = "cxzca"
Output : "bsxz"
```

<br>

### 나의 풀이
---
- 푸는 시간을 줄여야 한다
```js
export class Solution {

  /**
   * concatenetedString
   *
   * @param s1: the 1st string
   * @param s2: the 2nd string
   * @return: uncommon characters of given strings
   */
  concatenetedString(s1, s2) {
    let hash = new Map();

    for(let el of s1) {
        hash.set(el, 1)
    }
    for(let el of s2) {
        if(hash.get(el) === undefined) hash.set(el, 2);
        if(hash.get(el) === 1) hash.set(el, 3);
    }

    let answer = ''

    //Map is directly iterable
    for(let el of s1) {
        if(hash.get(el) === 1) answer += el
    }

    for(let el of s2) {
        if(hash.get(el) === 2) answer += el
    }

    return answer;
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
- `8.80 MB` memory cost
- Your submission beats `90.91%` Submissions
- `easy`

<br>

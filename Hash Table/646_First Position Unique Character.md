646 : First Position Unique Character
===
### Company
`Microsoft`, `Amazon`, `Bloomberg`

### Tags
`Hash Table`, `String`

### 문제 설명
---
#### Description
Given a string, find the first non-repeating character in it and return it's index. If it doesn't exist, return -1.

#### Example
Example 1:
```
Input : s = "lintcode"
Output : 0
```
Example 2:
```
Input : s = "lovelintcode"
Output : 2
```

<br>

### 나의 풀이
---
- 이제까지 푼 문제중에 가장 빨리 푼 것 같다.
```js
export class Solution {

  /**
   * firstUniqChar
   *
   * @param s: a string
   * @return: it's index
   */
  firstUniqChar(s) {
    let hash = s.split('').reduce((a,c) => {
        a[c] = a[c]? 2: 1
        return a
    }, {})

    for(let key in hash) {
        if(hash[key] === 1) return s.indexOf(key)
    }

    return -1;
  }

}
```
<br>

### 다른 사람 풀이
---
<br>

### Record
---
- `101 ms` time cost
- `9.29 MB` memory cost
- Your submission beats `100.00%` Submissions
- `easy`

<br>

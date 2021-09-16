209 : First Unique Character in a String
===
### Company
`Microsoft`, `Amazon`, `Bloomberg`, `Google`

### Tags
`Hash Table`, `String`

### 문제 설명
---
#### Description
Given a string and find the first unique character in a given string. You can assume that there is at least one unique character in the string.

#### Example
Example 1:
```
Input: "abaccdeff"
Output:  'b'

Explanation:
There is only one 'b' and it is the first one.
```
Example 2:
```
Input: "aabccd"
Output:  'b'
	
Explanation:
'b' is the first one.
```

<br>

### 나의 풀이
---
- 이제까지 푼 문제중에 가장 빨리 푼 것 같다22
```js
export class Solution {

  /**
   * firstUniqChar
   *
   * @param str: str: the given string
   * @return: char: the first unique character in a given string
   */
  firstUniqChar(str) {
      let hash = str.split('').reduce((a,c) => {
          a[c] = a[c]? 2: 1;
          return a
      }, {});

      for(let el of str) {
          if(hash[el] === 1) return el;
      }
  }

}
```
<br>

### 다른 사람 풀이
---
<br>

### Record
---
- `122 ms` time cost
- `10.68 MB` memory cost
- Your submission beats `97.91%` Submissions
- `easy`

<br>

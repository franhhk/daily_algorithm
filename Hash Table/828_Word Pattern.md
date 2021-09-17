828 : Word Pattern
===
### Company
`Uber`

### Tags
`Hash Table`, `String`, `Enumerate`

### 문제 설명
---
#### Description
Given a pattern and a string str, find if str follows the same pattern.
Here follow means a full match, such that there is a bijection between a letter in pattern and a non-empty word in str.

You may assume pattern contains only lowercase letters, and str contains lowercase letters separated by a single space.

#### Example
Example 1:
```
Input:  pattern = "abba" and str = "dog cat cat dog"
Output: true
Explanation:
The pattern of str is abba
```
Example 2:
```
Input:  pattern = "abba" and str = "dog cat cat fish"
Output: false
Explanation:
The pattern of str is abbc
```
Example 3:
```
Input:  pattern = "aaaa" and str = "dog cat cat dog"
Output: false
Explanation:
The pattern of str is abba
```

<br>

### 나의 풀이
---
```js
export class Solution {

  /**
   * wordPattern
   *
   * @param pattern: a string, denote pattern string
   * @param teststr: a string, denote matching string
   * @return: an boolean, denote whether the pattern string and the matching string match or not
   */
  wordPattern(pattern, teststr) {
    let hash = {}

    teststr = teststr.split(' ')
    pattern = pattern.split('')

    if(pattern.length !== teststr.length) return false;

    while(pattern.length) {
        let p = pattern.shift();
        let s = teststr.shift();

        if(!hash[p] && !hash[s]) {
            hash[p] = s
            hash[s] = p
        } else if(hash[p] !== s){
             return false
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
- `101 ms` time cost
- `8.70 MB` memory cost
- Your submission beats `100.00%` Submissions
- `easy`

<br>

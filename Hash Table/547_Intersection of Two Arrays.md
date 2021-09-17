547 · Intersection of Two Arrays
===
### Company
`Facebook`, `Uber`

### Tags
`Hash Table`, `Same Direction Two Pointers`, `Two Pointers`

### 문제 설명
---
#### Description
Given two arrays, write a function to compute their intersection.

Each element in the result must be unique.

#### Example
Example 1:
```
Input: nums1 = [1, 2, 2, 1], nums2 = [2, 2], 
Output: [2].
```
Example 2:
```
Input: nums1 = [1, 2], nums2 = [2], 
Output: [2].
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
- `easy`

<br>

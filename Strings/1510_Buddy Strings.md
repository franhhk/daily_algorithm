1510 · Buddy Strings
===
### Company
`Google`

### Tags
 `String`

### 문제 설명
---
#### Description
Given two strings A and B of lowercase letters, return true if and only if we can swap two letters in A so that the result equals B.Otherwise, return false.

1.0 <= A.length <= 20000
2.0 <= A.length <= 20000
3.A and B consist only of lowercase letters.

#### Example
Example 1:
```
Input: A = "ab", B = "ba"
Output: true
```
Example 2:
```
Input: A = "ab", B = "ab"
Output: false
```
Example 3:
```
Input: A = "aa", B = "aa"
Output: true
```
Example 4:
```
Input: A = "aaaaaaabc", B = "aaaaaaacb"
Output: true
```
Example 5:
```
Input: A = "", B = "aa"
Output: false
```
<br>

### 나의 풀이
---
<br>

```js
export class Solution {

  /**
   * buddyStrings
   *
   * @param A: string A
   * @param B: string B
   * @return: bool
   */
  buddyStrings(A, B) {
    if(A.length !== B.length || A.length < 2 || B.length < 2) return false;

    // aaabaabc aaacaabb
    let checkAB = {}
    let checkAA = {}

    for(let i = 0; i < A.length; i++) {
        if(A[i] !== B[i]) {
            checkAB[A[i]] = i
        } else {
            checkAA[A[i]] = checkAA[A[i]]? checkAA[A[i]] + 1: 1;
        }
    }

    let keys = Object.keys(checkAB);
    if(keys.length === 0) {
        for(let key in checkAA) {
            return checkAA[key] > 1 ;
        }
    } else {
        if(keys.length === 2) {
            let [first, second] = keys
            let [firstIdx, secondIdx] = [checkAB[first], checkAB[second]]

            if(B[secondIdx] !== first || B[firstIdx] !== second) return false
            else return true
        } else {
            return false
        }
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
- `122 ms` time cost
- `11.21 MB` memory cost
- Your submission beats `95.45%` Submissions
- `easy`

<br>

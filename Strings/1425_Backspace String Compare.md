1425 · Backspace String Compare
===
### Company
`Google`

### Tags
`String`

### 문제 설명
---
#### Description
Given two strings S and T, return if they are equal when both are typed into empty text editors. # means a backspace character.

1 <= S.length <= 200
1 <= T.length <= 200
S and T only contain lowercase letters and '#' characters.

#### Example
Example 1:
```
Input: S = "ab#c", T = "ad#c"
Output: true
Explanation: Both S and T become "ac".
```
Example 2:
```
Input: S = "ab##", T = "c#d#"
Output: true
Explanation: Both S and T become "".
```
Example 3:
```
Input: S = "a##c", T = "#a#c"
Output: true
Explanation: Both S and T become "c".
```
Example 4:
```
Input: S = "a#c", T = "b"
Output: false
Explanation: S becomes "c" while T becomes "b".
```
#### Challenge
Can you solve it in O(N) time and O(1) space?
<br>

### 나의 풀이
---
- I used push, pop methods to effectively implement backspace.
<br>

```js
// solution(1)

export class Solution {

  /**
   * backspaceCompare
   *
   * @param S: string S
   * @param T: string T
   * @return: Backspace String Compare
   */
  backspaceCompare(S, T) {
    let lenS = S.length,
        lenT = T.length;

      S = S.split('');
      T = T.split('');

    for(let i=0; i < lenS; i++) {
        let node = S.shift();
        node === '#'? S.pop(): S.push(node);
    }
    for(let i=0; i < lenT; i++) {
        let node = T.shift();
        node === '#'? T.pop(): T.push(node);
    }

    return S.join('') === T.join('');
  }

}
```
- I realized I was using the same code for strings `S` and `T`, so I decided to refactor my code.
- I declared a new function which I could reuse.
```js
// solution (2)

export class Solution {

  /**
   * backspaceCompare
   *
   * @param S: string S
   * @param T: string T
   * @return: Backspace String Compare
   */
  backspaceCompare(S, T) {
    function backSpace(str) {
        let len = str.length
        str = str.split('')

        for(let i=0; i < len; i++) {
            let node = str.shift();
            node === '#'? str.pop(): str.push(node);
        }
        return str.join('')
    }

    return backSpace(S) === backSpace(T);
  }
}
```
<br>

### Reference Code
---
<br>

### Record
---
solution (1)
- `121 ms` time cost
- `8.79 MB` memory cost
- Your submission beats `88.89%` Submissions

solution (2)
- `101 ms` time cost
- `8.79 MB` memory cost
- Your submission beats `100.00%` Submissions

`easy`

<br>

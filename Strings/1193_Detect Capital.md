1193 · Detect Capital
===
### Company
`Google`

### Tags
`String`, `Simulation`

### 문제 설명
---
#### Description
Given a word, you need to judge whether the usage of capitals in it is right or not.

We define the usage of capitals in a word to be right when one of the following cases holds:

All letters in this word are capitals, like "USA".
All letters in this word are not capitals, like "lintcode".
Only the first letter in this word is capital if it has more than one letter, like "Google".
Otherwise, we define that this word doesn't use capitals in a right way.

The input will be a non-empty word consisting of uppercase and lowercase latin letters.

#### Example
Example 1:
```
Input: "USA"
Output: True
```
Example 2:
```
Input: "FlaG"
Output: False
```
<br>

### 나의 풀이
---
<br>

```js
export class Solution {

  /**
   * detectCapitalUse
   *
   * @param word: a string
   * @return: return a boolean
   */
  detectCapitalUse(word) {
    if(word.length === 1) return true;
    
    if(word[0].toLowerCase() === word[0]) {
        return word.toLowerCase() == word 
    } else {
        if(
            word.toUpperCase() === word ||
            word.slice(1).toLowerCase() === word.slice(1)
        ) return true
        else return false
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
- `8.76 MB` memory cost
- Your submission beats `100.00%` Submissions

`easy`

<br>

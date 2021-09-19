1282 · Reverse Vowels of a String
===
### Company
`Google`

### Tags
`String`, `Two Pointers`

### 문제 설명
---
#### Description
Write a function that takes a string as input and reverse only the vowels of a string.

The vowels does not include the letter "y".

#### Example
Example 1:
```
Input : s = "hello"
Output :  "holle"
```
Example 2:
```
Input : s = "lintcode"
Output : "lentcodi".
```

<br>

### 나의 풀이
---
<br>

```js
export class Solution {

  /**
   * reverseVowels
   *
   * @param s: a string
   * @return: reverse only the vowels of a string
   */
  reverseVowels(s) {
    let vowels = 'aeiou'
    let stack = []

    s = s.split('');

    for(let i = 0; i < s.length; i++) {
        if(vowels.includes(s[i].toLowerCase())) {
            stack.push(s[i])
            s[i] = null
        }
    }

    for(let i = 0; i < s.length; i++) {
        if(s[i] === null) {
            s[i] = stack.pop();
        }
    }

    return s.join('');
  }

}
```
<br>

### Reference Code
---
```js
function isVowel(c) {
        return (c == 'a' || c == 'A' || c == 'e'
                || c == 'E' || c == 'i' || c == 'I'
                || c == 'o' || c == 'O' || c == 'u'
                || c == 'U');
    }
   
    // Function to reverse order of vowels
    function reverseVowel(str1) {
        let j = 0;
        // Storing the vowels separately
        let str = str1.split('');
        let vowel = "";
        for (let i = 0; i < str.length; i++) {
            if (isVowel(str[i])) {
                j++;
                vowel += str[i];
            }
        }
   
        // Placing the vowels in the reverse
        // order in the string
        for (let i = 0; i < str.length; i++) {
            if (isVowel(str[i])) {
                str[i] = vowel[--j];
            }
        }
   
        return str.join("");
    }
```
<br>

### Record
---
- `122 ms` time cost
- `9.71 MB` memory cost
- Your submission beats `100.00%` Submissions

`easy`

<br>

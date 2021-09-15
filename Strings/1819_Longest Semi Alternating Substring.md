1819 : Longest Semi Alternating Substring
===
### Company
`Microsoft`

### Tags
 `Same Direction Two Pointers`, `Two Pointers`

### 문제 설명
---
#### Description
You are given a string S of length N containing only characters a and b. A substring (contiguous fragment) of S is called a semi-alternating substring if it does not contain three identical consecutive characters. In other words, it does not contain either aaa or bbb substrings. Note that whole S is its own substring.

Write a function, which given a string S, returns the length of the longest semi-alternating substring of S.

NN is an integer within the range [1,200\,000][1,200000];
string S consists only of the characters a and/or b.

#### Example
Example 1
```
Input: "baaabbabbb"
Output: 7
Explanation: "aabbabb" is the longest semi-alternating substring.
```
Example 2
```
Input: "babba"
Output: 5
Explanation: Whole S is semi-alternating.
```
Example 3
```
Input: "abaaaa"
Output: 4
Explanation: "abaa" is the longest semi-alternating substring.
```
<br>

### 나의 풀이
---
- easy 단계임에도 내 마음은 easy가 아니었다
- 처음엔 재귀로 풀어서 timeout error가 발생했다
- 간단한 풀이인데도 활용할만큼 익숙해지는데 시간이 걸릴 것 같다.
<br>

```js
export class Solution {

  /**
   * longestSemiAlternatingSubstring
   *
   * @param s: the string
   * @return: length of longest semi alternating substring
   */
  longestSemiAlternatingSubstring(s) {
    if(s.length < 3) {
        return s.length;
    }
    let count = 1;
    let answer = 1;

    for(let i = 1; i < s.length; i++) {
        if(s[i] === s[i-1] && s[i] === s[i+1]) {
            answer = Math.max(count + 1, answer)
            count = 1;
        } else {
            count++
        }
    }

    return Math.max(answer, count);
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
- `11.54 MB` memory cost
- Your submission beats `100.00%` Submissions
- `easy`

<br>

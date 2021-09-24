627 · Longest Palindrome
===
### Company
`Amazon`, `Google`

### Tags
`Hash Table`

### 문제 설명
---
#### Description
Given a string which consists of lowercase or uppercase letters, find the length of the longest palindromes that can be built with those letters.

This is case sensitive, for example "Aa" is not considered a palindrome here.

Assume the length of given string will not exceed 100000.

#### Example
Example 1:
```
Input : s = "abccccdd"
Output : 7
Explanation :
One longest palindrome that can be built is "dccaccd", whose length is `7`.
```

<br>

### 나의 풀이
---
```js
export class Solution {

  /**
   * longestPalindrome
   *
   * @param s: a string which consists of lowercase or uppercase letters
   * @return: the length of the longest palindromes that can be built
   */
  longestPalindrome(s) {
    let answer = 0;
    let isOdd = 0;

    let hash = s.split('').reduce((a,c) => {
        a[c] = a[c]? a[c] + 1: 1;
        return a;
    }, {});

    for(let el in hash) {
        if(hash[el] % 2 === 0) answer += hash[el];
        else {
            isOdd = 1;
            answer += hash[el] - hash[el] % 2
        }
    }

    return answer + isOdd;
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
- `9.47 MB` memory cost
- Your submission beats `100.00%` Submissions
- `easy`

<br>

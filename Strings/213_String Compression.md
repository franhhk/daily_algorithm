213 · String Compression
===
### Company
`Snapchat`, `Microsoft`, `GoDaddy`, `Expedia`,`Lyft`,`Bloomberg`,`Yelp`

### Tags
 `String`, `Simulation`

### 문제 설명
---
#### Description
Implement a method to perform basic string compression using the counts of repeated characters. For example, the string aabcccccaaa would become a2b1c5a3.

If the "compressed" string would not become smaller than the original string, your method should return the original string.

You can assume the string has only upper and lower case letters (a-z).

#### Example
Example 1
```
Input: str = "aabcccccaaa"
Output: "a2b1c5a3"
```
Example 2
```
Input: str = "aabbcc"
Output: "aabbcc"
```

<br>

### 나의 풀이
---
<br>

```js
export class Solution {

  /**
   * compress
   *
   * @param originalString: a string
   * @return: a compressed string
   */
  compress(originalString) {
    let answer = ''

    if(originalString.length === 0) return answer; 

    let letter = originalString[0],
        count = 0;

    for(let el of originalString) {
        if(el === letter) {
            count++
        } else {
            answer += letter + count
            letter = el
            count = 1
        }
    }

    answer += letter + count;
    return answer.length >= originalString.length? originalString: answer;
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
- `9.23 MB` memory cost
- Your submission beats `79.67%` Submissions
- `easy`

<br>

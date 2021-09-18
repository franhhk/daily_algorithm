1438 · Positions of Large Groups
===
### Company
`Google`

### Tags
`String`

### 문제 설명
---
#### Description
In a string S of lowercase letters, these letters form consecutive groups of the same character.

For example, a string like S = "abbxxxxzyy" has the groups "a", "bb", "xxxx", "z" and "yy".

Call a group large if it has 3 or more characters. We would like the starting and ending positions of every large group.

The final answer should be in lexicographic order.

1 <= S.length <= 1000

#### Example
Example 1
```
Input: "abbxxxxzzy"
Output: [[3,6]]
Explanation: "xxxx" is the single large group with starting  3 and ending positions 6.
```
Example 2
```
Input: "abc"
Output: []
Explanation: We have "a","b" and "c" but no large group.
```
Example 3
```
Input: "abcdddeeeeaabbbcd"
Output: [[3,5],[6,9],[12,14]]
```
<br>

### 나의 풀이
---
- s, t가 null로 들어오는 테스트 케이스가 있었다. 이런 예외 사항에 대해 미리미리 생각하는 습관을 들이자!
<br>

```js
export class Solution {

  /**
   * largeGroupPositions
   *
   * @param S: a string
   * @return: the starting and ending positions of every large group
   */
  largeGroupPositions(S) {
    let letter,
        group = [];
    let answer = []
    
    for(let i=0; i < S.length; i++) {
        if(letter === S[i]) {
            if(i - group[0] >= 2 && S[i+1] !== letter) {
                group[1] = i
                answer.push(group)
                group = []
            }
        } else if(letter === undefined || letter !== S[i]) {
            letter = S[i]
            group = []
            group[0] = i
        } 
    }

    return answer;
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
- `9.05 MB` memory cost
- Your submission beats `100.00%` Submissions
- `easy`

<br>

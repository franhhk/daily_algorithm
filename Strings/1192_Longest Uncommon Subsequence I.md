1192 · Longest Uncommon Subsequence I
===
### Company
`Google`

### Tags
`String`

### 문제 설명
---
#### Description
Given a group of two strings, you need to find the longest uncommon subsequence of this group of two strings. The longest uncommon subsequence is defined as the longest subsequence of one of these strings and this subsequence should not be any subsequence of the other strings.

A subsequence is a sequence that can be derived from one sequence by deleting some characters without changing the order of the remaining elements. Trivially, any string is a subsequence of itself and an empty string is a subsequence of any string.

The input will be two strings, and the output needs to be the length of the longest uncommon subsequence. If the longest uncommon subsequence doesn't exist, return -1.

Both strings' lengths will not exceed 100.
Only letters from a ~ z will appear in input strings.

#### Example
Example 1:
```
Input: "aba", "cdc"
Output: 3
Explanation: The longest uncommon subsequence is "aba" (or "cdc"), 
because "aba" is a subsequence of "aba", but not a subsequence of any other strings in the group of two strings.
```
<br>

### 나의 풀이
---
- Used a recursive solution
<br>

```js
export class Solution {

  /**
   * findLUSlength
   *
   * @param a: a string
   * @param b: a string
   * @return: return a integer
   */
  findLUSlength(a, b) {
    if(a === b) return -1;

    function isSub(str1, str2) {
        let count = 0;
        let j = 0;
        
        for(let i=0; i < str1.length; i++) {
            while(j < str2.length) {
                if(str1[i] === str2[j]) {
                    count++;
                    break;
                }
                j++;
            }
        }

        return count === str1.length;
    }

    if(!isSub(a,b) && !isSub(a,b)) return Math.max(a.length, b.length);
    else if(!isSub(a, b)) return a.length;
    else if(!isSub(b, a)) return b.length;
    else return -1;
  }

}
```
<br>

### Reference Code
---
- Assumably due to the triple for loop, the reference code (from [GeekforGeeks](https://www.geeksforgeeks.org/longest-uncommon-subsequence/)) took too much time to process, thus causing a runtime error.
```js
function findLUSlength(a,b)
    {
        // creating an unordered map to map
    // strings to their frequency
    let map= new Map();
    let strArr= [];
    strArr.push(a);
    strArr.push(b);
   
    // traversing all elements of vector strArr
    for (let s=0; s<strArr.length;s++)
    {
        // Creating all possible subsequences, i.e 2^n
        for (let i = 0; i < (1 << strArr[s].length); i++)
        {
            let t = "";
            for (let j = 0; j < strArr[s].length; j++) {
   
                // ((i>>j) & 1) determines which
                // character goes into string t
                if (((i >> j) & 1) != 0)
                     
                    t += strArr[s][j];
                     
            }
   
            // If common subsequence is found,
            // increment its frequency
            if (map.has(t))
                map.set(t,map.get(t)+1);
            else
                map.set(t,1);
        }
    }
    let res = 0;
    for (let [key, value] of map.entries())
   
    // traversing the map
    {
        // if frequency equals 1
        if (value == 1)
            res = Math.max(res, key.length);
    }
    return res;
    }
```
<br>

### Record
---
- `101 ms` time cost
- `9.13 MB` memory cost
- Your submission beats `100.00%` Submissions

`easy`

<br>

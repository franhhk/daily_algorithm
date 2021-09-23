1200 · Relative Ranks
===
### Company
`Google`

### Tags
`Sort`

### 문제 설명
---
#### Description
Given scores of N athletes, find their relative ranks and the people with the top three highest scores, who will be awarded medals: "Gold Medal", "Silver Medal" and "Bronze Medal".

N is a positive integer and won't exceed 10,000.
All the scores of athletes are guaranteed to be unique.

#### Example
Example 1:
```
Input: [5, 4, 3, 2, 1]
Output: ["Gold Medal", "Silver Medal", "Bronze Medal", "4", "5"]
Explanation: The first three athletes got the top three highest scores, so they got "Gold Medal", "Silver Medal" and "Bronze Medal". 
For the right two athletes, you just need to output their relative ranks according to their scores.
```
<br>

### 나의 풀이
---
<br>

```js
export class Solution {

  /**
   * findRelativeRanks
   *
   * @param nums: List[int]
   * @return: return List[str]
   */
  findRelativeRanks(nums) {
    let sortedNums = nums.slice()
    sortedNums.sort((a,b) => b-a);

    return nums.map((el, idx) => {
        if(el === sortedNums[0]) return "Gold Medal";
        else if(el === sortedNums[1]) return "Silver Medal";
        else if(el === sortedNums[2]) return "Bronze Medal";
        else return `${sortedNums.indexOf(el)+1}`;
    })
  }
}
```
<br>

### Reference Code
---
```js
export class Solution {

  /**
   * findRelativeRanks
   *
   * @param nums: List[int]
   * @return: return List[str]
   */
  findRelativeRanks(nums) {
    var sorted = nums.slice(),
        map = {};
    
    sorted.sort((a,b) => b-a);
    
    sorted.forEach((v,i) => {
        map[v] = i + 1 + '';
    })
    
    return nums.map((v,i) => {
        switch(v){
            case sorted[0]:
                return "Gold Medal";
            case sorted[1]:
                return "Silver Medal";
            case sorted[2]:
                return "Bronze Medal";
            default:
                return map[v]
        }
    })
  }
}
```
### Records
---
- `122 ms` time cost
- `9.27 MB` memory cost
- Your submission beats `95.24 %` Submissions
<br>

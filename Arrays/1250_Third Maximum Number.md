1250 : Third Maximum Number
===
### Company
`Microsoft`, `Bloomberg`, `Amazon`

### Tags
`Array`, `Enumerate`

### 문제 설명
---
#### Description
Given a non-empty array of integers, return the third maximum number in this array. If it does not exist, return the maximum number. The time complexity must be in O(n).

#### Example
Example 1:
```
Input: num = [3, 2, 1]
Output: 1
Explanation: The third maximum is 1.
```
Example 2:
```
Input: num = [1, 2]
Output: 2
Explanation: The third maximum does not exist, so the maximum (2) is returned instead.
```
Example 3:
```
Input: num = [2, 2, 3, 1]
Output: 1
Explanation: Note that the third maximum here means the third maximum distinct number.
Both numbers with value 2 are both considered as second maximum.
```

<br>

### 나의 풀이
---
- sort를 사용했다면 금방 풀렸을 문제지만, 시간복잡도를 O(N)으로 설정해달라는 조건이 있으므로 다른 방식을 생각해봐야 했다.
- 어떻게보면 간단한데 처음엔 candi를 배열로 두면서 pop메소드를 통해 자동으로 순서가 밀려나는 대신 매번 first, second, third에 할당해주는 방식으로 코드를 짜서 문제가 많았다.

```js
export class Solution {

  /**
   * thirdMax
   *
   * @param nums: the array
   * @return: the third maximum number in this array
   */
  thirdMax(nums) {
    let candi = [null, null, null]
    let hash = []
    
    for(let el of nums) {
        if(hash[el]) {
            continue;
        } else if(el > candi[0] || candi[0] === null) {
            candi.unshift(el)
        } else if(el > candi[1] || candi[1] === null) {
            candi.splice(1, 0, el)
        } else if(el > candi[2] || candi[2] === null) {
            candi.splice(2, 0, el)
        } else {
            continue;
        }

        hash[el] = 1;
        candi.pop();
    }
    return candi[2] || candi[0];
    
    // nums = nums.sort((a,b) => b-a)
    // return nums[2]
  }

}
```
<br>

### 다른 사람 풀이
---
- 내 풀이와 time / memory cost 면에서 거의 비슷하다
- -Infinity를 사용하는 방법에 익숙해져도 좋을 것 같다
```js
const findThirdMax = (arr) => {
   let [first, second, third] = [-Infinity, -Infinity, -Infinity];
   for (let el of arr) {
      if (el === first || el === second || el === third) {
         continue; };
         if (el > first) {
            [first, second, third] = [el, first, second]; continue; };
         if (el > second) {
            [second, third] = [el, second]; continue;
          };
         if (el > third) {
            third = el; continue;
      };
   };
   return third !== -Infinity ? third : first;
};
```
<br>

### Record
---
- `122 ms` time cost
- `10.18 MB` memory cost
- Your submission beats `85.19%` Submissions
- `easy`

<br>

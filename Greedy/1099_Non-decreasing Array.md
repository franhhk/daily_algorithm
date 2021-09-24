1099 · Non-decreasing Array
===
### Company
`Google`

### Tags
`Greedy`

### 문제 설명
---
#### Description
Given an array with n integers, your task is to check if it could become non-decreasing by modifying at most 1 element.

We define an array is non-decreasing if array[i] <= array[i + 1] holds for every i (1 <= i < n).

The n belongs to [1, 10,000].

#### Example
Example 1:
```
Input: [4,2,3]
Output: True
Explanation: You could modify the first 4 to 1 to get a non-decreasing array.
```
Example 2:
```
Input: [4,2,1]
Output: False
Explanation: You can't get a non-decreasing array by modify at most one element.
```

<br>

### 나의 풀이
---
- 처음엔 주석처리한 부분을 작성하지 못해 테스트 케이스를 일부 통과하지 못했다. 
- (ex) [3,4,2,1] -> (4, 2)에서 4를 수정하면 앞의 3보다 값이 작아지므로 1번의 수정으로 불가
- 예외에 대해 꼼꼼히 생각해보는 습관이 필요하다!
```js
export class Solution {

  /**
   * checkPossibility
   *
   * @param nums: an array
   * @return: if it could become non-decreasing by modifying at most 1 element
   */
  checkPossibility(nums) {
    let count = 0;
    for(let i=0; i < nums.length; i++) {
        if(nums[i] > nums[i+1]){
            // nums.splice(i, 1, nums[i+1]);
            // if(nums[i-1] > nums[i]) return false;
            count++
        }

        if(count>1) return false
    }

    return true;
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
- `9.17 MB` memory cost
- Your submission beats `100.00 %` Submissions

- `easy`

<br>

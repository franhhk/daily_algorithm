1451 · Maximize Distance to Closest Person
===
### Company
`Google`

### Tags
`Array`, `Simulation`

### 문제 설명
---
#### Description
In a row of seats, 1 represents a person sitting in that seat, and 0 represents that the seat is empty. 

There is at least one empty seat, and at least one person sitting.

Alex wants to sit in the seat such that the distance between him and the closest person to him is maximized. 

Return that maximum distance to closest person.

1 <= seats.length <= 20000
seats contains only 0s or 1s, at least one 0, and at least one 1.

#### Example
Example 1:
```
Input: [1,0,0,0,1,0,1]
Output: 2
Explanation: 
If Alex sits in the second open seat (seats[2]), then the closest person has distance 2.
If Alex sits in any other open seat, the closest person has distance 1.
Thus, the maximum distance to the closest person is 2.
```
Example 2:
```
Input: [1,0,0,0]
Output: 3
Explanation: 
If Alex sits in the last seat, the closest person is 3 seats away.
This is the maximum distance possible, so the answer is 3.
```

<br>

### 나의 풀이
---
- 두 사람 사이에 앉을 경우, 두 사람의 중간에 앉는 것이 가장 가까운 사람과의 거리를 최대로 하는 방법이다.
- 양 끝에 앉을 경우는 예외처리를 해줘야 한다.
```js
export class Solution {

  /**
   * maxDistToClosest
   *
   * @param seats: an array
   * @return: the maximum distance
   */
  maxDistToClosest(seats) {
    let distance = 0;
    let candi;
    let startIdx;

    for(let i = 0; i < seats.length; i++) {
        if(seats[i]) {
            if(startIdx !== undefined) {
                candi = parseInt((i - startIdx)/2)
            } else {
                candi = i - 0
            }
            startIdx = i
            distance = Math.max(distance, candi)
        } else if(i === seats.length -1) {
            candi = seats.length - 1 - startIdx
            distance = Math.max(distance, candi)
        }
    }

    return distance;
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
- `10.37 MB` memory cost
- Your submission beats `85.19%` Submissions
- `easy`

<br>

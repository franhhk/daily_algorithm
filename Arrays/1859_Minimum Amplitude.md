1859 · Minimum Amplitude
===
### Company
`Google`

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
- 처음엔 마땅한 풀이가 생각나지 않아서 재귀로 풀었다. 하지만 그냥 봐도 시간복잡도는 매우 높아보인다.
- 예상대로 배열의 길이가 조금만 커져도 runtime error가 발생했다.
```js
// 풀이 (1)
export class Solution {

  /**
   * MinimumAmplitude
   *
   * @param A: a list of integer
   * @return: Return the smallest amplitude
   */
  MinimumAmplitude(A) {
      let min;
      if(A.length <= 3) return 0

      function rec(arr) {
          if(arr.length === A.length -3) {
              let candi = Math.abs(Math.max(...arr) - Math.min(...arr))
              
              if(min === undefined) min = candi
              else if(min > candi) min = candi
          }
          for(let i = 0; i < arr.length; i++) {
              let copyArr = arr.slice()
              copyArr.splice(i, 1);
              rec(copyArr);
          }
      }
      rec(A);
      return min;
  }

}
```
- 다른 방법을 생각해보다가 sort를 사용하면 좋을 것 같다는 생각이 들었다.
- 수가 오름차순으로 놓여있다면 오른쪽으로 한칸씩 이동해가며 좌우로 총 3개의 숫자가 빠졌을 때 나머지 숫자들 사이의 amplitude를 구하면 된다.
```js
// 풀이 (2)
export class Solution {

  /**
   * MinimumAmplitude
   *
   * @param A: a list of integer
   * @return: Return the smallest amplitude
   */
  MinimumAmplitude(A) {
      if(A.length <= 3) return 0;

      A.sort((a,b) => a-b);

      let min;
      for(let i = 0; i < A.length - 1; i++) {
          let candi = Math.abs(A[i] - A[A.length-1 - 3 + i]);
          
          if((typeof candi === 'number' && min > candi) || min === undefined) min = candi;
      }

      return min;
  }

}
```
<br>

### 다른 사람 풀이
---
<br>

### Record
---
- `122 ms` time cost
- `9.50 MB` memory cost
- Your submission beats `66.67%` Submissions
- `easy`

<br>

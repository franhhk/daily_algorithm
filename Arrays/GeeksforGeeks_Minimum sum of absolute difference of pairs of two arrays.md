긱스포긱스 : Minimum sum of absolute difference of pairs of two arrays
===
### 링크
https://www.geeksforgeeks.org/minimum-sum-absolute-difference-pairs-two-arrays/?ref=lbp

<br>

### 문제 설명
---
Given two arrays a[] and b[] of equal length n. The task is to pair each element of array a to an element in array b, such that sum S of absolute differences of all the pairs is minimum.
Suppose, two elements a[i] and a[j] (i != j) of a are paired with elements b[p] and b[q] of b respectively, 
then p should not be equal to q.
### Examples: 
```
Input :  a[] = {3, 2, 1}
         b[] = {2, 1, 3}
Output : 0
Explaination :
 1st pairing: |3 - 2| + |2 - 1| + |1 - 3|
         = 1 + 1 + 2 = 4
 2nd pairing: |3 - 2| + |1 - 1| + |2 - 3|
         = 1 + 0 + 1 = 2
 3rd pairing: |2 - 2| + |3 - 1| + |1 - 3|
         = 0 + 2 + 2 = 4
 4th pairing: |1 - 2| + |2 - 1| + |3 - 3|
         = 1 + 1 + 0 = 2
 5th pairing: |2 - 2| + |1 - 1| + |3 - 3|
         = 0 + 0 + 0 = 0
 6th pairing: |1 - 2| + |3 - 1| + |2 - 3|
         = 1 + 2 + 1 = 4
 Therefore, 5th pairing has minimum sum of
 absolute difference.

Input :  n = 4
         a[] = {4, 1, 8, 7}
         b[] = {2, 3, 6, 5}
Output : 6
```
<br>

### 나의 풀이
---
- 시간 복잡도: O(N*log(N))
- 어떻게 짝을 만들지 생각하, 어떤 경우에 합이 최소가 될지를 우선 생각해보자!

<br>

```js
function test(a, b) {
    a.sort((a,b) => a-b)
    b.sort((a,b) => a-b)

    return a.reduce((a,c, idx) => {
        a += Math.abs(c - b[idx])
        return a
    },0)
}
```
<br>

### Reference Code
---
<br>

```js
function findMinSum(a, b, n)
    {
        // Sort both arrays
        a.sort();
        b.sort();
      
        // Find sum of absolute differences
        let sum = 0 ;
        for (let i = 0; i < n; i++)
            sum = sum + Math.abs(a[i] - b[i]);
      
        return sum;
    }
```
### 유사 문제
---
<br>

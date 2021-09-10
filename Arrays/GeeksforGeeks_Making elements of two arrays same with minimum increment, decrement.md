긱스포긱스 : Making elements of two arrays same with minimum increment/decrement
===
### 링크
https://www.geeksforgeeks.org/making-elements-of-two-arrays-same-with-minimum-incrementdecrement/?ref=lbp
<br>

### 문제 설명
---
Given two arrays of same size, we need to convert the first array into another with minimum operations. In an operation, we can either increment or decrement an element by one. Note that orders of appearance of elements do not need to be same.
Here to convert one number into another we can add or subtract 1 from it.
### Examples : 
```
Input : a = { 3, 1, 1 }, b = { 1, 2, 2 } 
Output : 2 
Explanation : Here we can increase any 1 into 2 by 1 operation and 3 to 2 in one decrement operation. So a[] becomes {2, 2, 1} which is a permutation of b[].
Input : a = { 3, 1, 1 }, b = { 1, 1, 2 } 
Output : 1
```
<br>

### 나의 풀이
---
- 풀면서 두 요소의 차의 절대값의 합이 최소인 경우를 구하는 문제와 풀이가 같다는 걸 깨달았다.

<br>

```js
function test(a, b) {
    a.sort();
    b.sort();

    return a.reduce((a, c, idx) => {
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
function MinOperation(a, b, n)
    {
        // sorting both arrays 
        // in ascending order
        a.sort(function(a, b){return a - b});
        b.sort(function(a, b){return a - b});
 
 
        // variable to store 
        // the final result
        let result = 0;
 
        // After sorting both arrays
        // Now each array is in non-
        // decreasing order. Thus,
        // we will now compare each
        // element of the array and
        // do the increment or decrement
        // operation depending upon the
        // value of array b[].
        for (let i = 0; i < n; ++i) 
        {
            if (a[i] > b[i])
                result = result +
                Math.abs(a[i] - b[i]);
 
            else if (a[i] < b[i])
                result = result +
                Math.abs(a[i] - b[i]);
        }
 
        return result;
    }
```
### 유사 문제
---
- GeekforGeeks_Minimum sum of absolute difference of pairs of two arrays [링크](https://www.geeksforgeeks.org/minimum-sum-absolute-difference-pairs-two-arrays/?ref=lbp)
<br>

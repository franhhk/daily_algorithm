긱스포긱스 : Minimum Increment / decrement to make array elements equal
===
### 링크
https://www.geeksforgeeks.org/minimum-increment-decrement-to-make-array-elements-equal/

<br>

### 문제 설명
---
Given an array of integers where 1 <= A[i] <= 10^18 . In one operation you can either Increment/Decrement any element by 1. The task is to find the minimum operations needed to be performed on the array elements to make all array elements equal.
### Examples: 
```
Input : A[] = { 1, 5, 7, 10 }
Output : 11
Increment 1 by 4, 5 by 0.
Decrement 7 by 2, 10 by 5.
New array A = { 5, 5, 5, 5 } with 
cost of operations = 4 + 0 + 2 + 5 = 11.

Input : A = { 10, 2, 20 }
Output : 18
```
<br>

### 나의 풀이
---
- 나는 arr만 주어진다는 가정 하에 코드를 작성했다.
- 시간 복잡도: O(N*log(N))

<br>

```js
var minOperations = function(arr) {
    arr.sort((a,b) => a-b);

    let midIdx = parseInt(arr.length/2)
    let answer = 0;

    for(let el of arr) {
        answer += Math.abs(arr[midIdx] - el)
    }
    
    //짝수일 경우 2가지를 모두 고려해준다
    if(arr.length % 2 === 0) {
        let tempAnswer = 0
        let midIdx = arr.length/2 + 1

        for(let el of arr) {
            tempAnswer += Math.abs(arr[midIdx] - el)
        }
        answer = Math.min(answer, tempAnswer)
    }
    
    return answer
};
```
<br>

### Reference Code
---
- 테스트 케이스가 주어져있지 않아서 확실하지 않지만 웹상의 풀이에 의문점이 있다.
- 짝수일 경우 가운데 요소 중 나머지 하나의 경우도 계산을 하는데, 이 때 레퍼런스 코드에서는 midIdx를 arr.length/2 -1 로 구했다.
- 하지만 이렇게 할 경우 가운데의 두 요소가 구해지지 않는다.
- 예를 들어 배열의 요소가 6개인 경우, arr.length/2는 3이다.
- 따라서 arr.length/2 -1 을 하면 2이므로, 우리가 원하는 3, 4의 인덱스 값을 구할 수 없다.
- 이부분을 제외한다면 나의 풀이와 거의 비슷하다.

<br>

```js
function minCost(A,n)
{
    // Initialize cost to 0
    var cost = 0;
 
    // Sort the array
    A.sort();
 
    // Middle element
    var K = A[parseInt(n/2)];
    var i;
    // Find Cost
    for (i = 0; i < n; ++i)
        cost += Math.abs(A[i] - K);
     
 
    // If n, is even. Take minimum of the
    // Cost obtained by considering both
    // middle elements
    if (n % 2 == 0) {
        var tempCost = 0;
 
        K = A[parseInt(n / 2) - 1];
 
        // Find cost again
        for (i = 0; i < n; ++i)
            tempCost += Math.abs(A[i] - K);
 
        // Take minimum of two cost
        cost = Math.min(cost, tempCost);
    }
 
    // Return total cost
    return cost;
}
```
### 유사 문제
---
- LeetCode_1551. Minimum Operations to Make Array Equal [](https://leetcode.com/problems/minimum-operations-to-make-array-equal/)
<br>

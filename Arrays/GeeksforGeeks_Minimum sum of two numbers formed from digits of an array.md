긱스포긱스 : Minimum sum of two numbers formed from digits of an array
===
### 링크
https://www.geeksforgeeks.org/minimum-sum-two-numbers-formed-digits-array-2/?ref=lbp

<br>

### 문제 설명
---
Given an array of digits (values are from 0 to 9), find the minimum possible sum of two numbers formed from digits of the array. All digits of given array must be used to form the two numbers.

### Examples: 
```
Input: [6, 8, 4, 5, 2, 3]
Output: 604
The minimum sum is formed by numbers 
358 and 246

Input: [5, 3, 0, 7, 4]
Output: 82
The minimum sum is formed by numbers 
35 and 047
```
<br>

### 나의 풀이
---
-합이 최소가 되는 조건
    1) 두 숫자의 자릿수가 최대한 비슷해야 한다. 즉, 6개의 숫자를 가지고 1, 5자리의 두 숫자로 나누는 것보다, 3, 3으로 나누는 것의 합이 훨씬 적다.
    2) 10^n의 자리에 있는 숫자는 n이 클수록 작아야 한다.
- 시간 복잡도: O(N*log(N))

<br>

```js
function test(arr) {
    arr.sort((a,b) => a-b); // 오름차순 정렬
    
    let num1 = "", num2 = "";
    let toggle = false;

    for(let num of arr) {
        if(toggle) {
            num2 += num
            toggle = false;
        } else {
            num1 += num;
            toggle = true;
        }
        console.log(num1, num2)
    }

    return Number(num1) + Number(num2);
}
```
<br>

### Reference Code
---
- 물론 토글을 사용하는 대신 2의 배수임을 이용하는 방법도 있다
- string 형태를 사용해서 뒤에 붙여주는 방식 대신에 이전 숫자에 10을 곱해준 후 더함으로써 자릿수를 추가하는 방법이다

<br>

```js
function minSum(a, n){
 
        // sort the elements
        a.sort();
 
        let num1 = 0;
        let num2 = 0;
        for(let i = 0;i<n;i++){
            if(i%2==0)
                num1 = num1*10+a[i];
            else num2 = num2*10+a[i];
        }
        return num2+num1;
    }
```
### 유사 문제
---
<br>

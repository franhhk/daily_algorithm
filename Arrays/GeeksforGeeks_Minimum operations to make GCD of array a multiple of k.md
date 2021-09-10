긱스포긱스 : Minimum operations to make GCD of array a multiple of k
===
### 링크
https://www.geeksforgeeks.org/minimum-operations-make-gcd-array-multiple-k/?ref=lbp

<br>

### 문제 설명
---
Given an array and k, we need to find the minimum operations needed to make GCD of the array equal or multiple of k. Here an operation means either increment or decrements an array element by 1.

### Examples:
```
Input : a = { 4, 5, 6 }, k = 5 
Output: 2 
Explanation: We can increase 4 by 1 so that it becomes 5 and decrease 6 by 1 so that it becomes 5. Hence minimum operation will be 2.

Input : a = { 4, 9, 6 }, k = 5 
Output : 3 
Explanation: Just like the previous example we can increase and decrease 4 and 6 by 1 and increase 9 by 1 so that it becomes 10. Now each element has GCD 5. Hence minimum operation will be 3.
```
<br>

### 나의 풀이
---
- 생각보다 헷갈렸는데 막상 한번에 해결되니 신기했다

<br>

```js
function test(arr, k) {
    // arr 요소의 최대공약수가 k로 나누어 떨어져야 한다
    // k가 arr 요소의 공약수여야 한다 
    let ops = 0;
    for(let el of arr) {
        let remains = el % k
        if(remains  > k/2) {
            remains = k - remains
        }
        ops += remains
    }
    return ops
}
```
<br>

### Reference Code
---
- 나와 풀이가 비슷하다! 원리도 같다!
<br>

```js
function MinOperation(a, n, k)
{
    let result = 0;
     
    for (let i = 0; i < n; ++i)
    {
     
        // If array value is
        // not 1 and it is
        // greater than k then
        // we can increase the
        // or decrease the remainder
        // obtained by dividing
        // k from the ith value of
        // array so that we get the
        // number which is either
        // closer to k or its multiple
        if (a[i] != 1 && a[i] > k)
        {
            result = result + Math.min(a[i] %
                                    k, k -
                                    a[i] % k);
        }
        else
        {
 
            // Else we only have one
            // choice which is to
            // increment the value
            // to make equal to k
            result = result +
                      k - a[i];
        }
    }
 
    return result;
}
```
### 유사 문제
---
<br>

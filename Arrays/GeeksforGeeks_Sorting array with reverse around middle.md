긱스포긱스 : Sorting array with reverse around middle
===
### 링크
https://www.geeksforgeeks.org/sorting-array-reverse-around-middle/?ref=lbp
<br>

### 문제 설명
---
Consider the given array arr[], we need to find if we can sort array with the given operation. The operation is 
1. We have to select a subarray from the given array such that the middle element(or elements (in case of even 
number of elements)) of subarray is also the middle element(or elements (in case of even number of elements)) of 
the given array. 
2. Then we have to reverse the selected subarray and place this reversed subarray in the array. 
We can do the above operation as many times as we want. The task is to find if we can sort array with the given operation. 
### Examples: 
```
Input : arr[] = {1, 6, 3, 4, 5, 2, 7}
Output : Yes
We can choose sub-array[3, 4, 5] on 
reversing this we get [1, 6, 5, 4, 3, 2, 7]
again on selecting [6, 5, 4, 3, 2] and 
reversing this one we get [1, 2, 3, 4, 5, 6, 7] 
which is sorted at last thus it is possible
to sort on multiple reverse operation.

Input : arr[] = {1, 6, 3, 4, 5, 7, 2}
Output : No
```
<br>

### 나의 풀이
---
- 처음엔 실제로 reverse를 하면서 매번 정렬을 확인하는 방법으로 풀었다
- 하지만 풀다보니 시간이 너무 오래 걸린다는 것을 알게 되어 다른 풀이를 생각해보게 되었다.
<br>

```js
function test(arr) {
    // 최종적으로 array가 정렬이 되려면 subarray도 정렬이 되어있어야 한다
    let midIdx = parseInt(arr.length / 2);
    let i =0;
    let subArr = arr.length % 2? arr.slice(midIdx - 1 - i, midIdx + 2 + i): arr.slice(midIdx - 1 - i, midIdx + 1 + i);

    while(subArr.length <= arr.length) {
        if(subArr === subArr.sort()) {
            i++
            subArr = arr.length % 2? arr.slice(midIdx - 1 - i, midIdx + 2 + i): arr.slice(midIdx - 1 - i, midIdx + 1 + i);
            subArr.reverse()
        } else {
            return "No"
        }
    }

    return "Yes"
}
```
<br>

### Reference Code
---
- 왜 이 간단한 방법이 떠오르지 않았을까. 정말 알다가도 모를 일이다..
<br>

```js
 function ifPossible(arr, n)
    {
   
        // making the copy of the original array
        let copy = arr;
   
        // sorting the copied array
        copy.sort();
   
        for (let i = 0; i < n; i++) {
   
            // checking mirror image of elements of
            // sorted copy array and equivalent element
            // of original array
            if (!(arr[i] == copy[i]) && !(arr[n - 1 - i] == copy[i]))
                return false;
        }
   
        return true;
    }
```
### 유사 문제
---
<br>

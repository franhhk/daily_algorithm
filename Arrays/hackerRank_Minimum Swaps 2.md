해커랭크 : Minimum Swaps 2
===
### 링크
https://www.hackerrank.com/challenges/minimum-swaps-2/problem?h_l=interview&playlist_slugs%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D=arrays

<br>

### 문제 설명
---
You are given an unordered array consisting of consecutive integers  [1, 2, 3, ..., n] without any duplicates. You are allowed to swap any two elements. Find the minimum number of swaps required to sort the array in ascending order.

#### Example
Perform the following steps:

```
i   arr                     swap (indices)
0   [7, 1, 3, 2, 4, 5, 6]   swap (0,3)
1   [2, 1, 3, 7, 4, 5, 6]   swap (0,1)
2   [1, 2, 3, 7, 4, 5, 6]   swap (3,4)
3   [1, 2, 3, 4, 7, 5, 6]   swap (4,5)
4   [1, 2, 3, 4, 5, 7, 6]   swap (5,6)
5   [1, 2, 3, 4, 5, 6, 7]
```
It took  swaps to sort the array.

#### Function Description

Complete the function minimumSwaps in the editor below.

minimumSwaps has the following parameter(s):

- int arr[n]: an unordered array of integers
#### Returns

int: the minimum number of swaps to sort the array
#### Input Format

The first line contains an integer, , the size of .
The second line contains  space-separated integers .

#### Constraints
- 1 <= arr[i] <= n
- 1 <= n <= 10^5
#### Sample Input 0
```
4
4 3 1 2
```
#### Sample Output 0
```
3
```
<br>

### 나의 풀이
---
<br>

```js
function minimumSwaps(arr) {
    arr.unshift(0);
    let answer = 0;
    
    for(let i=0; i < arr.length; i++) {
        let idx = arr[i]
        if(idx !== i) {
            let removed = arr[idx]
            arr[i] = removed
            arr[idx] = idx
            answer++
            i-- //제 자리에 맞는 알파벳이 돌아오는 걸 확인하고 넘어가는 게 계속해서 루프를 도는 것보다 효율적이라고 생각했다
        }
    }
    
    return answer;
}
```
### 유사 문제
---

<br>

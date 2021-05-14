코드스테이츠 : (토이 10번) binarySearch
===
### 링크
https://urclass.codestates.com/codeproblem/b06d36ed-129a-44e5-a624-90a8768848ad

<br>

### 문제 설명
---
오름차순 정렬된 정수의 배열(arr)과 정수(target)를 입력받아 target의 인덱스를 리턴해야 합니다.

<br>

### 주의사항
---
- 이진탐색 알고리즘(O(logN))을 사용해야 합니다.
- 단순한 배열 순회(O(N))로는 통과할 수 없는 테스트 케이스가 존재합니다.
- target이 없는 경우, -1을 리턴해야 합니다.

<br>


### 나의 풀이
---
- 이진탐색의 기본 중 기본이라 잘 기억해둬야겠다는 생각이 든다

<br>

```js
const binarySearch = function (arr, target) {
  let startIdx = 0;
  let endIdx = arr.length - 1;

  while(startIdx <= endIdx) {
    let midIdx = parseInt((endIdx + startIdx) / 2)
    if(arr[midIdx] === target) {
      return midIdx;
    }
    if(arr[midIdx] < target) {
      startIdx = midIdx + 1
    } else {
      endIdx = midIdx - 1
    }
  }

  return -1;
};
```
<br>

### Reference Code
---
- 내 코드와 똑같다

```js
const binarySearch = function (arr, target) {
  let left = 0,
    right = arr.length - 1;
  while (left <= right) {
    let middle = parseInt((right + left) / 2);
    if (arr[middle] === target) {
      return middle;
    }
    if (target < arr[middle]) {
      right = middle - 1;
    } else {
      left = middle + 1;
    }
  }
  return -1;
};
```
<br>

### 유사 문제
---

<br>

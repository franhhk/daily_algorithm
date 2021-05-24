코드스테이츠 : (토이 18번) getItemFromTwoSortedArrays
===
### 링크
https://urclass.codestates.com/codeproblem/bddd30d8-44c1-4039-8c49-134555c03552

<br>

### 문제 설명
---
길이가 m, n이고 오름차순으로 정렬되어 있는 자연수 배열들을 입력받아 전체 요소 중 k번째 요소를 리턴해야 합니다.

<br>

### 주의사항
---
- 두 배열의 길이의 합은 1,000,000 이하입니다.
- 어떤 배열 arr의 k번째 요소는 arr[k-1]을 의미합니다.

<br>


### 나의 풀이
---
- 시간복잡도를 O(K)에서 O(logK)로 줄이지 못해 테스트 케이스 하나를 통과하지 못했다

<br>

```js
const getItemFromTwoSortedArrays = function (arr1, arr2, k) {
  let target, idx1 = 0, idx2 = 0, count = 0;

  while(count < k) {
    let remains = k - count
    if(idx1 >= arr1.length) {
      return arr2[idx2 + remains]
    }

    if(idx2 >= arr1.length) {
      return arr1[idx1 + remains]
    }

    if(arr1[idx1] < arr2[idx2]) {
      target = arr1[idx1]
      idx1++
    } else {
      target = arr2[idx2]
      idx2++
    }
    count++
  }
  return target;
};
```
<br>

### Reference Code
---
- k는 내 코드에서의 remains와 같은 역할을 한다 (k 재할당)

```js
const getItemFromTwoSortedArrays = function (arr1, arr2, k) {
  let leftIdx = 0,
    rightIdx = 0;

  while (k > 0) {
    let cnt = Math.ceil(k / 2);
    let leftStep = cnt,
      rightStep = cnt;
      
    if (leftIdx === arr1.length) {
      rightIdx = rightIdx + k;
      break;
    }

    if (rightIdx === arr2.length) {
      leftIdx = leftIdx + k;
      break;
    }

    if (cnt > arr1.length - leftIdx) leftStep = arr1.length - leftIdx;
    if (cnt > arr2.length - rightIdx) rightStep = arr2.length - rightIdx;

    if (arr1[leftIdx + leftStep - 1] < arr2[rightIdx + rightStep - 1]) {
      leftIdx = leftIdx + leftStep;
      k = k - leftStep;
    } else {
      rightIdx = rightIdx + rightStep;
      k = k - rightStep;
    }
  }

  leftMax = arr1[leftIdx - 1] || -1;
  rightMax = arr2[rightIdx - 1] || -1;

  return Math.max(leftMax, rightMax);
};
```
<br>

### 유사 문제
---

<br>

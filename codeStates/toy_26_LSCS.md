코드스테이츠 : (토이 26번) LSCS
===
### 링크
---
https://urclass.codestates.com/codeproblem/2b959b1d-f8d2-4af8-ab2f-d5f730b5c0a3

<br>

### 문제 설명
---
정수를 요소로 갖는 배열을 입력받아 다음의 조건을 만족하는 LSCS*를 리턴해야 합니다.

- LSCS: 주어진 배열의 연속된 부분 배열*의 합을 구한다고 할 때, 이 중 가장 큰 값(Largest Sum of Contiguous Subarray)
- 연속된 부분 배열들: 배열 [1,2,3]의 연속 부분 배열은 [1], [1, 2], [1, 2, 3], [2], [2, 3], [3] 입니다.

<br>

### 입력
---
- number 타입을 요소로 갖는 배열
- arr.length는 60,000 이하
- arr[i]는 -100,000 이상 100,000 이하의 정수

<br>

### 출력
---
number 타입을 리턴해야 합니다.

<br>

### 주의사항
---
배열의 모든 요소가 음수인 경우도 있습니다.

<br>

### Advanced
---
LSCS를 계산하는 효율적인 알고리즘(O(N))이 존재합니다. 쉽지 않기 때문에 바로 레퍼런스 코드를 보고 이해하는 데 집중하시기 바랍니다.

<br>

### 나의 풀이
---
- 테스트 케이스는 통과했으나 시간복잡도를 줄이지 못해 Advanced 항목을 통과하지 못했다
- 배열에 음수가 끼어있다는 점을 이용하면 될 것 같아서 코드를 수정했

<br>

```js
//초기의 코드

const LSCS = function (arr) {
  let length = 1, start = 0
  let answer = arr[0]

  while(length <= arr.length) {
    let node = 0
    for(let i = start; i < start + length; i++) {
      node = node + arr[i]
    }
    if(answer < node) {
      answer = node
    }
    if(start + length >= arr.length) {
      start = 0
      length++
    } else {
      start++
    }
  }

  return answer
};
```

```js
//최종 코드

const LSCS = function (arr) {
  let length = 1, start = 0
  let answer = arr[0]

  while(length <= arr.length) {
    let node = 0
    for(let i = start; i < start + length; i++) {
      node = node + arr[i]
    }
    
    //더한 값이 음수인 경우 멈추고 다음 인덱스로 넘어간다
    if(node < 0) {
      node = 0
      i = start++
    }
    
    if(answer < node) {
      answer = node
    }
    if(start + length >= arr.length) {
      start = 0
      length++
    } else {
      start++
    }
  }

  return answer
};
```

<br>

### Reference Code
---
- 처음부터 더하다가 그 값이 음수가 된다면, 그 앞의 연속된 배열을 더하는 것은 의미가 없다!

```js
// naive solution: O(N^2)
// const LSCS = function (arr) {
//   let max = -100000;
//   for (let i = 0; i < arr.length; i++) {
//     let sum = arr[i];
//     if (sum > max) max = sum;
//     for (let j = i + 1; j < arr.length; j++) {
//       sum = sum + arr[j];
//       if (sum > max) max = sum;
//     }
//   }
//   return max;
// };

// dynamic programming: O(N)
const LSCS = function (arr) {
  let subArrSum = 0; // 연속 배열의 합
  let max = Number.MIN_SAFE_INTEGER; // 정답의 후보를 저장
  for (let i = 0; i < arr.length; i++) {
    subArrSum = subArrSum + arr[i];
    if (subArrSum > max) max = subArrSum;

    // 연속된 구간의 합이 음수인 경우,
    // 해당 부분은 버리고 다시 시작해도 된다.
    if (subArrSum < 0) {
      subArrSum = 0;
    }
  }

  return max;
};

// also dynamic 2: O(N)
// const LSCS = function (arr) {
//   let subArrSum = arr[0];
//   let max = arr[0]; // 정답의 후보를 저장
//   for (let i = 1; i < arr.length; i++) {
//     // subArrSum는 바로 직전의 요소까지 검토했을 때 가장 연속합
//     // 연속합에 추가로 검토하는 요소, 즉 arr[i]를 더하는 것보다
//     // arr[i] 하나의 값이 더 큰 경우 (subArrSum가 음수일 경우)
//     // subArrSum를 버리는 게 좋다.
//     // 쭉 더해서 음수인 부분은 굳이 더할 필요가 없다.
//     subArrSum = Math.max(subArrSum + arr[i], arr[i]);
//     max = Math.max(max, subArrSum);
//   }

//   return max;
// };
```

<br>

### 유사 문제
---

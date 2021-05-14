코드스테이츠 : (토이 12번) treeBFS
===
### 링크
https://urclass.codestates.com/codeproblem/9347b40b-4775-4ab9-92fb-63bbed16a14f

<br>

### 문제 설명
---
정수를 요소로 갖는 배열을 입력받아 오름차순으로 정렬하여 리턴해야 합니다.

<br>

### 주의사항
---
- 삽입 정렬을 구현해야 합니다.
- arr.sort 사용은 금지됩니다.
- 입력으로 주어진 배열은 중첩되지 않은 1차원 배열입니다.

<br>

### Advanced
---
insertionSort 함수의 두 번째 인자로 callback 함수를 받아서, 그 함수의 리턴값을 기준으로 요소들을 정렬해 보세요.

<br>


### 나의 풀이
---
- Advanced 항목을 고려하여 compA, comB를 도입했다.
- arr의 요소를 처음부터 끝까지 두 개씩 비교하면서 순서를 맞춘다
- arr 순회를 마쳤을 때 순서가 바뀐 요소가 없다면 arr를 리턴한다

<br>

```js
const insertionSort = function (arr, cb) {
  let isAlter = true;

  while(isAlter) {
    isAlter = false
    for(let i = 0; i < arr.length - 1; i++) {
      let a = arr[i]
      let b = arr[i + 1]
      let compA = a;
      let compB = b;

      if(typeof cb === 'function') {
        compA = cb(a);
        compB = cb(b)
      }

      if(compB < compA) {
        arr[i] = b
        arr[i + 1] = a
        isAlter = true;
      }
    }
  }
  return arr;
};

```
<br>

### Reference Code
---
- arr의 0번째 요소부터 새로운 배열에 집어넣는다
- sorted에 새로운 요소를 추가할 때마다 기존에 있는 요소들과의 크기를 비교한다
- 개인적으로는 내 코드가 더 직관적인 것 같다

```js
// naive solution
// const insertionSort = function (arr) {
//   let sorted = [arr[0]];
//   for (let i = 1; i < arr.length; i++) {
//     if (arr[i] >= sorted[i - 1]) {
//       sorted.push(arr[i]);
//     } else {
//       for (let j = 0; j < i; j++) {
//         if (arr[i] <= sorted[j]) {
//           const left = sorted.slice(0, j);
//           const right = sorted.slice(j);
//           sorted = left.concat(arr[i], right);
//           break;
//         }
//       }
//     }
//   }

//   return sorted;
// };

const insertionSort = function (arr, transform = (item) => item) {
  let sorted = [arr[0]];
  for (let i = 1; i < arr.length; i++) {
    if (transform(arr[i]) >= transform(sorted[i - 1])) {
      sorted.push(arr[i]);
    } else {
      for (let j = 0; j < i; j++) {
        if (transform(arr[i]) <= transform(sorted[j])) {
          const left = sorted.slice(0, j);
          const right = sorted.slice(j);
          sorted = left.concat(arr[i], right);
          break;
        }
      }
    }
  }

  return sorted;
};
```
<br>

### 유사 문제
---

<br>

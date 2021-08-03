코드스테이츠 : (토이 45번) subsetSum
===
### 링크
https://urclass.codestates.com/codeproblem/9bd2dccb-4394-4c7d-a80d-46b5a7d8d7d3

<br>

### 문제 설명
---
자연수의 집합(set)과 자연수(bound)를 입력받아 아래의 조건을 만족하는 가장 큰 수를 리턴해야 합니다.

- 집합의 요소를 최대 한번씩만 더해서 만들어야 한다.
- `bound`를 넘지 않아야 한다.

### 입력
---
#### 인자 1: set
자연수를 요소로 갖는 배열
#### 인자 2: bound
number 타입의 자연수 (bound <= 300)
#### 출력
number 타입을 리턴해야 합니다.

<br>

### 주의사항
---
조건을 만족하는 조합이 없는 경우, 0을 리턴해야 합니다.

<br>

### 나의 풀이
---

<br>

```js
const subsetSum = function (set, bound) {
  let answer = 0;
  set = set.filter(el => el <= bound);

  function subset(sum, idx) {
    if(sum <= bound && answer < sum) {
        answer = sum
      }

    if(idx === set.length) {
      return '';
    }
    subset(sum + set[idx], idx + 1)
    subset(sum, idx+1)
  }

  subset(0, 0)

  return answer;
};
```
<br>

### Reference Code
---

```js
// naive solution: O(2^N)
// const subsetSum = function (set, bound) {
//   const LENGTH = set.length;
//   function pickOrNot(idxToCheck, left) {
//     if (idxToCheck === LENGTH) return bound - left;

//     if (set[idxToCheck] > left) return pickOrNot(idxToCheck + 1, left);
//     if (set[idxToCheck] === left) return bound;

//     return Math.max(
//       pickOrNot(idxToCheck + 1, left - set[idxToCheck]),
//       pickOrNot(idxToCheck + 1, left)
//     );
//   }

//   return pickOrNot(0, bound);
// };

// dynamic: O(bound * N)
const subsetSum = function (set, bound) {
  let max = 0;
  // 집합의 원소들로 만들 수 있는 합의 조합을 관리하는 배열
  // bound는 최대 300이므로, 배열의 크기를 301로 설정한다.
  // 300 + 1 로 적는 이유는 가독성과 배열 인덱스를 직관적으로 관리하기 위함
  // 원소들을 통해 sum을 만들 수 있는 경우, bound[sum]을 true로 설정한다.
  const cached = Array(300 + 1).fill(false);
  set.forEach((member) => {
    // 집합의 원소를 차례대로 검사
    // 이전 단계까지 검사한 원소들로 만들 수 있는 합의 조합은 cached에 저장되어 있다.
    // cached의 요소에 각각 member를 더한 값을 만들 수 있다.
    const reachables = [];
    // 이 중에서 bound를 넘어가는 값은 고려하지 않는다.
    // reachables로 따로 관리하는 이유는 중복 계산을 피하기 위함
    for (let wanted = 1; wanted <= bound - member; wanted++) {
      if (cached[wanted] === true) {
        const reached = wanted + member;
        reachables.push(reached);
        if (reached > max) max = reached;
      }
    }

    // bound 이하로 만들 수 있는 합의 조합을 cached에 추가한다.
    reachables.forEach((r) => (cached[r] = true));

    // 집합의 원소를 마지막에 cached에 추가하는 이유는 중복 계산을 방지하기 위함
    if (member <= bound) {
      cached[member] = true;
      if (member > max) max = member;
    }
  });
  return max;
};

// 객체를 활용한 방법
// const subsetSum = function (set, bound) {
//   let max = 0;
//   const reachables = {};
//   set.forEach((member) => {
//     Object.keys(reachables).forEach((r) => {
//       // 객체의 키는 string 타입
//       const reached = Number(r) + member;
//       if (reached <= bound) {
//         reachables[reached] = true;
//         if (reached > max) max = reached;
//       }
//     });
//     if (member <= bound) {
//       reachables[member] = true;
//       if (member > max) max = member;
//     }
//   });
//   return max;
// };
```
<br>

### 유사 문제
---

<br>

코드스테이츠 : (토이 11번) powerSet
===
### 링크
https://urclass.codestates.com/codeproblem/e7598493-e085-4931-b8c2-8225ecca4382

<br>

### 문제 설명
---
하나의 집합을 의미하는 문자열을 입력받아 각 문자를 가지고 만들 수 있는 모든 부분집합을 리턴해야 합니다.

<br>

### 제한 조건
---
- arr[i]는 각 부분집합을 구성하는 원소를 연결한 문자열입니다.
- arr[i]는 알파벳 순서로 정렬되어야 합니다.
- 집합은 중복된 원소를 허용하지 않습니다.
- 부분집합은 빈 문자열을 포함합니다.
- arr은 사전식 순서(lexical order)로 정렬되어야 합니다.

<br>


### 나의 풀이
---
- 프로그래머스 문제에서 배웠던 Set 메소드를 드디어 써봤다!
- 다만 set를 Object.keys(set).length를 하니 값이 0으로 인식되어 오류가 났다

<br>

```js
const powerSet = function (str) {
  let result = [];
  let set = new Set(str.split('').sort())
  let uniq = [...set]

  function rec(idx, el) {
    if(idx === uniq.length) {
      result.push(el)
      return;
    }
    rec(idx + 1, el)
    rec(idx + 1, el + uniq[idx])
  }
  
  rec(0, '')

  return result.sort()
};
```
<br>

### Reference Code
---
- 중복 요소를 제외하는 부분만 빼면 내 풀이와 거의 비슷한 것 같다
- 나는 개인적으로 내 코드가 더 보기 좋다

```js
const powerSet = function (str) {
  // 정렬
  const sorted = str.split('').sort();

  // 중복 제거
  const deduplicated = sorted.reduce((acc, item) => {
    if (acc[acc.length - 1] === item) {
      return acc;
    } else {
      return acc.concat(item);
    }
  });

  let subSets = [];
  const pickOrNot = (idx, subset) => {
    // base case
    if (idx === deduplicated.length) {
      // 마지막 문자까지 검토한 경우
      subSets.push(subset);
      return;
    }

    // recursive case
    // idx번째 문자가 포함되지 않는 경우
    pickOrNot(idx + 1, subset);

    // idx번째 문자가 포함되는 경우
    pickOrNot(idx + 1, subset + deduplicated[idx]);
  };

  pickOrNot(0, '');

  return subSets.sort();
};```
<br>

### 유사 문제
---
- 코드스테이츠 / Data Structure & Algorithm_20 집밥이 그리워

<br>

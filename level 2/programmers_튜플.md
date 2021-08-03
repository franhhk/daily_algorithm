프로그래머스 : 튜플
===
### 링크
https://programmers.co.kr/learn/courses/30/lessons/64065

<br>

### 문제 설명
---
셀수있는 수량의 순서있는 열거 또는 어떤 순서를 따르는 요소들의 모음을 튜플(tuple)이라고 합니다. n개의 요소를 가진 튜플을 n-튜플(n-tuple)이라고 하며, 다음과 같이 표현할 수 있습니다.

(a1, a2, a3, ..., an)
튜플은 다음과 같은 성질을 가지고 있습니다.

중복된 원소가 있을 수 있습니다. ex : (2, 3, 1, 2)
원소에 정해진 순서가 있으며, 원소의 순서가 다르면 서로 다른 튜플입니다. ex : (1, 2, 3) ≠ (1, 3, 2)
튜플의 원소 개수는 유한합니다.
원소의 개수가 n개이고, 중복되는 원소가 없는 튜플 (a1, a2, a3, ..., an)이 주어질 때(단, a1, a2, ..., an은 자연수), 이는 다음과 같이 집합 기호 '{', '}'를 이용해 표현할 수 있습니다.

{{a1}, {a1, a2}, {a1, a2, a3}, {a1, a2, a3, a4}, ... {a1, a2, a3, a4, ..., an}}
예를 들어 튜플이 (2, 1, 3, 4)인 경우 이는

{{2}, {2, 1}, {2, 1, 3}, {2, 1, 3, 4}}
와 같이 표현할 수 있습니다. 이때, 집합은 원소의 순서가 바뀌어도 상관없으므로

{{2}, {2, 1}, {2, 1, 3}, {2, 1, 3, 4}}
{{2, 1, 3, 4}, {2}, {2, 1, 3}, {2, 1}}
{{1, 2, 3}, {2, 1}, {1, 2, 4, 3}, {2}}
는 모두 같은 튜플 (2, 1, 3, 4)를 나타냅니다.

특정 튜플을 표현하는 집합이 담긴 문자열 s가 매개변수로 주어질 때, s가 표현하는 튜플을 배열에 담아 return 하도록 solution 함수를 완성해주세요.
<br>

### 제한 조건
---
- s의 길이는 5 이상 1,000,000 이하입니다.
- s는 숫자와 '{', '}', ',' 로만 이루어져 있습니다.
- 숫자가 0으로 시작하는 경우는 없습니다.
- s는 항상 중복되는 원소가 없는 튜플을 올바르게 표현하고 있습니다.
- s가 표현하는 튜플의 원소는 1 이상 100,000 이하인 자연수입니다.
- return 하는 배열의 길이가 1 이상 500 이하인 경우만 입력으로 주어집니다.
<br>


### 나의 풀이
---
- 객체처럼 구성된 하나의 문자열을 배열로 바꾸는 부분에서 의외로 생각보다 많은 시간을 소요했다. replace 사용에 익숙해지는 과정이라고 생각한다.

```js
function solution(s) {
    return s = s
        .replace(/{/g, '')
        .split('}')
        .filter(el => el !== '')
        .map(el => el.split(',').filter(el => el !== '').map(el => Number(el)))
        .sort((a,b) => {
            if(a.length < b.length) {
                return -1
            } else {
                return 1
            }
        })
        .reduce((a,c) => {
        for(let el of c) {
            if(!a.includes(el)) {
                return a = a.concat(el)
            }
        }
    })
}
```

<br>

### 다른 사람의 풀이
---
- split 메소드를 '{' 또는 '}'을 기준으로 했을 때 생기는 번거로움을 깔끔하게 해결

```js
const tupleFrom = (str) =>
  str.slice(2, -2).split('},{')
    .map((it) => toNumbers(it))
    .sort(accendingByLength)
    .reduce((acc, cur) =>
      [...acc, ...cur.filter((it) => !acc.includes(it))], []);

const toNumbers = (str) => str.split(',').map(it => Number(it));

const accendingByLength = (arr1, arr2) => arr1.length - arr2.length;

const solution = (s) => tupleFrom(s);
```

<br>

### 유사 문제
---

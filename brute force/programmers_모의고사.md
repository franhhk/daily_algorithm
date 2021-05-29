프로그래머스 : 모의고사
===
### 링크
https://programmers.co.kr/learn/courses/30/lessons/42840

<br>

### 문제 설명
---
수포자는 수학을 포기한 사람의 준말입니다. 수포자 삼인방은 모의고사에 수학 문제를 전부 찍으려 합니다. 수포자는 1번 문제부터 마지막 문제까지 다음과 같이 찍습니다.

1번 수포자가 찍는 방식: 1, 2, 3, 4, 5, 1, 2, 3, 4, 5, ...
2번 수포자가 찍는 방식: 2, 1, 2, 3, 2, 4, 2, 5, 2, 1, 2, 3, 2, 4, 2, 5, ...
3번 수포자가 찍는 방식: 3, 3, 1, 1, 2, 2, 4, 4, 5, 5, 3, 3, 1, 1, 2, 2, 4, 4, 5, 5, ...

1번 문제부터 마지막 문제까지의 정답이 순서대로 들은 배열 answers가 주어졌을 때, 가장 많은 문제를 맞힌 사람이 누구인지 배열에 담아 return 하도록 solution 함수를 작성해주세요.

<br>

### 제한 조건
---
- 시험은 최대 10,000 문제로 구성되어있습니다.
- 문제의 정답은 1, 2, 3, 4, 5중 하나입니다.
- 가장 높은 점수를 받은 사람이 여럿일 경우, return하는 값을 오름차순 정렬해주세요.

<br>

### 나의 풀이
---
```js
function solution(answers) {
    var answer = [];
    const one = [1, 2, 3, 4, 5],
          two = [2, 1, 2, 3, 2, 4, 2, 5],
          three = [3, 3, 1, 1, 2, 2, 4, 4, 5, 5]
    let idx = 0
    let cnt = [0, 0, 0]
    
    for(let el of answers) {
        if(el === one[idx % one.length]) { cnt[0]++ }
        if(el === two[idx % two.length]) { cnt[1]++ }
        if(el === three[idx % three.length]) { cnt[2]++ }
        
        idx++
    }
    
    let max = Math.max(...cnt)
    for(let i = 0; i < cnt.length; i++) {
        if(cnt[i] === max) { answer.push(i + 1)}
    }
    
    return answer;
}
```
<br>

### 다른 사람의 풀이
---
- 보기에 깔끔하다
- filter 메소드의 index 인자를 활용한 풀이가 인상적이다. 나도 고차함수의 인덱스 인자를 잘 활용하고 싶다.

```js
function solution(answers) {
    var answer = [];
    var a1 = [1, 2, 3, 4, 5];
    var a2 = [2, 1, 2, 3, 2, 4, 2, 5]
    var a3 = [ 3, 3, 1, 1, 2, 2, 4, 4, 5, 5];

    var a1c = answers.filter((a,i)=> a === a1[i%a1.length]).length;
    var a2c = answers.filter((a,i)=> a === a2[i%a2.length]).length;
    var a3c = answers.filter((a,i)=> a === a3[i%a3.length]).length;
    var max = Math.max(a1c,a2c,a3c);

    if (a1c === max) {answer.push(1)};
    if (a2c === max) {answer.push(2)};
    if (a3c === max) {answer.push(3)};


    return answer;
}
```

<br>

### 유사 문제
---

<br>

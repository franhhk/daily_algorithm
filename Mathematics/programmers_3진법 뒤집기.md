프로그래머스 : 3진법 뒤집기
===
### 링크
https://programmers.co.kr/learn/courses/30/lessons/68935
<br>

### 문제 설명
---
자연수 n이 매개변수로 주어집니다. n을 3진법 상에서 앞뒤로 뒤집은 후, 이를 다시 10진법으로 표현한 수를 return 하도록 solution 함수를 완성해주세요.

<br>

### 제한 조건
---
- n은 1 이상 100,000,000 이하인 자연수입니다.
<br>

### 입출력 예
---
```
n	result
45	7
125	229
```

### 나의 풀이
---
```js
function solution(n) {
    let answer = 0;
    let i = 0;

    for(let el of n.toString(3)){
        answer += el * Math.pow(3, i)
        i++
    }

    return answer;
}
```

<br>
### 다른 사람 풀이
---
- parseInt() 메소드를 저렇게 쓸 수 있다는 걸 처음 알았다.
- parseInt() 함수는 문자열 인자를 구문분석하여 특정 진수(수의 진법 체계에 기준이 되는 값)의 정수를 반환합니다.

```js
const solution = (n) => {
    return parseInt([...n.toString(3)].reverse().join(""), 3);
}
```

<br>

프로그래머스 : 최대공약수와 최소공배수
===
### 링크
https://programmers.co.kr/learn/courses/30/lessons/12940

<br>

### 문제 설명
---
두 수를 입력받아 두 수의 최대공약수와 최소공배수를 반환하는 함수, solution을 완성해 보세요. 배열의 맨 앞에 최대공약수, 그다음 최소공배수를 넣어 반환하면 됩니다. 예를 들어 두 수 3, 12의 최대공약수는 3, 최소공배수는 12이므로 solution(3, 12)는 [3, 12]를 반환해야 합니다.
<br>

### 제한 조건
---
두 수는 1이상 1000000이하의 자연수입니다.

<br>


### 나의 풀이
---
```js
function solution(n, m) {
    var answer = [];
    
    //lcm = |a*b|/gcd 이므로
    for(let i = 1; i <= Math.min(n , m); i++) {
        if(n % i === 0 && m % i === 0) {
            answer[0] = i
            answer[1] = n*m / i
        }
    }
    
    return answer;
}
```

<br>

### 다른 사람의 풀이
---

<br>

### 유사 문제
---

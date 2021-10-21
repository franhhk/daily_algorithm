프로그래머스 : 가장 큰 수
===
### 링크
https://programmers.co.kr/learn/courses/30/lessons/42746
<br>

### 문제 설명
---
0 또는 양의 정수가 주어졌을 때, 정수를 이어 붙여 만들 수 있는 가장 큰 수를 알아내 주세요.

예를 들어, 주어진 정수가 [6, 10, 2]라면 [6102, 6210, 1062, 1026, 2610, 2106]를 만들 수 있고, 이중 가장 큰 수는 6210입니다.

0 또는 양의 정수가 담긴 배열 numbers가 매개변수로 주어질 때, 순서를 재배치하여 만들 수 있는 가장 큰 수를 문자열로 바꾸어 return 하도록 solution 함수를 작성해주세요.
<br>

### 제한 조건
---
- numbers의 길이는 1 이상 100,000 이하입니다.
- numbers의 원소는 0 이상 1,000 이하입니다.
- 정답이 너무 클 수 있으니 문자열로 바꾸어 return 합니다.

<br>

### 입출력 예
---
```
numbers	return
[6, 10, 2]	"6210"
[3, 30, 34, 5, 9]	"9534330"
```

### 나의 풀이
---
```js
function solution(numbers) {
    function compare(a, b, i) {
        if(a[i] === undefined || b[i] === undefined) {
            let candi1 = a + b,
                candi2 = b + a

            return +candi1 <= +candi2 ? 1: -1;
        }

        if(+a[i] === +b[i]) return compare(a, b, i+1)
        else if(+a[i] < +b[i]) return 1
        else return -1
    }

    numbers = numbers
        .map(el => '' + el)
        .sort((a,b) => compare(a, b, 0))
        .join('')

    return +numbers[0]? numbers: '0'
}
```

<br>

### 다른 사람의 풀이
---
- 별도의 함수를 사용하지 않고 스트링화된 값을 붙여서 1을 곱함으로써 int 형으로 변환하여 어떤 값이 큰지 비교해서 sort 합니다.

```js
function solution(numbers) {
    var answer = numbers.map(v=>v+'')
                        .sort((a,b) => (b+a)*1 - (a+b)*1)
                        .join('');

    return answer[0]==='0'?'0':answer;
}
```
- 이 풀이의 경우 '-'연산자로 인해 타입 변환이 일어납니다.
```js
function solution(numbers) {
    let answer = numbers.sort((a, b) => `${b}${a}` - `${a}${b}`).join('');
    return answer[0] === '0' ? '0' : answer;
}
```
<br>

### 유사 문제
---

프로그래머스 : 숫자 문자열과 영단어
===
### 링크
https://programmers.co.kr/learn/courses/30/lessons/81301

<br>

### 문제 설명
---
네오와 프로도가 숫자놀이를 하고 있습니다. 네오가 프로도에게 숫자를 건넬 때 일부 자릿수를 영단어로 바꾼 카드를 건네주면 프로도는 원래 숫자를 찾는 게임입니다.

다음은 숫자의 일부 자릿수를 영단어로 바꾸는 예시입니다.

1478 → "one4seveneight"
234567 → "23four5six7"
10203 → "1zerotwozero3"
이렇게 숫자의 일부 자릿수가 영단어로 바뀌어졌거나, 혹은 바뀌지 않고 그대로인 문자열 s가 매개변수로 주어집니다. s가 의미하는 원래 숫자를 return 하도록 solution 함수를 완성해주세요.
<br>

### 제한 조건
---
- 1 ≤ s의 길이 ≤ 50
- s가 "zero" 또는 "0"으로 시작하는 경우는 주어지지 않습니다.
- return 값이 1 이상 2,000,000,000 이하의 정수가 되는 올바른 입력만 s로 주어집니다.

<br>


### 나의 풀이
---
- 처음엔 단순하게 이중포문으로 문제를 풀었는데, 1개의 테스트 케이스가 통과가 되지 않아 다른 방법을 찾았다
- 's.replaceAll is not a function' 에러를 해결하기 위해 replace 메소드를 정규식을 사용해서 풀었다.
- 정규식의 세계에 눈을 뜨게 해준 문제다. 재밌다!
- 주석처리한 부분의 풀이를 사용하면 정규식이 문자열 타입이기 때문에 문제가 풀리지 않는다. 참고로 정규 표현식은 문자열에 나타는 특정 문자 조합과 대응시키기 위해 사용되는 패턴으로 자바스크립트에서 **정규 표현식은 객체이다**. 

```js
function solution(s) {
    s = s.replace(/zero/g, '0');
    s = s.replace(/one/g, '1');
    s = s.replace(/two/g, '2');
    s = s.replace(/three/g, '3');
    s = s.replace(/four/g, '4');
    s = s.replace(/five/g, '5');
    s = s.replace(/six/g, '6');
    s = s.replace(/seven/g, '7');
    s = s.replace(/eight/g, '8');
    s = s.replace(/nine/g, '9');
    
//     let numbers = ['zero', 'one', 'two', 'three', 'four', 'five', 'six', 'seven', 'eight', 'nine'];
    
//     for(let el of numbers) {
//         s = s.replace('/' + el + '/g', String(numbers.indexOf(el)))
//     }
    
    return Number(s);
}
```

<br>

### 다른 사람의 풀이
---
- split 코앞까지 가서 이 방법을 생각해내지 못했다는 게 분하다!
- 이 문제를 통해 정규표현식에 대해 더 공부할 수 있어서 좋았지만, 다시 푼다면 다음과 같은 풀이를 생각해내고 싶다.

```js
function solution(s) {
    let numbers = ["zero", "one", "two", "three", "four", "five", "six", "seven", "eight", "nine"];
    var answer = s;

    for(let i=0; i< numbers.length; i++) {
        let arr = answer.split(numbers[i]);
        answer = arr.join(i);
    }

    return Number(answer);
}
```

<br>

### 유사 문제
---

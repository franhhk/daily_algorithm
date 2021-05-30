프로그래머스 : 소수 
===
### 링크
https://programmers.co.kr/learn/courses/30/lessons/42839

<br>

### 문제 설명
---
한자리 숫자가 적힌 종이 조각이 흩어져있습니다. 흩어진 종이 조각을 붙여 소수를 몇 개 만들 수 있는지 알아내려 합니다.

각 종이 조각에 적힌 숫자가 적힌 문자열 numbers가 주어졌을 때, 종이 조각으로 만들 수 있는 소수가 몇 개인지 return 하도록 solution 함수를 완성해주세요.

<br>

### 제한 조건
---
- numbers는 길이 1 이상 7 이하인 문자열입니다.
- numbers는 0~9까지 숫자만으로 이루어져 있습니다.
- "013"은 0, 1, 3 숫자가 적힌 종이 조각이 흩어져있다는 의미입니다.

<br>

### 나의 풀이
---
- 이중포문을 쓰는 대신 filter 메소드를 쓴 부분이 나름 뿌듯하다
- Math.sqrt()를 사용해 소수 여부를 확인하는 코드의 시간복잡도를 줄이는 부분을 알고 있었으나 사용하지 않았다,, 반성,,
- Set가 배열이 아닌 set객체를 반환한다는 것 주의!

```js
function solution(numbers) {
    var answer = 0;
    numbers = numbers.split('')
    let result = []
    
    function rec(number, remains) {
        if(remains.length === 0) { return; }

        for(let idx=0; idx<remains.length; idx++) {
            let newNumber = number + remains[idx]
            result.push(Number(newNumber))
            
            let remainsCopy = [...remains]
            remainsCopy.splice(idx, 1)
            rec(newNumber, remainsCopy)
        }
    }
    
    rec('', numbers)
    
    const resultSet = new Set(result)
    result = []
    for(let el of resultSet) {
        result.push(el)
    }
    
    answer = result.filter(el => {
        if(el <= 1) { return false; }
        if(el === 2) { return true; }
        for(let i=2; i<el; i++) {
            if(el % i === 0) { return false; }
        }
        return true;
    }).length
    
    return answer;
}
```
<br>

### 다른 사람의 풀이
---
- Set에 add등의 메소드를 활용한 점이 인상적이었다. 그 밖에도 delete, clear, size 등의 유용한 메소드가 있다.

```js
function solution(numbers) {
    var answer = 0;

    var n = numbers.split('');
    var nums = new Set()
    combi(n,'');

    function combi(a, s) {
        if (s.length > 0) {
            if (nums.has(Number(s))=== false) {
                nums.add(Number(s));
                if (chkPrime(Number(s))) {

                    answer++;
                }
            }
        }
        if (a.length > 0) {
            for (var i = 0; i< a.length; i++) {
                var t = a.slice(0)
                t.splice(i,1);
                combi(t,s + a[i]);
            }
        }
    }

    function chkPrime(num) {
        if (num < 2) return false;
        if (num === 2) return true;
        for (var i = 2; i <= Math.sqrt(num); i++) {
            if (num%i===0) return false;
        }
        return true;
    }

    return answer;
}
```

<br>

### 유사 문제
---

<br>

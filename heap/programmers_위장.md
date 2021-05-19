프로그래머스 : 위장
===
### 링크
https://programmers.co.kr/learn/courses/30/lessons/42578

<br>

### 문제 설명
---
스파이들은 매일 다른 옷을 조합하여 입어 자신을 위장합니다.

예를 들어 스파이가 가진 옷이 아래와 같고 오늘 스파이가 동그란 안경, 긴 코트, 파란색 티셔츠를 입었다면 다음날은 청바지를 추가로 입거나 동그란 안경 대신 검정 선글라스를 착용하거나 해야 합니다.
```
종류	이름
얼굴	동그란 안경, 검정 선글라스
상의	파란색 티셔츠
하의	청바지
겉옷	긴 코트
```
스파이가 가진 의상들이 담긴 2차원 배열 clothes가 주어질 때 서로 다른 옷의 조합의 수를 return 하도록 solution 함수를 작성해주세요.



<br>

### 제한 조건
---
- clothes의 각 행은 [의상의 이름, 의상의 종류]로 이루어져 있습니다.
- 스파이가 가진 의상의 수는 1개 이상 30개 이하입니다.
- 같은 이름을 가진 의상은 존재하지 않습니다.
- clothes의 모든 원소는 문자열로 이루어져 있습니다.
- 모든 문자열의 길이는 1 이상 20 이하인 자연수이고 알파벳 소문자 또는 '_' 로만 이루어져 있습니다.
- 스파이는 하루에 최소 한 개의 의상은 입습니다.
<br>


### 나의 풀이
---
- 문제를 처음 봤을 때는 멱집합 문제라고 생각해서 그 방법으로 풀었으나, 테스트 케이스에서 1개가 통과되지 않아 시간을 줄이고자 다른 방법을 생각해보게 되었다.
- 문제에서 경우의 수를 요구하고 있다보니 각각의 경우를 굳이 구하지 않아도 된다는 것을 깨닫고 코드를 수정했다.
- 간단한 문제를 복잡하게 접근했지만 이참에 멱집합 코드를 복습할 수 있어서 좋았다. 
<br>

```js
//초기 코드

function solution(clothes) {
    var answer = 1;
    let obj = {}
    
    for(let el of clothes) {
        obj[el[1]]? obj[el[1]].push(el[0]): obj[el[1]] = [el[0]];
    }
    
    let keys = Object.keys(obj)
    const powerSet = (idx, list) => {
         //탈출 조건
         if(idx === keys.length) {
             answer++
             return;
         }
        
         //idx요소 미포함
         powerSet(idx + 1, list)
        
         //idx요소 포함
         for(let clothing of obj[keys[idx]]) {
             powerSet(idx + 1, [...list, clothing])
         }
     }
    
     powerSet(0, [])
    
    return answer - 1;
}
```

아래는 최종 테스트를 통과한 코드이다.
```js
// 최종 코드

function solution(clothes) {
    var answer = 1;
    let obj = {}
    
    for(let el of clothes) {
        obj[el[1]]? obj[el[1]].push(el[0]): obj[el[1]] = [el[0]];
    }
    
    for(let key in obj) {
        answer = answer * (obj[key].length + 1)
    }
    
    return answer - 1;
}
```
<br>

### 다른 사람의 풀이
---
- 옷의 종류에 해당하는 요소들도 배열로 정리할 필요가 없었다
- 불필요한 코드를 작성하지 않는 연습이 필요하다고 느꼈다

```js
function solution(clothes) {
    return Object.values(clothes.reduce((obj, t)=> {
        obj[t[1]] = obj[t[1]] ? obj[t[1]] + 1 : 1;
        return obj;
    } , {})).reduce((a,b)=> a*(b+1), 1)-1;    
}
```

<br>

### 유사 문제
---
- 코드스테이츠 / Data Structure & Algorithm_20 집밥이 그리워
: 조금만 수정하면 충분히 멱집합을 구하는 문제가 될 수 있으므로 그와 유사한 문제를 달아놓는다.

<br>

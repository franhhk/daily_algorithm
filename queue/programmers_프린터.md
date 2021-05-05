프로그래머스 : 프린터
===
### 링크
https://programmers.co.kr/learn/courses/30/lessons/42587

<br>

### 문제 설명
---
일반적인 프린터는 인쇄 요청이 들어온 순서대로 인쇄합니다. 그렇기 때문에 중요한 문서가 나중에 인쇄될 수 있습니다. 이런 문제를 보완하기 위해 중요도가 높은 문서를 먼저 인쇄하는 프린터를 개발했습니다. 이 새롭게 개발한 프린터는 아래와 같은 방식으로 인쇄 작업을 수행합니다.
```
1. 인쇄 대기목록의 가장 앞에 있는 문서(J)를 대기목록에서 꺼냅니다.
2. 나머지 인쇄 대기목록에서 J보다 중요도가 높은 문서가 한 개라도 존재하면 J를 대기목록의 가장 마지막에 넣습니다.
3. 그렇지 않으면 J를 인쇄합니다.
예를 들어, 4개의 문서(A, B, C, D)가 순서대로 인쇄 대기목록에 있고 중요도가 2 1 3 2 라면 C D A B 순으로 인쇄하게 됩니다.
```
내가 인쇄를 요청한 문서가 몇 번째로 인쇄되는지 알고 싶습니다. 위의 예에서 C는 1번째로, A는 3번째로 인쇄됩니다.

현재 대기목록에 있는 문서의 중요도가 순서대로 담긴 배열 priorities와 내가 인쇄를 요청한 문서가 현재 대기목록의 어떤 위치에 있는지를 알려주는 location이 매개변수로 주어질 때, 내가 인쇄를 요청한 문서가 몇 번째로 인쇄되는지 return 하도록 solution 함수를 작성해주세요.

<br>

### 제한 조건
---
현재 대기목록에는 1개 이상 100개 이하의 문서가 있습니다.
인쇄 작업의 중요도는 1~9로 표현하며 숫자가 클수록 중요하다는 뜻입니다.
location은 0 이상 (현재 대기목록에 있는 작업 수 - 1) 이하의 값을 가지며 대기목록의 가장 앞에 있으면 0, 두 번째에 있으면 1로 표현합니다.

<br>


### 나의 풀이
---

- 리스트 객체에 각 프린트의 첫 위치와 중요도 정보를 저장한다
- queue에 순서대로 프린트를 넣고 node에 하나씩 shift해서 빼낸다
- list에 있는 다른 값 중에 node의 중요도보다 높은 값이 있으면 queue에 다시 푸쉬하고, 그렇지 않으면 result에 푸쉬하고 list에서 해당 키를 삭제한다
- 중요한 문서를 처리한 후에 남은 문서들의 순서를 고려하는 부분에서 고민을 많이 했다

<br>

```js
function solution(priorities, location) {
    var answer = 0;
    let list = {}
    
    for(let i = 0; i < priorities.length; i++) {
        list[i] = priorities[i] 
    }
    
    let queue = [...Object.keys(list)]
    let result = []
    let node;
    
    while(queue.length !== 0) {
        node = queue.shift()
        let isMax = false 
        
        for(let key in list) {
            if(list[key] > list[node]) {
                isMax = true
                break;
            }
        }
        if(isMax) {
            queue.push(node)
        } else {
            result.push(node)
            delete list[node]
        }
    }
        
    for(let num of result) {
        if(Number(num) === location) {
            answer = result.indexOf(num) + 1
            break;
        }
    }
    
    return answer;
}
```
<br>

### 다른 사람의 풀이
---
원리는 비슷하지만 배운 것이 많다. 역시 다른 사람의 코드를 보는 게 가장 공부가 잘 되는 것 같다.
- array.some 메소드를 처음 봤다
- array.map 메소드의 인덱스 인자를 잘 활용하는 법을 배워야겠다
- 카운트를 이용해 불필요한 연산을 하지 않은 것이 인상깊었다

```js
function solution(priorities, location) {
    var list = priorities.map((t,i)=>({
        my : i === location,
        val : t
    }));
    var count = 0;        
    while(true){
        var cur = list.shift();        
        if(list.some(t=> t.val > cur.val )){
            list.push(cur);                        
        }
        else{            
            count++;
            if(cur.my) return count;
        }
    }
}
```
<br>

### 유사 문제
---
- 프로그래머스 / 다리를 지나는 트럭
- 코드스테이츠 / Data Structure & Algorithm_05_프린터

<br>

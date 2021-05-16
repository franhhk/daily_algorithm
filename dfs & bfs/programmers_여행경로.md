프로그래머스 : 여행 경로
===
### 링크
https://programmers.co.kr/learn/courses/30/lessons/43164

<br>

### 문제 설명
---
주어진 항공권을 모두 이용하여 여행경로를 짜려고 합니다. 항상 "ICN" 공항에서 출발합니다.

항공권 정보가 담긴 2차원 배열 tickets가 매개변수로 주어질 때, 방문하는 공항 경로를 배열에 담아 return 하도록 solution 함수를 작성해주세요.

<br>

### 제한 조건
---
- 모든 공항은 알파벳 대문자 3글자로 이루어집니다.
- 주어진 공항 수는 3개 이상 10,000개 이하입니다.
- tickets의 각 행 [a, b]는 a 공항에서 b 공항으로 가는 항공권이 있다는 의미입니다.
- 주어진 항공권은 모두 사용해야 합니다.
- 만일 가능한 경로가 2개 이상일 경우 알파벳 순서가 앞서는 경로를 return 합니다.
- 모든 도시를 방문할 수 없는 경우는 주어지지 않습니다.
<br>


### 나의 풀이
---
처음에는 다음과 같은 코드를 짰다. 이렇게 했을 때 테스트 케이스 2개가 통과가 되지 않아서 고생을 했는데, 반례를 찾고 코드의 문제점을 발견했다.

반례)
tickets = [['ICN','B'],['B','ICN'],['ICN','A'],['A','D'],['D','A']]
answer = ['ICN', 'B', 'ICN', 'A', 'D', 'A']

위와 같은 경우 sort때문에 인천에서 A공항으로 이동하지만 그랬을 경우 여행 경로가 마무리되지 않는다(= tickets.length가 0이 되는 경우가 생기지 않는다.) 따라서 가능한 여행 경로를 전부 구한 후 이를 sort한 뒤 첫번째 요소를 반환해야겠다는 생각을 하게 되었다.

<br>

```js
//초기의 코드

function solution(tickets) {
    var answer = [];
    let node = 'ICN';
    
    // tickets.sort((a,b) => {
    //     if(a[0] === b[0] && a[1] < b[1]) {
    //         return -1
    //     } else if(a[0] === b[0] && a[1] > b[1]){
    //         return 1
    //     } else {
    //         return 0
    //     }
    // })
    // --> no need to do this
    tickets.sort()
    
    answer.push(node);
    
    while(tickets.length) {
        for(let i = 0; i < tickets.length; i++) {
            if(tickets[i][0] === node) {
                node = tickets.splice(i, 1)[0][1] 
                answer.push(node)
                break;
            }
        }
    }
    return answer;
}
 
```
따라서 다음과 같이 코드를 수정했다
```js
//최종 코드
function solution(tickets) {
    var answer = [];
    
    function findPath(path, node, tickets) {
        let newPath = path.slice()
        newPath.push(node)
        
        if(tickets.length === 0) {
            answer.push(newPath)
        }
        
        for(let i = 0; i < tickets.length; i++) {
            if(tickets[i][0] === node) {
                let remains  = tickets.slice()
                let newNode = remains.splice(i, 1)[0][1]
                findPath(newPath, newNode, remains);
            }
        }
    }
    
    findPath([], "ICN", tickets);
    
    return answer.sort()[0];
}
```
<br>

### 다른 사람의 풀이
---
- 나와 풀이가 거의 비슷하지만 tickets.map()을 사용했다는 점이 인상적이다.

```js
function solution(tickets) {
    var answer = [];
    const DFS = (airport, tickets, path) => {
        let newPath = [...path, airport]
        if(tickets.length === 0) {
            answer.push(newPath)
        } else {
            tickets.map((ticket, idx) => {
                if(ticket[0] === airport) {
                    let copiedTickets = [...tickets]
                    let [[from, to]] = copiedTickets.splice(idx, 1)
                    DFS(to, copiedTickets, newPath)
                }
            })
        }
    }
    DFS('ICN', tickets, [])
    return answer.sort()[0];
}
```

<br>

### 유사 문제
---

<br>

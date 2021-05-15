프로그래머스 : 단어 변환
===
### 링크
https://programmers.co.kr/learn/courses/30/lessons/43163

<br>

### 문제 설명
---
두 개의 단어 begin, target과 단어의 집합 words가 있습니다. 아래와 같은 규칙을 이용하여 begin에서 target으로 변환하는 가장 짧은 변환 과정을 찾으려고 합니다.

1. 한 번에 한 개의 알파벳만 바꿀 수 있습니다.
2. words에 있는 단어로만 변환할 수 있습니다.

예를 들어 begin이 "hit", target가 "cog", words가 ["hot","dot","dog","lot","log","cog"]라면 "hit" -> "hot" -> "dot" -> "dog" -> "cog"와 같이 4단계를 거쳐 변환할 수 있습니다.

두 개의 단어 begin, target과 단어의 집합 words가 매개변수로 주어질 때, 최소 몇 단계의 과정을 거쳐 begin을 target으로 변환할 수 있는지 return 하도록 solution 함수를 작성해주세요.


<br>

### 제한 조건
---
- 각 단어는 알파벳 소문자로만 이루어져 있습니다.
- 각 단어의 길이는 3 이상 10 이하이며 모든 단어의 길이는 같습니다.
- words에는 3개 이상 50개 이하의 단어가 있으며 중복되는 단어는 없습니다.
- begin과 target은 같지 않습니다.
- 변환할 수 없는 경우에는 0를 return 합니다.
<br>


### 나의 풀이
---
- while문을 순회할 때마다 우선 target으로 전환할 수 있는지 확인해보는 것이 포인트다.
- 더 깔끔하게 쓸 방법이 있을 것 같기는 하지만 우선 이렇게 보는 게 편해서 놔두기로 했다.
<br>

```js
function solution(begin, target, words) {
    var answer = 0;
    let queue = [...words]
    let node = begin
    
    while(words.includes(target)) {
        //target으로 전활 할 수 있나?
        let count = 0;
        for(let j = 0; j < node.length; j++) {
            if(node[j] === target[j]) {
                count++
            }
        }
        if(count === node.length - 1) {
            answer++
            return answer;
        }
        
        //target으로 전활할 수 없네?
        let comp = queue.shift()
        count = 0;
        for(let i = 0; i < node.length; i++) {
            if(node[i] === comp[i]) {
                count++
            }
        }
        if(count === node.length - 1) {
            answer++
            node = comp
        } else {
            queue.push(comp)
        }
    }
    return answer;
}
```
<br>

### 다른 사람의 풀이
---
dfs/bfs 문제 특성상 node의 방문 여부를 체크하는 경우가 많았는데, 나는 여기서는 굳이 이를 boolean값으로 표시할 필요가 없다고 느꼈다. 나는 방문 후 node에 재할당이 이뤄지지 않으면 queue에 다시 push, 그렇지 않으면 shift메소드로 queue에서 제거하는 방식으로 방문 여부를 확인했다.

```js
function solution(begin, target, words) {
    const queue = [begin];
    const visitArr = new Array(words.length).fill(false);
    let ctr = 0;
    let shiftedWord = begin;
    let queueLeng = 1;

    while(queue.length > 0) {
        shiftedWord = queue.shift();
        queueLeng--;

        for(let i in words) {            
            if(check(shiftedWord, words[i])) {
                if(visitArr[i] == true) 
                    continue;

                if(words[i] == target)
                    return ctr+1;

                visitArr[i] = true;
                queue.push(words[i]);
            }
        }

        if(queueLeng == 0) {
            ctr++;
            queueLeng = queue.length;
        }
    }
    return 0;

    function check(standard, word) {
        let diffCtr = 0;

        if(standard.length != word.length) 
            return false;

        for(let i=0; i<standard.length; i++) {
            if(standard.charAt(i) != word.charAt(i))
                diffCtr++;
            if(diffCtr > 1)
                return false;
        }
        return true;
    }
}
```

<br>

### 유사 문제
---

<br>

코드스테이츠 : (토이 12번) treeBFS
===
### 링크
https://urclass.codestates.com/codeproblem/b48664f6-524d-4d91-bfa4-d42c7f4c3f44

<br>

### 문제 설명
---
임의의 tree를 구성하는 노드 중 하나의 Node 객체를 입력받아, 해당 노드를 시작으로 너비 우선 탐색(BFS, Breadth First Search)을 합니다. 이 때, 탐색되는 순서대로 노드의 값이 저장된 배열을 리턴해야 합니다.

<br>

### 주의사항
---
생성자 함수(Node)와 메소드(addChild)는 변경하지 않아야 합니다.

<br>


### 나의 풀이
---
- 넓이 우선 탐색이라는 거! (아직 나는 깊이 우선 탐색이 더 익숙한가 보다)

<br>

```js
let bfs = function (node) {
  let result = []
  let queue = [node]

  while(queue.length !== 0) {
    node = queue.shift()
    result.push(node.value)
    node.children.forEach(el => queue.push(el))
  }

  return result;
};

// 이 아래 코드는 변경하지 않아도 됩니다. 자유롭게 참고하세요.
let Node = function (value) {
  this.value = value;
  this.children = [];
};

// 위 Node 객체로 구성되는 트리는 매우 단순한 형태의 트리입니다.
// membership check(중복 확인)를 따로 하지 않습니다.
Node.prototype.addChild = function (child) {
  this.children.push(child);
  return child;
};
```
<br>

### Reference Code
---
- 내 풀이와 원리는 같다

```js
let bfs = function (node) {
  // TODO: 여기에 코드를 작성합니다.
  let queue = [node];
  const values = [];
  while (queue.length > 0) {
    const head = queue[0];
    queue = queue.slice(1);

    values.push(head.value);

    head.children.forEach((child) => queue.push(child));
  }
  return values;
};

// 이 아래 코드는 변경하지 않아도 됩니다. 자유롭게 참고하세요.
let Node = function (value) {
  this.value = value;
  this.children = [];
};

// 위 Node 객체로 구성되는 트리는 매우 단순한 형태의 트리입니다.
// membership check(중복 확인)를 따로 하지 않습니다.
Node.prototype.addChild = function (child) {
  this.children.push(child);
  return child;
};
```
<br>

### 유사 문제
---

<br>

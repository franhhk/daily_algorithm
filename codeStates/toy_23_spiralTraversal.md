코드스테이츠 : (토이 23번) spiralTraversal
===
### 링크
https://urclass.codestates.com/codeproblem/a642de1d-c2b0-4ea7-b205-58a8224c0a74

<br>

### 문제 설명
---2차원 M x N 배열을 나선형(spiral)으로 순회해야 합니다.

<br>

### 입력
---
- 세로 길이(matrix.length)가 M, 가로 길이(matrix[i].length)가 N인 2차원 배열
- matrix[i]는 string 타입을 요소로 갖는 배열
- matrix[i][j].length는 1

<br>

### 출력
---
string 타입을 리턴해야 합니다.

<br>

### 주의사항
---
순회는 좌측 상단 (0,0)에서 시작합니다.
배열의 모든 요소를 순서대로 이어붙인 문자열을 리턴해야 합니다.

<br>

### 나의 풀이
---
- Array.reverse() 메소드가 원본을 수정한다는 점이 주의할 포인트였다
- 여러차례 for문을 도는 대신 join을 사용했다

<br>

```js
const spiralTraversal = function (matrix) {
  // Careful: reverse is destructive -- it changes the original array.

  let rowDir = 'right', colDir = 'down';
  let dir = 'row';
  let answer = '';

  while(matrix.length) {
    if(dir === 'row') {
      if(rowDir === 'right') {
        answer = answer + matrix.shift().join('')
        rowDir = 'left'
      } else if(rowDir === 'left') {
        answer = answer + matrix.pop().reverse().join('')
        rowDir = 'right'
      }
      dir = 'col'
    } else if(dir === 'col') {
      if(colDir === 'down') {
        for(let el of matrix) {
          answer = answer + el.pop()
        }
        colDir = 'up'
      } else if(colDir === 'up') {
        for(let el of matrix.reverse()) {
          answer = answer + el.shift()
        }
        matrix.reverse()
        colDir = 'down'
      }
      dir = 'row'
    }
  }

  return answer;
};

```

<br>

### Reference Code
---

```js
const spiralTraversal = function (matrix) {
  // 각 방향마다 row와 col의 변화를 저장
  const RIGHT = [0, 1];
  const DOWN = [1, 0];
  const LEFT = [0, -1];
  const UP = [-1, 0];
  // 각 방향을 위한 lookup table
  const MOVES = [RIGHT, DOWN, LEFT, UP];
  const M = matrix.length;
  const N = matrix[0].length;
  const isValid = (row, col) => row >= 0 && row < M && col >= 0 && col < N;

  let cnt = 0;
  let row = 0,
    col = -1;
  let direction = 0;
  let result = '';
  while (cnt < M * N) {
    const move = MOVES[direction];
    const [rd, cd] = move;

    row = row + rd;
    col = col + cd;
    while (isValid(row, col) && matrix[row][col] !== false) {
      result = result + matrix[row][col];
      // 한 요소를 두 번 접근하지 않게 하기 위해서, 접근된 요소를 false로 변경한다.
      matrix[row][col] = false;
      row = row + rd;
      col = col + cd;
      cnt++;
    }
    // row, col 이 행렬의 범위를 벗어났기 때문에,
    // 진행된 방향의 반대로 한 칸 이동한다.
    row = row - rd;
    col = col - cd;

    // 각 방향이 순환되기 때문에 모듈러 연산을 사용한다.
    direction = (direction + 1) % 4;
  }
  return result;
};
```

<br>

### 유사 문제
---

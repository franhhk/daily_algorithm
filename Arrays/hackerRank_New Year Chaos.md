해커랭크 : New Year Chaos
===
### 링크
https://www.hackerrank.com/challenges/new-year-chaos/problem?h_l=interview&playlist_slugs%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D=arrays&h_r=next-challenge&h_v=zen

<br>

### 문제 설명
---
It is New Year's Day and people are in line for the Wonderland rollercoaster ride. Each person wears a sticker indicating their initial position in the queue from  to . Any person can bribe the person directly in front of them to swap positions, but they still wear their original sticker. One person can bribe at most two others.

Determine the minimum number of bribes that took place to get to a given queue order. Print the number of bribes, or, if anyone has bribed more than two people, print Too chaotic.

#### Example


If person  bribes person , the queue will look like this: . Only  bribe is required. Print 1.


Person  had to bribe  people to get to the current position. Print Too chaotic.

#### Function Description

Complete the function minimumBribes in the editor below.

minimumBribes has the following parameter(s):

- int q[n]: the positions of the people after all bribes
#### Returns

No value is returned. Print the minimum number of bribes necessary or Too chaotic if someone has bribed more than  people.
#### Input Format

The first line contains an integer , the number of test cases.

Each of the next  pairs of lines are as follows:
- The first line contains an integer , the number of people in the queue
- The second line has  space-separated integers describing the final state of the queue.

#### Constraints
- 1 <= t <= 10
- 1 <= n <= 10^5
#### Subtasks

For 60% score 1 <= n <= 10^3
For 100% score 1 <= n <= 10^5

#### Sample Input

STDIN       Function
-----       --------
2           t = 2
5           n = 5
2 1 5 3 4   q = [2, 1, 5, 3, 4]
5           n = 5
2 5 1 3 4   q = [2, 5, 1, 3, 4]
#### Sample Output

3
Too chaotic
<br>

### 나의 풀이
---
- 점수 100%를 얻기 위해서는 시간 복잡도를 O(NlogN)이하로 내려야한다는 걸 알고 있었다. 하지만 방법이 생각나지 않아서 우선은 O(N^2)로 풀었다.

<br>

```js
//풀이 (1)
function minimumBribes(q) {
    let bribes = 0;
    let i = 0;
    let shifts = 0;
    let isFinished = Array(q.length).fill(false)
        
    while(isFinished.includes(false)) {
        if(i === q.length) {
            i = 0;
        }
        if(shifts > 2) {
            console.log('Too chaotic');
            return;
        }
        
        if(q[i] > q[i+1]) {
            shifts++;
            let removed = q.splice(i, 1)
            q.splice(i+1, 0, ...removed)
        } else {
            if(q[i] === i+1) {
                isFinished[i] = true;
            }
            bribes += shifts;
            shifts = 0;
        }
        i++
    }
    
    if(bribes > 0) {
        console.log(bribes);
    }
}
```
- 예상대로 테스트 케이스는 통과했지만 submit을 했을 때 time limit을 넘기는 경우가 발생했다.
- 따라서 O(N)의 시간복잡도를 가지는 Array.includes 메소드를 대체할 방법을 생각했다.
- while문의 조건으로 들어가야하기 때문에 불리언 값으로 q가 원래의 상태로 돌아갔는지 확인하는 건 어려웠다.
- 따라서 제자리에 맞게 돌아간 사람들의 수를 세기로 했다.
```js
//풀이 (2)
function minimumBribes(q) {
    let bribes = 0;
    let i = 0;
    let shifts = 0;
    let inPlace= 0;
        
    while(inPlace !== q.length) {
        if(i === q.length) {
            i = 0;
            inPlace = 0;
        }
        if(shifts > 2) {
            console.log('Too chaotic');
            return;
        }
        
        if(q[i] > q[i+1]) {
            shifts++;
            let removed = q.splice(i, 1)
            q.splice(i+1, 0, ...removed)
        } else {
            if(q[i] === i+1) {
                inPlace++;
            }
            bribes += shifts;
            shifts = 0;
        }
        i++
    }
    
    if(bribes > 0) {
        console.log(bribes);
        return;
    }
}
```
- 그럼에도 타임아웃 에러가 났다
- 결국 인터넷을 참고해 다음과 같이 풀었다
```js
function minimumBribes(q) {
    q.unshift(0);
    
    let num = 0
    let chaotic = false
    for (let i = q.length - 1; i >= 0; i--) {
        if (q[i] - i > 2) chaotic = true
        for (let j = q[i] - 1; j < i; j++) {
            if (q[j] > q[i]) num++
        }
    }
    if (chaotic) console.log("Too chaotic")
    else console.log(num)
}
```
<br>

### 유사 문제
---

<br>

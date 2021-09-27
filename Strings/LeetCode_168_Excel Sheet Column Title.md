168 . Excel Sheet Column Title
===
### Company
`Facebook`,
`Zenefits`,
`Microsoft`

### Tags
`String`, `Simulation`

### 문제 설명
---
#### Description
Given an integer columnNumber, return its corresponding column title as it appears in an Excel sheet.

For example:

A -> 1
B -> 2
C -> 3
...
Z -> 26
AA -> 27
AB -> 28 
...

#### Example
Example 1:
```
Input: columnNumber = 1
Output: "A"
```
Example 2:
```
Input: columnNumber = 28
Output: "AB"
```
Example 3:
```
Input: columnNumber = 701
Output: "ZY"
```
Example 4:
```
Input: columnNumber = 2147483647
Output: "FXSHRXW"
```

#### Constraints:

1 <= columnNumber <= 2^31 - 1
<br>

### 나의 풀이
---
- 26으로 나누어 떨어지는 경우를 대비해 columnNumber에서 1씩 뺀 후 계산하는 것이 중요하다.
<br>

```js
// Solution (1)

/**
 * @param {number} columnNumber
 * @return {string}
 */
var convertToTitle = function(columnNumber) {
    let alphabets = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ';
    let answer = '';
    
    while(columnNumber > 0) {
        columnNumber--;
          
        let idx = columnNumber % 26
        answer = alphabets[idx] + answer;
  
        columnNumber = ~~(columnNumber / 26)
    }
    
    return answer;
};
```
- String.fromCharCode를 사용해 풀었을 때 index를 이용해 알파벳을 찾는 것보다 소요되는 시간이 훨씬 줄어든다.
```js
// Solution (2)

/**
 * @param {number} columnNumber
 * @return {string}
 */
var convertToTitle = function(columnNumber) {
    let answer = '';
    
    while(columnNumber > 0) {
        columnNumber--
          
        let idx = columnNumber % 26
        answer = String.fromCharCode(65 + idx) + answer;
          columnNumber = ~~(columnNumber / 26)
    }
    
    return answer;
};
```
<br>

### 다른 사람 풀이
---

```js
var convertToTitle = function(n) {
    let title = '';
    
    while(n > 0) {
        n--;
        
			  title = String.fromCharCode(65 + (n % 26)) + title;
        
        n = parseInt(n / 26);
    }
    
		return title;
};
```
<br>

### Record
---
Solution (1)
- Runtime: 72 ms, faster than 66.74% of JavaScript online submissions for Excel Sheet Column Title.
- Memory Usage: 38.7 MB, less than 45.40% of JavaScript online submissions for Excel Sheet Column Title.

Solution (2)
- Runtime: 60 ms, faster than 98.54% of JavaScript online submissions for Excel Sheet Column Title.
- Memory Usage: 38.6 MB, less than 57.11% of JavaScript online submissions for Excel Sheet Column Title.

#### Level
`easy`

<br>

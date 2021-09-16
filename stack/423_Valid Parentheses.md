423 · Valid Parentheses
===
### Company
`Microsoft`, `Facebook`, `Amazon`, `Google`, `Twitter`, `Airbnb`, `Zenefits`, `Bloomberg`, `Uber`

### Tags
`Stack`, `String`

### 문제 설명
---
#### Description
Given a string containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

The brackets must close in the correct order, "()" and "()[]{}" are all valid but "(]" and "([)]" are not.

#### Example
Example 1:
```
Input: "([)]"
Output: False
```
Example 2:
```
Input: "()[]{}"
Output: True
```

#### Challenge
Use O(n) time, n is the number of parentheses.

<br>

### 나의 풀이
---

```js
export class Solution {

  /**
   * isValidParentheses
   *
   * @param s: A string
   * @return: whether the string is a valid parentheses
   */
  isValidParentheses(s) {
    let stack = []

    for(let el of s) {
        if(el === '{' || el === '(' || el === '[') {
            stack.push(el)
        } else if(
            (el === '}' && stack[stack.length-1] === '{') ||
            (el === ')' && stack[stack.length-1] === '(') ||
            (el === ']' && stack[stack.length-1] === '[')
        ) {
            stack.pop();
        } else if(el === '}' || el === ')' || el === ']') {
            return false;
        }
    }

    return stack.length? false: true;
  }

}
```
<br>

### 다른 사람 풀이
---
- It occurred to me that using a hash would make the code seem cleaner.
```js
let map = {
  '}': '{',
  ')': '(',
  ']': '[',
}

=> if(stack[stack.length-1] === map[s[i]])
```
<br>

### Record
---
- `122 ms` time cost
- `9.04 MB` memory cost
- Your submission beats `89.14%` Submissions
- `easy`

<br>

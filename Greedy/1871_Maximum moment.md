1871 · Maximum moment
===
### Company
`Google`

### Tags
`Greedy`

### 문제 설명
---
#### Description
Give you a 24-hour time (00: 00-23: 59), where one or more numbers of the four numbers are question marks. Question mark can be replaced with any number, then what is the maximum time you can represent.

#### Example
Example 1:
```
Input: 
time = "2?:00"
Output: 
"23:00"
```
Example 2:
```
Input: 
time = "??:??"
Output: 
"23:59"
```

<br>

### 나의 풀이
---
- 예외사항을 잘 생각해서 걸러야 한다!
```js
export class Solution {

  /**
   * MaximumMoment
   *
   * @param time: a string of Time
   * @return: The MaximumMoment
   */
  MaximumMoment(time) {
    let answer = ""
    let [hour, min] = time.split(':')
    
    if(hour[0] === '?') {
        answer += hour[1] === '?' || +hour[1] < 4? '2': '1'
    } else {
        answer += hour[0]
    }
    if(hour[1] === '?') {
        answer += +answer[0] < 2? '9': '3'
    } else {
        answer += hour[1]
    }
    answer += ':'
    answer += min[0] === '?'? '5': min[0]
    answer += min[1] === '?'? '9': min[1]

    return answer
  }

}
```
<br>

### 다른 사람 풀이
---

<br>

### Record
---
- `101 ms` time cost
- `8.85 MB` memory cost
- Your submission beats `100.00%` Submissions
- `easy`

<br>

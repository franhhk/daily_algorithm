코드스테이츠 : (네특심 9번) commonCharacters
===
### 링크
https://urclass.codestates.com/codeproblem/3d5c7dcc-0112-4cc7-83b6-5265e86e0574

<br>

### 문제 설명
---
Write a function f(a, b) which takes two strings as arguments and returns a string containing the characters found in both strings (without duplication), in the order that they appeared in a.
Remember to skip spaces and characters you have already encountered!

Example: commonCharacters('acexivou', 'aegihobu')
Returns: 'aeiou'

Extra credit: Extend your function to handle more than two input strings.

<br>

### 나의 풀이
---
<br>

```js
function commonCharacters(string1, ...strings) {
  //recursion
  strings = strings.reduce((a,c) => commonCharacters(a, c))

  //filter characters in the order they appear in string1
  return string1.split('').filter(el => strings.includes(el)).join('');
}
```
<br>

### 페어의 풀이
---
<br>

```js
function commonCharacters(...args) {
  let res=''
  for(let i=0;i<args[0].length;i++){
      let flag=true;
      for(let j=1;j<args.length;j++){
          if (args[j].indexOf(args[0][i])==-1){
              flag=false;
              break;
          }
      }
      if(flag){
          res+=args[0][i]
      }
  }
  return res
}
```
<br>

### Reference Code
---

```js
/* START SOLUTION */
// HELPER FUNCTIONS!
// Given two objects, intersection() uses reduce to create an object with only the common keys
const intersection = function (set1, set2) {
  return Object.keys(set1).reduce(function (out, val) {
    if (val in set2) { out[val] = true; }
    return out;
  }, {});
};
// Takes a string and makes an object with each  alphabetical character in the string represented by a key with the value 'true'
const objectify = function (string) {
  return string.split('').reduce(function (obj, char) {
     // this simple regex matches only alphabetical characters of either case
    if (char.match(/[a-z]/i)) { obj[char] = true; }
    return obj;
  }, {});
};
/* END SOLUTION */

function commonCharacters(string1, string2) {
  // TODO: Your code here!
  /* START SOLUTION */
  // Separate out multiple input strings
  let otherStrings = Array.prototype.slice.call(arguments, 1);

 // Use reduce to iterate over all collections of letters, narrowing down the pool of common characters.
 // Go look at the helper functions and figure out what they do!
  let common = otherStrings.reduce(function(obj, string) {
    obj = intersection(obj, objectify(string));
    return obj;
  }, objectify(string1)); // An object representing all characters in string1 is passed in as a starting value

  // use reduce to create a string representing all common chars in the order seen in string1, and return it!
  return string1.split('').reduce(function(result, char) {
    if (common[char]) { result += char; common[char] = false; }
    return result;
  }, '');
  /* END SOLUTION */
};
```
<br>

### 유사 문제
---

<br>

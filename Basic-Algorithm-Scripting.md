# split

**`split()`, `split("")`, and `split(" ")`**
: divides a `String` into an ordered list of substrings, puts these substrings into an array, and returns the array. 
[from mozilla](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/split)


| `str.split()` | `str.split('')` | `str.split(' ')` |
| ----------- | ----------- | ----------- |
| convert to array? | characters | words |
| copy whole? | output whitout space | output incuding space |

example of `const str = 'A dog';`
| `str.split()` | `str.split('')` | `str.split(' ')` |
| ----------- | ----------- | ----------- |
| ['A dog'] | ['A', 'dog']  | ["A", " ", "d", "o", "g"] |
| 0: 'A dog'| 0: 'A' <br /> 1: 'dog' | 0: "A"<br /> 1: " "<br /> 2: "d"<br /> 3: "o"<br /> 4: "g" |
| length: 1 | length: 2 | length: 5 |

- **`split` function looks better than `for` loop**
example [from freeCodeCamp](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures#basic-algorithm-scripting)
```
function reverseString(str) {
  return str
  .split("")
  .reverse()
  .join("");
}
reverseString("hello");
```
vs
```
function reverseString(str) {
  for (var reversedStr = "", i = str.length - 1; i >= 0; i--) {
    reversedStr += str[i];
  }
  return reversedStr;
}
reverseString("hello");
```
---

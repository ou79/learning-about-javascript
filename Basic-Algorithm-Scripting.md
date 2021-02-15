# split

## `split()`, `split("")`, and `split(" ")`

: divides a `String` into an ordered list of substrings, puts these substrings into an array, and returns the array. 
[@mozilla](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/split)

| `str.split()` | `str.split('')` | `str.split(' ')` |
| ----------- | ----------- | ----------- |
| convert to array? | characters | words |
| copy whole? | output whitout space | output incuding space |

### example of `const str = 'A dog'`

| `str.split()` | `str.split('')` | `str.split(' ')` |
| ----------- | ----------- | ----------- |
| ['A dog'] | ['A', 'dog']  | ["A", " ", "d", "o", "g"] |
| 0: 'A dog'| 0: 'A' <br /> 1: 'dog' | 0: "A"<br /> 1: " "<br /> 2: "d"<br /> 3: "o"<br /> 4: "g" |
| length: 1 | length: 2 | length: 5 |

### `split` function looks better than `for` loop

example [@freeCodeCamp](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures#basic-algorithm-scripting)

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

# Function.bind

## `Function.bind` 

: works just like `Math.max` but also has `Function.prototype.apply`'s ability to take arrays as its arguments [@freeCodeCamp](https://forum.freecodecamp.org/t/freecodecamp-challenge-guide-return-largest-numbers-in-arrays/16042). When being called, `Function.bind` has its `this` keyword set to the provided value, with a given sequence of arguments preceding any provided when the new function is called [@mozilla](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_objects/Function/bind).

### `bind` function looks cleaner

example [@freeCodeCamp](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures#basic-algorithm-scripting)

```
function largestOfFour(arr) {
  return arr.map(Function.apply.bind(Math.max, null));
}
```

- **need to know**

*pass a null as the 2nd param to `Function.prototype.apply.bind` which gives a context to the `Math.max` method.
*`Function.prototype.apply.bind(Math.max, null)` makes a new function accepting the `arr.map` values i.e. the inner arrays.

vs

```
function largestOfFour(arr) {
  return arr.map(function(group) {
    return group.reduce(function(prev, current) {
      return current > prev ? current : prev;
    });
  });
}
```



---

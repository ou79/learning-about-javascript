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

### `split` function compares to `for` loop

example [@freeCodeCamp](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures#basic-algorithm-scripting)

```
function reverseString(str) {
  return str
  .split("")
  .reverse()
  .join("");
}
reverseString("hello");
// expected output: `olleh`
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
// expected output: `olleh`
```

---

## `bind()`

: works just like `Math.max` but also has `Function.prototype.apply`'s ability to take arrays as its arguments [@freeCodeCamp](https://forum.freecodecamp.org/t/freecodecamp-challenge-guide-return-largest-numbers-in-arrays/16042). When being called, `Function.bind` has its `this` keyword set to the provided value, with a given sequence of arguments preceding any provided when the new function is called [@mozilla](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_objects/Function/bind).

### `bind` an new array of max numbers in each nested array 

example [@freeCodeCamp](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures#basic-algorithm-scripting)

```
function largestOfFour(arr) {
  return arr.map(Function.apply.bind(Math.max, null));
}

largestOfFour([[17, 23, 25, 12], [25, 7, 34, 48], [4, -10, 18, 21], [-72, -3, -17, -10]]);
// expected output: [25, 48, 21, -3]
```

### need to know

- about `this`
- pass a null as the 2nd param to `Function.prototype.apply.bind` which gives a context to the `Math.max` method.
- `Function.prototype.apply.bind(Math.max, null)` makes a new function accepting the `arr.map` values i.e. the inner arrays.

---

## `reduce()` vs `slice()`

### `reduce()`
: executes a reducer function (that you provide) on each element of the array, resulting in single output value [@mozilla](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce). 

- The `reduce()` method executes the callback once for each assigned value present in the array, taking four arguments: `accumulator`, `currentValue`, `currentIndex`, and `sourceArray` [@mozilla](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce).
- syntax: `arr.reduce(callback( accumulator, currentValue, [, index[, array]] )[, initialValue])`
- `callback` is a function to execute on each element in the array (except for the first, if no initialValue is supplied).
- 
### conclude an new array of max numbers from `reduce`-ing the rest numbers in each nested array

example [@freeCodeCamp](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures#basic-algorithm-scripting)

```
function largestOfFour(arr) {
  return arr.map(function(newArr) {
    return newArr.reduce(function(prev, current) {
      return current > prev ? current : prev;
    });
  });
}

largestOfFour([[17, 23, 25, 12], [25, 7, 34, 48], [4, -10, 18, 21], [-72, -3, -17, -10]]);
// expected output: [25, 48, 21, -3]
```


### `slice()`
: returns a shallow copy of a portion of an array into a new array object selected from start to end (end not included) where start and end represent the index of items in that array. The original array will not be modified.

| `slice()` | `slice(start)` | `slice(start, end)`|
| ----------- | ----------- | ----------- |
| a shallow copy of elements from the original array | index at which to start extraction | index at which to start extraction and extracts up to but not including end |

- So `slice(1,4)` extracts the second element through the fourth element. `slice(2,-1)` extracts the third element through the second-to-last element in the sequence.

```
function confirmEnding(str, target) {
  return str.slice(-target.length) === target
}

confirmEnding("Bastian", "n");
// expected output: true
```
---

# JavaScript

## Function Declaration
``` js
challenge = (x, y, z) => x + y + z // single statement

challenge = (x, y, z) => {
  // multiple statements
  return x + y + z
}

challenge = (x, y, z) => (// not always shorter and cannot use control statements like if, while
  1, 2, // multiple expressions seperated with ,
  x + y + z
)
```

## Logging
``` js
challenge = (x, y, z) => {
  console.log(x*y, y*z);
  return x + y + z
}
```

## Types
JS is __weakly typed__ (eg. `if (x != y)` can be written as `if (x - y)`).
``` js
// Primitives:
0 // number
true // boolean (behaves mostly the same as `1` (true) or `0` (false))
'asdf' // string

// All primitives are immutable (eg. `s = 'x'; s += 'y'; s == 'x' // true`)

// Objects:
[1, 2, 3] // array
{ x: 'fds' } // object
x => x+1 // function

// You can access and set *any* property on objects:
a = [1, 2, 3]
a[1] = 5           // a = [1, 5, 3]
a[5] = 7           // a = [1, 5, 3, undefined x 2, 7]
a[-1] = 9          // a = [1, 5, 3, undefined x 2, 7] + { '-1': 9 }
a['-1'] = 4        // a = [1, 5, 3, undefined x 2, 7] + { '-1': 4 }
a['ab'] = 'cd' // a = [1, 5, 3, undefined x 2, 7] + { '-1': 4, 'ab': 'cd' }
```

## Truthiness
``` js
// Falsy
undefined / null
0 / false
'' // empty string

// Everything else is truthy
```

## Variables
``` js
a = 1     // global
var a = 1 // local, only use if necessary (for recursion, etc)
```

## Arrays
``` js
a = [1+2, 'asdf', 99] // [3, 'asdf', 99]

// Initialise with value
Array(3).fill(0) // [0, 0, 0]
Array(5).fill(3) // [3, 3, 3, 3, 3]

// Initialise matrix
a = []; for (i = 3; i--; ) a[i] = [] // 25 chars
a = [...Array(3)].map(_ => [])       // 26 chars

// Length
a.length // 3

// Access
a[1]   // 'asdf'
a['1']

// Slice
a.slice(1, 3) // ['asdf', 99]

// Push
a.push(6, 7)     // [3, 'asdf', 99, 6, 7], 11 chars
a = [...a, 6, 7] //                        12 chars
a[a.length] = 6  // [3, 'asdf', 99, 6]

// Pop
a.pop() // 99, a = [3, 'asdf']

// Shift
a.shift() // 3, a = ['asdf', 99]

// Unshift
a.unshift(1) // [1, 3, 'asdf', 99]

// Splice
a.splice(1, 0, 'x', 'y') // [3, 'x', 'y', 'asdf', 99]

// Remove
a.splice(1, 1) // [3, 99]

// Concatenate
b = [8, 9]
a.push(...b)     // 12 chars, [3, 'asdf', 99, 8, 9]
a = a.concat(b)  // 13 chars
a = [...a, ...b] // 13 chars

// Clone
[...a]    // 6 chars
a.slice() // 9 chars

// NOTE: You can set and access negative indices on an array, but they count as
//       object properties, not array indices.
```

## Ranges
``` js
[...Array(5).keys()] // [0, 1, 2, 3, 4]

a = []
for (i = 2; i < 8; i += 2) a.push(i)
a // [2, 4, 6]
```

## Loops
``` js
// While
for (; x > y; ...) ...
for (; x > y; ...) { ... }

// Range (3 4 5 6 7 8)
for (i = 2; i++ < 9; ) ...

// Infinite
for (;;) ...
```

## Reduce
``` js
// Example: sum of array
a = [4, 7, 5]

// Use `eval` and `join` for simple cases
eval(a.join`+`) // 15 chars, creates string `"4+7+5"` then `eval`s it as JS code

// Use `map` if you cannot do the calculation just by joining
s = 0
a.map(n => s += n) && s // 20 chars, works because `a.map()` is always truthy

// Numbers can also be returned with `|` instead of `&&` (see casts section)
s = 0
a.map(n => s += n) | s // 19 chars
// But this will not work if `a.length == 1` and `a.map(...)[0]` is a number
// such that `(a.map(...)[0] | result) != result`
s = 0                             // returns `6` instead of `2` because `map`
[2].map(n => (s += n, x = 4)) | s //     returns `[4]` and `([4] | 2) == 6`)

// `reduce` is longer 99% of the time
a.reduce((s, n) => s + n)    // 20 chars, `s` initialised to `a[0]`
a.reduce((s, n) => s + n, 0) // 22 chars, `s` initialised to `0`
```

## Operators
In order of precedence (highest to lowest, same grouped):
``` js
a**b // a to-the-power-of b

+a // positive a (cast a to number)
-a // negative a
~a // bitwise-NOT a (equals -(a+1))

a * b // a times b
a / b // a divided-by b (floating-point division)
a % b // a remainder b (different to modulo for negative numbers)
(a % b + b) % b // a modulo b

a + b // a plus b
a - b // a minus b

a & b // a bitwise-AND b

a / b | 0 // a divided-by b (integer division, see casts section)
a | b // a bitwise-OR b

a ^ b // a bitwise-XOR b

a && b // a logical-AND b (returns a if a is false, else returns b)

a || b // a logical-OR b (returns a if a is true, else returns b)

a ? b : c // if a then b else c (comma operator cannot be used inside ternary)
```

## Comma Operator
The `,` operator returns the result of the rightmost operation.
``` js
f = n => { // 20 chars without comma operator
  x *= 3
  return n + 3
}
f = n => (x *= 3, n + 3) // 15 chars with comma operator

for (i in o) { // without
  x *= 3
  n += 3
}
for (i in o) // with (saves one char)
  x *= 3,
  n += 3
```

## Spread/Rest Operator
``` js
a = [4, 5, 6]
b = [1, 2, 3, ...a] // b = [1, 2, 3, 4, 5, 6]
f(...a) // f(4, 5, 6)

f = (...a) => a; f(1, 2, 3) // returns [1, 2, 3]
```

## Default Arguments
``` js
f = (a, b, c = 2) => [a, b, c]; f(1) // returns [1, undefined, 2]
f = (a, b = a*2) => [a, b]; f(3)     // returns [3, 6]
```

## Casts
Casts are pretty weird in JS, so here's a section about how they work:
- strings cast to numbers like so:
``` js
'1'     => 1
' 1 '   => 1   // leading and trailing whitespace allowed
'0b101' => 5   // 0b binary format
'0xa1'  => 161 // 0x hex format
'011'   => 11  // leading zeroes have no effect, no octal format
''      => 0   // empty string casts to 0

'1a'    => NaN // NaN = not-a-number, non-digit in string
'1 2'   => NaN // non-digit, not leading or trailing space
```
- arrays cast to strings like so:
``` js
[1]                    -> "1"
[1, 2, 'zxcv', 3, 'x'] -> "1,2,zxcv,3,x"
// Each item is cast to string then the array is joined with `,`
// Equivalent to a.join(',')
```
- functions, objects, etc. all cast to strings too but are less useful
- when casting to a number, things cast first to a string, then to a number:
``` js
[1]       -> "1"     -> 1
['a']     -> "a"     -> NaN
[1, 2, 3] -> "1,2,3" -> NaN
```
- `number + number` does addition (`boolean`s also act like numbers)
``` js
4 + 5 = 9
```
- `notNumber + number`, `number + notNumber` and `notNumber + notNumber` cast
  operands to strings and do string concatenation
``` js
3 + 'abc'     -> "3abc"
'abc' + 3     -> "abc3"
'abc' + 'xyz' -> "abcxyz"

arr = [1, 2, 'zzz', 3]
arr + ''      -> "1,2,zzz,3"
arr + 'x'     -> "1,2,zzz,3x"
arr + 3       -> "1,2,zzz,33"
[] + 2        -> "2"

func = x => x*2
4 + func      -> "4x => x*2"
```
- operators `-`, `*`, `/` and unary `+-` always cast
  operands to numbers
- bitwise operators (`|`, `&`, `~`, etc) always cast operands to signed
  32-bit integers (if something cannot be cast to a 32-bit integer, it casts to `0`)
``` js
'3' & 2       = ("3" -> 3 -> 3)                    & 2 = 2
~'a'          = ~("a" -> NaN -> 0)                     = -1
[7] | 8       = ([7] -> "7" -> 7 -> 7)             | 8 = 15
[1, 2, 3] | 1 = ([1, 2, 3] -> "1,2,3" -> NaN -> 0) | 1 = 1

0xffffffff + 0 = 4294967295
0xffffffff | 0 = -1 // look up signed integers if you're confused
0xf000000003 << 1 = 6 // 0xf000000003 truncates to 0x00000003
0xf000000003 << 0xf000000001 = 6 // 0xf000000003 -> 3, 0xf000000001 -> 1
```
- `number == number`, `number == notNumber` and `notNumber == number` (and
  same with `!=`, `<`, `<=`, etc.) cast operands to numbers (use `===` for strict equality)
``` js
// True
1 == 1
1 == '1'
1 == '   1   '
0 == ''
0 == '    '
0 == '\n\t'
1 == [1]
1 == ['1']

// False
1   == 2
1   == '2'
'1' == '  1  '
0   == '1'
0   == 'a'
1   == [1, 2]
```
- `string == notNumber` and `notNumber == string` compare as strings
- `notNumberOrString == notNumberOrString` compares by reference
``` js
[1, 2, 3] == [1, 2, 3] // false, because they are different arrays in memory

arrA = [1, 2, 3]
arrB = arrA
arrA == arrB // true, they are the same array (pushing to one will push to both)
```
- functions which expect a certain type of value will usually cast internally
``` js
'x'.repeat(2.7) // "xx" (2.7 truncated to 2)
'x'.repeat('3') // "xxx"
['a', 'b', 'c'].join(1) // "a1b1c" (1 cast to "1")
'xaaayaz'.match('a+') // ["aaa"] ('a+' cast to regex /a+/)
```

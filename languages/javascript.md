# JavaScript
- __dynamically typed__ (eg. `a = 2; a = 'zxcv'` is allowed)
- __weakly typed__ (eg. `if (x != y)` can be written as `if (x - y)`)

## Function Declaration
``` js
challenge = (x, y, z) => x + y + z

challenge = (x, y, z) => {
  return x + y + z
}
```

## Logging
``` js
challenge = (x, y, z) => {
  console.log(x*y, y*z);
  return x + y + z
}
```

## Variables
``` js
a = 1                  // 1 (global)
var a = 1              // 1 (local, only use if necessary for recursion, etc)
a = [x+y, y+z, 'asdf'] // [x+y, y+z, "asdf"]
```

## Loops
``` js
// While
while (x != y);
while (x != y) ...
while (x != y) { ... }

// Range (3 4 5 6 7 8)
for (i = 2; i++ < 9; ) ...
```

## Reduce
``` js
// Example: sum of array
a = [4, 7, 5]
// Use `eval` and `join` for simple cases
eval(a.join`+`) // 15 chars
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
// There is a `reduce` function, but it is longer 90% of the time
a.reduce((s, n) => s + n)    // 20 chars, `s` initialised to `a[0]`
a.reduce((s, n) => s + n, 0) // 22 chars, `s` initialised to `0`
```

## Casts
Casts are pretty weird in JS, so here's a section about how they work:
- strings cast to numbers like so:
``` js
'1'     -> 1
' 1 '   -> 1   // leading and trailing whitespace allowed
'0b101' -> 5   // 0b binary format
'0xa1'  -> 161 // 0x hex format
'011'   -> 11  // leading zeroes have no effect, no octal format
''      -> 0   // empty string casts to 0

'1a'    -> NaN // NaN = not-a-number, non-digit in string
'1 2'   -> NaN // non-digit, not leading or trailing space
```
- arrays cast to strings like so:
``` js
[1]                    -> "1"
[1, 2, 'zxcv', 3, 'x'] -> "1,2,zxcv,3,x"
// Each item is cast to string then the array is joined with `,`
```
- functions, objects, etc. all cast to strings too but are less useful
- when casting to a number, things cast first to a string, then to a number:
``` js
[1]       -> "1"     -> 1
['a']     -> "a"     -> NaN
[1, 2, 3] -> "1,2,3" -> NaN
```
- `number + number` does addition
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
- operators `-`, `*`, `/`, `<`, `<=`, `>`, `>=` and unary `+-` always cast
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
  same with `!=`) cast operands to numbers (use `===` for strict equality)
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
- `string == string` compares as strings
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

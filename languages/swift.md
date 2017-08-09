# Swift

## Function Declaration
``` swift
func buildSum(x: Int, y: Int, z: Int) -> Int {
  return x + y + z
}
```

Return type can be changed (eg. from `Int` to `Double` if that saves a cast).

## Logging
``` swift
challenge = (x, y, z) => {
  print(x*y, y*z)
  return x + y + z
}
```

## Types
Swift is __strongly typed__ (eg. `if (x != y)` cannot be written as `if (x - y)`).
``` swift
0         // Int
1.2       // Float/Double
[1, 2, 3] // Array<Int>
```

## Variables
``` swift
var a = 1              // 1
let a = 1              // 1 (immutable)
```

## Arrays
``` swift
// If the array will be modified, it must be mutable (declared using `var`)
var a = [1, 2, 3]

// Length
a.count // 3

// Access
a[1] // 2

// Slice
a[1 ... 2]             // [2, 3]
a[1 ... 2] = [5, 6, 7] // a = [1, 5, 6, 7]

// Push
a += [4, 5] // a = [1, 2, 3, 4, 5]
a.append(4) // a = [1, 2, 3, 4]

// Splice
a[1 ... 1] += [9]  // a = [1, 2, 9, 3]
a.insert(9, at: 2) // a = [1, 2, 9, 3]

// Remove
a[0 ... 1] = [] // a = [3]
a.remove(at: 1) // a = [1, 3]
```

## Ranges
``` swift
1 ... 5 // closed range: 1 2 3 4 5
1 ..< 5 // half-open range: 1 2 3 4
```

## Loops
``` swift
// While
while x < y { ... }

// Range (3 4 5 6 7 8)
for i in 3 ... 8 { ... }
```

## Map
``` swift
// Example: square each number
let a = [4, 7, 5]

a.map { $0*$0 }
```

## Reduce
``` swift
// Example: sum of array
let a = [4, 7, 5]

a.reduce(0, +)

a.reduce(0) { $0 + $1*$1 }

var s = 0
for n in a { s += n }
s
```

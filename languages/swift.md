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
0 // Int
1.2 // Float/Double

```

## Variables
``` swift
var a = 1              // 1
let a = 1              // 1 (immutable)
```

## Loops
``` swift
// While
while x < y { ... }

// Range (3 4 5 6 7 8)
for i in 3 ... 8 { ... }
```

## Ranges
``` swift
1 ... 5 // closed range: 1 2 3 4 5
1 ..< 5 // half-open range: 1 2 3 4
```

## Reduce
``` swift
let a = [4, 7, 5]

// Example: sum of array
a.reduce(0, +)

// Example: sum of squares
a.reduce(0) { $0 + $1*$1 }
```

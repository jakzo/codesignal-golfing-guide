# Kotlin
Kotlin runs in the Java VM and uses Java types, methods, etc.
- semicolons are optional (so don't use them)

## Function Declaration
``` kotlin
// Single-line function
fun challenge(x: Int, y: Int, z: Int) = x + y + z

// Multi-line function
fun fermactor(x: Int, y: Int, z: Int): Int {
  // ...
  return x + y + z
}

// Returning lists
// `fun challenge(): MutableList<Int> { ... }` can be changed to:
fun challenge(): List<Int> {
  // ...
  return listOf(1, 2, 3)
}
```

## Logging
``` kotlin
// TODO
```

## Variables
``` kotlin
var a = 1 // mutable
val b = 2 // immutable
a++ // ++a, --a, etc. same as Java
a += 3 // etc
```

## Loops
``` kotlin
// While
while (a < b); // condition must be boolean (not just int, etc)
while (a < b) x /= 2
while (a < b) { ... }

// Iterate over list
for (n in arr)

// Iterate over range
for (i in 1..5)
```

## Ranges
``` kotlin
3..8        // 3 4 5 6 7 8
3..8 step 2 // 3 5 7
8 downto 3  // 8 7 6 5 4 3
```

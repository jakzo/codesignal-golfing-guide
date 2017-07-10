# CoffeeScript

## Function Declaration
``` coffeescript
challenge = (x, y, z) ->
  x + y + z
```

## Logging
``` coffeescript
challenge = (x, y, z) ->
  console.log x*y, y*z
  x + y + z
```

## Cheat Sheet
CoffeeScript is JavaScript with different syntax. All types, methods, etc. are
the same as JavaScript. We will only cover the differences between
CoffeeScript and JavaScript.

- No curly braces - use indentation instead
- Implicit return - no need to write return at the end of a function
- Parentheses required around function arguments for only one argument

``` js
// JavaScript
f = n => {
  x = n + 1
  return x / 2
}
```

``` coffeescript
# CoffeeScript
f = (n) ->
  x = n + 1
  x / 2
```

- function calls need no parentheses - can also chain without parentheses if there
  is no space between the function and the argument
- No ternary - analogue is `x = if p then a else b` but that is long
- List comprehension
- string interpolation is `"a#{myVar}b"`
- `until` - means `while !condition`
- No `var` - no global variables

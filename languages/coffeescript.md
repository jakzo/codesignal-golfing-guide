# CoffeeScript
CoffeeScript is JavaScript with different syntax. All types, methods, etc. are
the same as JavaScript. We will only cover the differences between
CoffeeScript and JavaScript.
- __Function Declaration__
``` coffeescript
challenge = (x, y, z) ->
  x + y + z
```
- __Logging__
``` coffeescript
challenge = (x, y, z) ->
  console.log x*y, y*z
  x + y + z
```
- __No curly braces__ - use indentation instead
- __Implicit return__ - no need to write return at the end of a function
- __Parentheses required around function arguments__ for only one argument
``` coffeescript
# CoffeeScript
f = (n) ->  # `f = n ->` is not allowed
  x = n + 1
  x / 2     # return value of `f`
```
- __function calls need no parentheses__ - can also chain without parentheses if there
  is no space between the function and the argument
``` coffeescript
str.split"x".join"y" == str.split("x").join("y")
str.split "x".join"y" == str.split("x".join("y"))
```
- __No ternary__ - analogue is `x = if p then a else b` but that is long
- __List comprehension__
- __String interpolation__ is `"a#{myVar}b"`
- __`until` loop__ - means `while !condition`
- __No `var`__ - no global variables

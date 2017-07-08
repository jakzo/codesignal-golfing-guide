# Python

## Function Declaration
``` py
challenge = lambda x, y, z: x + y + z

def challenge(x, y, z):
  return x + y + z
```

## Logging
``` py
def challenge(x, y, z):
  print(x*y, y*z)
  return x + y + z
```

## Python 2 vs Python 3
The main difference between Python 2 and 3 is that in Python 2, `/` does integer
division if both of its operands are integers. `//` is required to do integer
division in Python 3.

Another difference is that in Python 3 numbers cannot be converted to strings using
`` `n` ``. `str(n)` must be used instead.

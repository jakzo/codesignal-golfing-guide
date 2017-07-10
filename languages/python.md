# Python

- __Function Declaration__
``` py
challenge = lambda x, y, z: x + y + z

def challenge(x, y, z):
  ...
  return x + y + z
```
- __Logging__
``` py
def challenge(x, y, z):
  print(x*y, y*z)
  return x + y + z
```
- __Python 2 vs Python 3__ - `/` = integer division in Python 2 if both of operands
are integers, `//` required for integer division in Python 3, `` `n` `` converts
numbers to strings in Python 2, `str(n)` must be used in Python 3
``` py
5 / 2  # `2` in Python 2, `2.5` in Python 3
5 / 2. # `2.5` in Python 2 and Python 3
5 // 2 # `2` in Python 2 and Python 3
`4`    # `"4"` in Python 2, error in Python 3
str(4) # `"4"` in Python 2 and Python 3

# C#

## Function Declaration
``` cs
int challenge(int x, int y, int z) => x + y + z;

int challenge(int x, int y, int z) {
  return x + y + z;
}
```

Argument and return types can be modified.

## Logging
``` cs
int challenge(int x, int y, int z) {
  Console.WriteLine("{0} {1}", x*y, y*z);
  return x + y + z;
}
```

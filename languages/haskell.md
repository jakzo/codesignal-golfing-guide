# Haskell

## Function Declaration
``` haskell
challenge x y z = x + y + z
```

## Logging
``` haskell
challenge s = unsafePerformIO $ do
    print $ (show $ x * y) ++ " " ++ (show $ y * z)
    return $ x + y + z
```

## Count Items in Array
``` haskell
-- Counts numbers in `array` which are divisible by 3
sum [ 1 | n <- array, mod n 3 < 1 ]
```

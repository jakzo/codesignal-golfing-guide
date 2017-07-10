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

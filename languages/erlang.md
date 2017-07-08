# Erlang

## Function Declaration
``` erlang
convertString(X, Y, Z) ->
  X + Y + Z.
```

## Logging
``` erlang
convertString(X, Y, Z) ->
  io:fwrite("~p ~p~n", [X*Y, Y*Z]),
  X + Y + Z.
```

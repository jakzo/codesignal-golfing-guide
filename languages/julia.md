# Julia

<details>
<summary>Function Declaration</summary>

``` julia
challenge(x, y, z) = x + y + z # single statement

challenge(x, y, z) = ( # multiple statements
  something();
  somethingelse();
  x + y + z
)
```
</details>

<details>
<summary>Logging</summary>

``` julia
challenge(x) = (
  println(1 + 2);
  x
)
```
</details>

<details>
<summary>Variables</summary>

``` julia
a = 1
```
</details>

<details>
<summary>Implicit Multiplication</summary>
You can put numbers before things with no operator in between and it will automatically multiply the results:

``` julia
4 * n
4n
```
</details>

<details>
<summary>Operator Overloading</summary>
When you have a function you use multiple times, you can assign an operator to it to shorten the name and save parentheses:

``` julia
cumsum([1, 2]) + cumsum([3, 4])

~ = cumsum
~[1, 2] + ~[3, 4]

div(19, 5) + div(18, 7)

/ = div
19 / 5 + 18 / 7
```
</details>

<details>
<summary>Arrays</summary>
Array items may be separated by newlines instead of commas:

``` julia
a = [1, 2, 3]
a = [1
     2
     3]
```
</details>

<details>
<summary>Map</summary>
You can pass lists into functions to map them:

``` julia
a = [1, 2, 3]
div(a, 2) # [0, 1, 1]
```

You can also map an operator across a list by prefixing it with `.`:

``` julia
a .* 2 # [2, 4, 6]
a .>= 2 # [false, true, true]
```

If they don't work, you can use list comprehension:

``` julia
[2n for n = a] # [2, 4, 6]
</details>

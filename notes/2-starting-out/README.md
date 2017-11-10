## Functions

- most functions are prefix e.g. `min 3.4 3.2`
  - has highest precedence
  - spaces are used for function application instead of e.g. C-style `()`
- if function takes two parameters, can call as infix function by surrounding it with backticks

```
div 92 10
```

- function definition
  - use `'` in name to either denote a strict version of a function (one that isn't lazy) or a slightly modified version of a function or a variable
  - func name can't start w/ uppercase

```
doubleUs x y = doubleMe x + doubleMe y
doubleMe x = x + x
```

- functions don't have to be defined in any particular order

- if expressions

```
doubleSmallNumber x = if x > 100
                        then x
                        else x*2
```

or

```
doubleSmallNumber' x = (if x > 100 then x else x*2) + 1
```

## Lists

```
lostNumbers = [4,8,15,16,23,42]
```

- must be homogenous
- strings are lists of chars
- list concatenation

```
[1,2,3,4] ++ [9,10,11,12] # => [1,2,3,4,9,10,11,12]
```

- when using `++`, Haskell walks over left list
- use `:` (*cons operator)* instead

```
5:[1,2,3,4,5] # => [5,1,2,4,5,5]
[1,2,3,4,5]:5 # => [1,2,3,4,5,5]
```

- `[1,2,3]` syntactic sugar for `1:2:3:[]`

- list index operator `!!`

```
[1,2,3,4,5] !! 1 # => 2
```

- Lists can be compared if the stuff they contain can be compared. When using <, <=, > and >= to compare lists, they are compared in lexicographical order. First the heads are compared. If they are equal then the second elements are compared, etc.

- lots of list functions...

###  ranges

- `[1..20]`
- `['K'..'Z']`
- `[20,19..1]` (`[20..1]` won't work)
- `[2,4..20]` (specify second element to create step)

- infinite list (lazily evaluated)
  - `[13,26..]`

### list comprehension

```
[x * *2 | x <- [1..10]]
```

  - for every `x` in range `[1..10]` return `x * 2`

- like above, but limited to those values of `x * 2` for which the predicate `x * 2 >= 12` returns true

```
[x * 2 | x <- [1..10], x * 2 >= 12]
```

- multiple predicates

```
[ x | x <- [10..20], x /= 13, x /= 15, x /= 19]
```

- multiple vars

```
[ x*y | x <- [2,5,10], y <- [8,10,11], x*y > 50]
```

## Tuples

- don't have to be homogenous
- a tuple of size k is its own type,

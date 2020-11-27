# PyPlus
This is a in-development package for all those good things python lacks, like a classic `for` and `async`/`promise` from JS with those sweet sweet anonymous functions.  

### Instalation
Simply put the `pyplus` folder in your project root. Soon it will be avaliable as a package on *PyPI* so you can install with *pip*.

## each
Use the `each` functon to construct a very interactive *for* and *foreach*, giving you full control of the execution stream.

### The problem
You need to create a for loop where you'll be skipping item or going back and forth. Python's default implementation of iterables don't allows that, so you'll need to do (at least I did) something like that:
```python
i = 0
while i < len(foo):
    ...
    i += 1
```
There should be a better way of doing that.

### The Solution
Our library adds a very easy to use and easy to extend function for that case. It is a generator that yields a implementation of EachIter, depending on the arguments passed.

### Usage
#### Arguments
The `each` function select the correct behavior by the signature of the arguments passed in `*args`. There are two by default:
```python
each(a: Int[, b: Int[, step: Int]]) -> EachIterRange
each(list: List[, step: int]) -> EachIterList
```
The first will work as the `range` function. If `b` is not provided, it will iterate all numbers from 0 up to, but not including, `b`. If `b` is provided, it will iterate all numbers from `a` up to, but not including, `b`. If `step` is provided, it will iterate step by step, otherwise it will iterate all numbers.

### Example
```python
for x in each(3, 7):
  # Skip the number 2
  if (x.val == 2):
    x.key += 1
    continue

  print(x.val)
## Output:
# 3
# 4
# 5
# 6
```

## More coming soon

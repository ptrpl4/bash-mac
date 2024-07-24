# List comprehension

The way to create new lists

### basic syntax

```python
# list comprehension syntax
new_list = [x for x in some_iterable]

# the equivalent code
new_list = []
for x in some_iterable:
    new_list.append(x)

# squared numbers
numbers = [1, 2, 3]
square_list = [x * x for x in numbers]  # [1, 4, 9]

# from string to float
strings = ["8.9", "6.0", "8.1", "7.5"]
floats = [float(num) for num in strings]  # [8.9, 6.0, 8.1, 7.5]
```

## List comprehension with if

### basic syntax

```python
# list comprehension with condition
new_list = [x for x in some_iterable if condition]

# odd numbers
numbers = [4, 8, 15, 16, 23, 42, 108]
odd_list = [x for x in numbers if x % 2 == 1] # [15, 23]

# conditions with functions
text = ["function", "is", "a", "synonym", "of", "occupation"]
words_tion = [word for word in text if word.endswith("tion")]
# result: ["function", "occupation"]
```

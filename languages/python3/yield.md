# yield

We can use yield if we need to take and use current generator value only onece and fast

```
def gen_countdown(n):
    while n != 0:
        yield n -1
        n -= 1
g = gen_countdown(4)
print(next(g))
# 3
print(next(g))
# 2
print(next(g))
# 1
print(next(g))
# 0
```

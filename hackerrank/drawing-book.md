# Drawing Book

```python
def pageCount(n, p):
    if n % 2 == 0: # even
        return min(p // 2, (n + 1 - p) // 2)
    return min(p // 2, (n - p) // 2)
```




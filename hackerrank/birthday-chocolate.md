# Birthday Chocolate

```python
def birthday(s, d, m):
    window = (0, m - 1)
    intS = [int(c) for c in s]

    result, cSum = 0, sum(intS[window[0]:(window[1] + 1)])
    if cSum == d:
        result += 1

    for _ in range(window[1], len(s) - 1):
        cSum = cSum - intS[window[0]] + intS[window[1] + 1]
        window = (window[0] + 1, window[1] + 1)
        if cSum == d:
            result += 1

    return result
```


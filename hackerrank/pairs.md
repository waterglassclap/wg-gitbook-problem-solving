# Pairs

```python
def pairs(k, arr):
    arrMap = {item:True for item in arr}
    return sum(item - k in arrMap for item in arr)
```




# Picking Numbers

```python
def pickingNumbers(a):
    if not a:
        return 0

    aMap = {}
    for item in a:
        aMap.setdefault(item, 0)
        aMap[item] += 1

    aKeys = sorted(aMap.keys())
    aggA = [(item, aMap[item]) for item in aKeys]
    
    result = aggA[0][1]
    for idx in range(1, len(aggA)):
        fItem, fItemCnt = aggA[idx - 1]
        sItem, sItemCnt = aggA[idx]

        result = max(result, fItemCnt, sItemCnt)
        if sItem - fItem <= 1:
            result = max(result, fItemCnt + sItemCnt)

    return result
```


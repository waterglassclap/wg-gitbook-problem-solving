# Sherlock and the Valid String

```python
def isValid(s):
    cnts = {}
    for c in s:
        cnts.setdefault(c, 0)
        cnts[c] += 1

    revCnts = {}
    for _, v in cnts.items():
        revCnts.setdefault(v, 0)
        revCnts[v] += 1

    revCntLen = len(revCnts)
    if revCntLen == 1:
        return "YES"
    if revCntLen > 2:
        return "NO"

    revCntIter = iter(revCnts)
    f, s = next(revCntIter), next(revCntIter)
    if f < s:
        f, s = s, f
    
    if revCnts[s] == 1 and s == 1:
        return "YES"
    if revCnts[f] == 1 and f - s == 1:
        return "YES"

    return "NO"
```


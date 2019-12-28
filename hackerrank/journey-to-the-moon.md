# Journey to the Moon

```python
from itertools import combinations

def journeyToMoon(n, astronaut):
    conn = [i for i in range(n)]

    def union(idx):
        while conn[idx] != idx:
            conn[idx] = conn[conn[idx]]
            idx = conn[idx]
        return idx
    for a,b in astronaut:
        conn[union(a)] = union(b)

    groups = {i:[] for i in range(n)}
    for i in range(n):
        groups[union(i)].append(i)

    gLenCnts = {}
    for gKey in groups:
        gLen = len(groups[gKey])
        if gLen > 0:
            gLenCnts.setdefault(gLen, 0)
            gLenCnts[gLen] += 1

    result = 0
    for gLen, gLenCnt in gLenCnts.items():
        result += (gLen * gLen) * int(gLenCnt * (gLenCnt - 1) / 2)
    for fGLen, sGLen in combinations(gLenCnts.keys(), 2):
        result += gLenCnts[fGLen] * gLenCnts[sGLen] * fGLen * sGLen

    return result
```


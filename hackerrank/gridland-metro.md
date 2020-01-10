# Gridland Metro

```python
from collections import deque

def gridlandMetro(n, m, k, track):
    rowQ = {}
    for f, s, t in track:
        r, c1, c2 = f - 1, s - 1, t
        rowQ.setdefault(r, [])
        
        if not rowQ[r]:
            rowQ[r].append((c1, c2))
            continue
        
        newQ = []
        rDeq = deque([])

        while rowQ[r]:
            left, right = rowQ[r].pop()
            if right < c1:
                newQ = rowQ[r][:] + [(left, right), (c1, c2)]
                break
            if left <= c1 <= right:
                newQ = rowQ[r][:] + [(min(left, c1), max(right, c2))]
                break
            rDeq.appendleft((left, right))

        while rDeq:
            left, right = rDeq.popleft()
            if newQ[-1][1] < left:
                newQ.append((left, right))
                break
            if newQ[-1][1] <= right:
                newQ[-1][1] = right
                break
        
        newQ += list(rDeq)
        rowQ[r] = newQ
    
    result = m * (n - len(list(rowQ.keys())))
    for rowQIdx, rowQVals in rowQ.items():
        prevIdx = 0
        for rowQLeft, rowQRight in rowQVals:
            result += rowQLeft - prevIdx
            prevIdx = rowQRight
        result += m - prevIdx

    return result
```


# Lily's Homework

```python
from operator import itemgetter

def lilysHomework(arr):
    arrLen = len(arr)

    def calc(idxes, idxMap):
        result = 0
        for i in range(arrLen):
            if idxes[i] == i:
                continue
            rIdx = idxMap[i]
            idxMap[i], idxMap[idxes[i]] = i, rIdx 
            idxes[i], idxes[rIdx] = idxes[rIdx], idxes[i]
            result += 1
        return result

    sIdxes, _ = zip(*sorted(enumerate(arr), key = itemgetter(1)))
    idxMap = {sIdxes[i]:i for i in range(arrLen)}

    revSIdxes, _ = zip(*sorted(enumerate([-item for item in arr]), key = itemgetter(1)))
    revIdxMap = {revSIdxes[i]:i for i in range(arrLen)}

    return min(calc(list(sIdxes), idxMap), calc(list(revSIdxes), revIdxMap))
```


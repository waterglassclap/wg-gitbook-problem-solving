# Hackerland Radio Transmitters

```python
import sys
from bisect import bisect_left

MAX_INT = sys.maxsize

def hackerlandRadioTransmitters(x, k):
    xLen = len(x)
    x.sort()

    yesM = [MAX_INT for _ in range(xLen)]
    noM = [MAX_INT for _ in range(xLen)]
    m = [MAX_INT for _ in range(xLen)]

    m[0], yesM[0] = 1, 1

    for i in range(1, xLen):
        newIdx = bisect_left(x, x[i] - k)
        if newIdx == 0:
            m[i], yesM[i], noM[i] = 1, 1, 1
            continue
        yesM[i] = m[newIdx - 1] + 1
        noM[i] = MAX_INT if newIdx == i else yesM[newIdx]
        m[i] = min(yesM[i], noM[i])

    return m[-1]
```


# Forming a Magic Square

```python
#!/bin/python3
import os
import sys

MAX_INT = sys.maxsize

def formingMagicSquare(s):

    sumTarget, maxInt = 15, 9
    subsets = []
    for i in range(1, maxInt + 1):
            for j in range(1, min(maxInt, sumTarget - i) + 1):
                k = sumTarget - i - j
                if k > maxInt or k <= 0 or i == k or j == k or i == j:
                    continue
                subsets.append((i, j, k))


    cost = MAX_INT
    for i, j, k in subsets:
        for l, m, n in subsets:
            o, p, q = sumTarget - (i + l), sumTarget - (j + m), sumTarget - (k + n)
        
            if not (0 < o <= maxInt and 0 < p <= maxInt and 0 < q <= maxInt):
                continue
    
            arr = [i, j, k, l, m, n, o, p, q]
            if len(arr) != len(set(arr)):
                continue
            if not (i + m + q == k + m + o == sumTarget):
                continue

            newCost = abs(s[0][0] - i) + abs(s[0][1] - j) + abs(s[0][2] - k)
            newCost = newCost + abs(s[1][0] - l) + abs(s[1][1] - m) + abs(s[1][2] - n)
            newCost = newCost + abs(s[2][0] - o) + abs(s[2][1] - p) + abs(s[2][2] - q)

            cost = min(cost, newCost)
    
    return cost

if __name__ == '__main__':
    fptr = open(os.environ['OUTPUT_PATH'], 'w')

    s = []

    for _ in range(3):
        s.append(list(map(int, input().rstrip().split())))

    result = formingMagicSquare(s)

    fptr.write(str(result) + '\n')

    fptr.close()

```


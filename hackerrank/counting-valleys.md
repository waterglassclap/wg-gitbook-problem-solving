# Counting Valleys

```python
#!/bin/python3

import math
import os
import random
import re
import sys

UP, DOWN = 1, -1

def countingValleys(n, s):
    count, pos = 0, 0
    for c in s:
        direc = UP if c == 'U' else DOWN
        pos += direc
        if pos == 0 and direc == UP:
            count += 1
    return count

if __name__ == '__main__':
    fptr = open(os.environ['OUTPUT_PATH'], 'w')

    n = int(input())
    s = input()

    result = countingValleys(n, s)

    fptr.write(str(result) + '\n')
    fptr.close()

```


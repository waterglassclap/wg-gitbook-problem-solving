# Highest Palindrome

```python
def highestValuePalindrome(s, n, k):
    iterCnt = n // 2
    
    nums = [int(c) for c in s]
    marks = {}
    for i in range(iterCnt):
        lIdx, rIdx = i, n - i - 1
        if nums[lIdx] == nums[rIdx]:
            continue
        if nums[lIdx] > nums[rIdx]:
            marks[rIdx] = True
            nums[rIdx] = nums[lIdx]
        else:
            marks[lIdx] = True
            nums[lIdx] = nums[rIdx]

    kRem = k - len(marks)    
    if kRem < 0:
        return "-1"

    for i in range(iterCnt):
        lIdx, rIdx = i, n - i - 1
        if nums[lIdx] == 9:
            continue
        if kRem < 1:
            break
        if lIdx in marks or rIdx in marks:
            nums[lIdx], nums[rIdx] = 9, 9
            kRem -= 1
        else:
            if kRem < 2:
                break
            nums[lIdx], nums[rIdx] = 9, 9
            kRem -= 2

    #handle odd
    if n % 2 == 1 and kRem > 0:
        nums[iterCnt] = 9

    return ''.join([str(item) for item in nums])
```


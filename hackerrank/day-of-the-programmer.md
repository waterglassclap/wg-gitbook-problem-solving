# Day of the Programmer

```python
def dayOfProgrammer(year):
    if (year == 1918):
        return '26.09.1918'

    if (year <= 1917) and (year % 4 == 0):
        return '12.09.%s' % year
    
    if (year > 1918) and (year % 400 == 0 or ((year % 4 == 0) and (year % 100 != 0))):
        return '12.09.%s' % year
    
    return '13.09.%s' % year
```




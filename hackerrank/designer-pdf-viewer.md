# Designer PDF Viewer

```python
#!/bin/python3

def designerPdfViewer(h, word):
    hMap = {chr(idx + ord('a')): item for idx, item in enumerate(h) }
    maxItem = max([hMap[c] for c in word])

    return maxItem * len(word)
```


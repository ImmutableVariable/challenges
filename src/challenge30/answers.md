# Answers

## Python

```python
def b(arr):
    c = 0
    for i,j in enumerate(arr[:-2]):
        if j == arr[i+2] and not j == arr[i+1]:
            c += 1
    return c
```
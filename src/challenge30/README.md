# Boomerang Numbers

Create a function that counts the "boomerangs" in an array where, given array `x` and index `n`, `x[n]` and `x[n+2]` are the same, but `x[n+1]` is different.

```
[1, 5, 1] -> 1
[1, 5, 1, 5, 1] -> 3
```

## Examples

```python
assert num_boomerangs([1, 5, 1, 5, 1]) == 3
```

## Notes

- Boomerangs can overlap, and you must account for this.


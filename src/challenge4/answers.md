# Answers

## JavaScript

```js
function rotate(nums, k, right) {
    if (right) k = nums.length - k;
    nums.unshift(...nums.splice(k));
    return nums;
}
```

## Go

```go
func rotate(nums []int, k int, right bool) []int {
    if right {
        k = len(nums) - k
    }
    return append(nums[k:], nums[:k]...)
}
```

## Python

```python
def rotate(nums, k, right=False):
    if right:
        k = len(nums) - k
    return nums[k:] + nums[:k]
```

# Answers

## JaveScript

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
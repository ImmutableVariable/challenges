# Answers

## JavaScript

```js
function isPalindrome(str) {
  return str === str.split('').reverse().join('');
}
```

## Python

```python
def is_palindrome(s: str) -> bool:
    return s == s[::-1]
```
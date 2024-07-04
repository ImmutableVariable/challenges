# Lychrel Numbers

A lychrel number is a natural number that never forms a palindrome through the reverse and add process. The process is defined as follows:

1. Take an integer
2. Reverse the digits
3. Add the original number and the reversed number
4. Check if the sum is a palindrome
5. If the sum is not a palindrome, repeat the process with the sum

### Example

```
47 -> 47 + 74 = 121 -> 121 is a palindrome, therefore 47 is not a lychrel number
```

Because this is an open problem, there is no known lychrel number. Therefore, you can assume that if the process reaches 50 iterations, the number is not a lychrel number.

Create a function that accepting a integer returns a boolean indicating if the number is a lychrel number.

## Examples

```python
196 -> True
47 -> False
```

## Source

[Project Euler - Problem 55](https://projecteuler.net/problem=55)
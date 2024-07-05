# Reversing A String While Preserving Special Characters

Create a function that accepts a string and returns the reverse of that string while preserving the position of all punctuation.

```
a,b$c -> c,b$a
hello world! -> dlrow olleh!
```

## Examples

```python
assert reverse_string("a,b$c") == "c,b$a"
assert reverse_string("hello world!") == "dlrow olleh!"
```

## Notes

- The string may include letters, numbers, and special characters.

## Constraints

- The string will not be empty.
- The string will contain at least one letter.



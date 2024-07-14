# Perfect Numbers

A perfect number is a number that can be formed by adding its proper divisors (excluding itself). Create a function that accepts a number and returns True if the number is a perfect number, and False if it is not.

## Example

| Number | Divisors | Sum of Divisors | Is Perfect Number |
|--------|----------|------------------| ------------------ |
| 6      | 1, 2, 3, 6*  | 1 + 2 + 3 = 6   | True               |
| 28     | 1, 2, 4, 7, 14, 28* | 1 + 2 + 4 + 7 + 14 = 28 |  True |
| 7     | 1, 7*       | 1 = 1              | False              |

\* A proper divisor is a positive divisor that is not the number itself.
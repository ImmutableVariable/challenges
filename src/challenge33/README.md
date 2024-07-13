# Pascal's Triangle

Pascal's triangle is a triangular array of binomial coefficients, named after the famous French mathematician Blaise Pascal. It is constructed by summing the two numbers directly above it. The numbers at the edges of the triangle are always one, and all other numbers can be determined by the sum.

Create a function that takes an integer `n` and returns the nth row of Pascal's triangle. You can assume that the nth row is greater than or equal to 0. You do not have to print the triangle, just return a 2d array.

## Example

```
1 
1 1 
1 (1+1) 1
1 (1+2) (2+1) 1
1 (1+3) (3+3) (3+1) 1
```

```
    1
   1 1
  1 2 1
 1 3 3 1
```

![Pascal's Triangle](../images/PascalTriangle.gif)

By Hersfold on the English Wikipedia - Own work, Public Domain, [here](https://commons.wikimedia.org/w/index.php?curid=3902538)
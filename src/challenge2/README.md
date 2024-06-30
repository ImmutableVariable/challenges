# Happy Numbers - Code Golf (Finding the shortest code to solve a problem)

Here is how it works basically:
1. take any number N.
2. Square the individual digits of N then add them together
3. Repeat step 2 until the answer is equal to 1, if it is a infinite loop, it is not a happy number.

Ex:
N = 13
1^2 + 3^2 = 1 + 9 = 10
1^2 + 0^2 = 1

So 13 is a happy number.

## Challenge

Create a function that accepts a number and returns True if the number is a happy number, False if it is not.

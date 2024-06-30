# Closest Index To A Specified Integer

Create a function that accepts two parameters, an integer and a array of integers, and returns the index of the integer that is the closest the the value; however, if they are the same distance from the integer, return the greater one! 

# Examples

```
closestIndexToNumber(10, [1, 5, 9, 11]); // 3
closestIndexToNumber(2, [1, 5, 9, 10]); // 0
closestIndexToNumber(5, [1, 5, 9, 10]); // 1
closestIndexToNumber(10, [9, 11]); // 1
closestIndexToNumber(-10, [-9, -11]); // 0
closestIndexToNumber(0, []); // 0
```
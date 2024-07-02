# Shortest Path Finder

Given a 2d matrix, find the shortest path from a point (row1, column1) to another point (row2, column2) and print the new matrix where the path it follows is the value 2. The matrix will have a value of 1 for walls and 0 for paths. Because it goes by row, column imagine the matrix as a coordinate system where the top left is (0, 0) and the bottom right is (n, m). 

## Example

```
Input
[
    [0, 0, 0, 0, 0],
    [1, 1, 1, 1, 0],
    [0, 0, 0, 0, 0],
    [0, 1, 1, 1, 1],
    [0, 0, 0, 0, 0]
]
(0, 0) -> (4, 4)

Output

[2, 2, 2, 2, 2]
[1, 1, 1, 1, 2]
[2, 2, 2, 2, 2]
[2, 1, 1, 1, 1]
[2, 2, 2, 2, 2] 

Where 2 is the path followed.
```
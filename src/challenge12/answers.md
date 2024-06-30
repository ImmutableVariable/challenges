# Answer

## Javascript 

```js
function matrixMultiply(matrix1, matrix2) {
    if (matrix1.length === 0 || matrix2.length === 0) return null;
    if (matrix1[0].length !== matrix2.length) return null;
 
    const result = [];
    for (const rowOfMatrix1 of matrix1) {
        const newRow = [];
        for (let matrix2Index = 0; matrix2Index < matrix2[0].length; matrix2Index++) {
            const column = matrix2.map(row => row[matrix2Index]);
            const sum = rowOfMatrix1.reduce((acc, value, index) => acc + value * column[index], 0);
            newRow.push(sum);
        }
        result.push(newRow);
    }
 
    return result;
}
```
# Answer

## JavaScript

```javascript
function closestIndexToNumber(number, array) {
    let closestIndex = 0;
    let closestDistance = Math.abs(array[0] - number);
 
    array.forEach((value, index) => {
        const distance = Math.abs(value - number);
        if (distance < closestDistance || (closestDistance === distance && value > array[closestIndex])) { 
            closestDistance = distance;
            closestIndex = index;
        }
    });
    
    return closestIndex;
}
```


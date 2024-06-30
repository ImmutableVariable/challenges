# Answer

## Javascript

```js
function isRightTriangle(arr) {
    if (arr.length !== 3) return false;
    
    let sortedArr = arr.sort((a, b) => a - b);
    
    return (sortedArr[0] ** 2 + sortedArr[1] ** 2) === (sortedArr[2] ** 2);
}
```

## Haskell

```hs
isRightTriangle :: [Int] -> Bool
isRightTriangle arr
    | length arr /= 3 = False
    | otherwise = a^2 + b^2 == c^2
    where [a, b, c] = sort arr
```
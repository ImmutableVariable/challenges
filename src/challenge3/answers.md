# Answers

## Javascript
```js
function isArmstrongNumber(n) {
    return n === n.toString().split('').reduce((a, c) => a + Math.pow(parseInt(c), n.toString().length), 0);
}
```

## Haskell
```hs
isArmstrongNumber :: Int -> Bool
isArmstrongNumber n = n == sum (map (\x -> read [x] ^ length (show n)) (show n))

findNArmstrongNumbers :: Int -> [Int]
findNArmstrongNumbers n = filter isArmstrongNumber [1..n]
```
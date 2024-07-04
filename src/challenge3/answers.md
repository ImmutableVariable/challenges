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

## Python
```python
def is_armstrong_number(n: int) -> bool:
    return n == sum([int(x) ** len(str(n)) for x in str(n)])

def find_n_armstrong_numbers(n: int) -> list:
    return [x for x in range(1, n + 1) if is_armstrong_number(x)]
```
# Answer

## Haskell 
```hs
collatzSequenceForN :: (Integral a) => a -> [a]
collatzSequenceForN n
  | n == 1 = [1]
  | even n = n : collatzSequenceForN (n `div` 2)
  | odd n = n : collatzSequenceForN (n * 3 + 1)

collatzSequenceToN :: (Integral a) => a -> [[a]]
collatzSequenceToN n = map collatzSequenceForN [1..n]
```

## Javascript (Recursive)

```javascript
function collatzForN(n) {
    if (n === 1) return [1];
    if (n % 2 === 0) return [n, ...collatzForN(n / 2)];
    return [n, ...collatzForN(3 * n + 1)];
}

function getCollatzToN(n) {
    const collatz = Array(n).fill().map((_, i) => collatzForN(i + 1));
    return collatz;
}
```

## Javascript (Iterative)

```javascript
function collatzForN(n) {
    const sequence = [];
    while (n !== 1) {
        sequence.push(n);
        n = n % 2 === 0 ? n / 2 : 3 * n + 1;
    }
    sequence.push(1);
    return sequence;
}
```

## Python

```python
def collatz_for_n(n):
    sequence = []
    while n != 1:
        sequence.append(n)
        n = n // 2 if n % 2 == 0 else 3 * n + 1
    sequence.append(1)
    return sequence
```
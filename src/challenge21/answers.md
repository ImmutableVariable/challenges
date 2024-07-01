# Answer

## JavaScript - For Loop

```javascript
function findMissingNumber(v) {
    for (let i = 1; i <= v.length + 1; i++) {
        if (!v.includes(i)) {
            return i;
        }
    }
}
```

## JavaScript - HashMap

```js
function findMissing(numbers) {
    const seen = new Set(numbers);
    const n = Math.max(...numbers) + 1;
    for (let i = 1; i <= n; i++) {
        if (!seen.has(i)) {
            return i;
        }
    }
    return n + 1;
}

```

## Rust - Sum

```rust
fn find_missing_number(v: &Vec<i32>) -> i32 {
    let n = v.len() as i32 + 1;
    let total = n * (n + 1) / 2;
    let sum: i32 = v.iter().sum();
    total - sum
}
```

## Haskell

```haskell
findMissingNumber :: [Int] -> Int
findMissingNumber v = n * (n + 1) `div` 2 - sum v
    where n = fromIntegral $ length v + 1
```

## C

```c
int findMissingNumber(int arr[], int size) {
    int xor = 0;
    for(int i = 0; i < size; i++) {
        xor ^= arr[i] ^ (i + 1);
    }
    return xor ^ (size + 1);
}
```

## Python

```py
def find_missing(numbers):
    n = len(numbers) + 1
    return (n * (n + 1)) // 2 - sum(numbers)
```
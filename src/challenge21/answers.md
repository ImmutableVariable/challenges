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


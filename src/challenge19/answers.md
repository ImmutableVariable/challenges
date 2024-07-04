# Answer

## Rust

```rust
fn bellard_pi(iterations: i32) -> f64 {
    let mut sum: f64 = 0.0;
    for n in 0..iterations {
        let t1 = f64::powi(-1.0, n) / f64::powi(2.0, 10 * n);
        let n = n as f64;
        let t2 = -32.0 / (4.0 * n + 1.0);
        let t3 = -1.0 / (4.0 * n + 3.0);
        let t4 = 256.0 / (10.0 * n + 1.0);
        let t5 = -64.0 / (10.0 * n + 3.0);
        let t6 = -4.0 / (10.0 * n + 5.0);
        let t7 = -4.0 / (10.0 * n + 7.0);
        let t8 = 1.0 / (10.0 * n + 9.0);

        sum += t1 * (t2 + t3 + t4 + t5 + t6 + t7 + t8);
    }
    return sum / 64.0;
}

# fn main() {
let iterations = 10;
println!("Result: {}", bellard_pi(iterations));
# }
```

```rust
fn leibniz(n: u32) -> f64 {
    if n == 0 {
       return 1.0
    }
    
    let numerator = if n % 2 == 0 {
        1.0
    } else {
        -1.0
    };
    
    return (numerator / (2 * n + 1) as f64) + leibniz(n-1);
}

# fn main() {
let n = 10000;
println!("Result: {}", 4.0 * leibniz(n));
# }
```

### Python Equivalent

```python
def leibniz(n: int) -> float:
    if n == 0:
        return 1.0
    
    numerator = 1.0 if n % 2 == 0 else -1.0
    return (numerator / (2 * n + 1)) + leibniz(n-1)
```

```python
def bellard_pi(iterations: int) -> float:
    sum = 0.0
    for n in range(iterations):
        t1 = (-1) ** n / 2 ** (10 * n)
        t2 = -32 / (4 * n + 1)
        t3 = -1 / (4 * n + 3)
        t4 = 256 / (10 * n + 1)
        t5 = -64 / (10 * n + 3)
        t6 = -4 / (10 * n + 5)
        t7 = -4 / (10 * n + 7)
        t8 = 1 / (10 * n + 9)

        sum += t1 * (t2 + t3 + t4 + t5 + t6 + t7 + t8)
    return sum / 64
```

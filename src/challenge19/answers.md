# Answer

## Rust

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
```

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
```


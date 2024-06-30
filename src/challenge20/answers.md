# Answer

## Rust

```rust
fn herons_method(S: f64, x_current: f64, tolerance: f64) -> f64 {
    let x_next = 0.5 * (x_current + S / x_current);
    
    if (x_next - x_current).abs() < tolerance {
        x_next
    } else {
        herons_method(S, x_next, tolerance)
    }
}

fn main() {
    let S = 13.0;
    let guess = S / 2.0;
    let tolerance = 1e-10;
    println!("Result: {}", herons_method(S, guess, tolerance));
}
```
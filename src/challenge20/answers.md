# Answer

## Rust

```rust
#use std::f64::consts::E;
fn square_root(s: f64) -> f64 {
    // sqrt(x) = e^((1/2)ln(S))
    let guess = E.powf(0.5 * f64::ln(s));
    (guess * 1e9).round() / 1e9 // round to 9 decimal places
}

#fn main() {
let s = 19.0;
println!("The square root of {} is {}", s, square_root(s));
#}
```

```rust, editable
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
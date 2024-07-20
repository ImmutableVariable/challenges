# Answer

## Rust

```rust
# #[derive(Debug)]
struct Wallet {
    dollars: i32,
    quarters: i32,
    dimes: i32,
    nickels: i32,
    pennies: i32,
}

fn cash_to_coins(cash: f64) -> Wallet {
    let dollars: i32 = cash as i32;
    let mut fractional = cash.fract();

    let quarters = (fractional / 0.25).floor() as i32;
    fractional %= 0.25; // ex: 0.76 % 0.25 = 0.01 which is the remaining cash after
                        // just repeat over and over 💀

    let dimes = (fractional / 0.10).floor() as i32;
    fractional %= 0.10;

    let nickels = (fractional / 0.05).floor() as i32;
    fractional %= 0.05;

    let pennies = (fractional / 0.01).floor() as i32;

    Wallet {
        dollars,
        quarters,
        dimes,
        nickels,
        pennies,
    }
}
#fn main() {
    #println!("{:?}", cash_to_coins(2.75));
    #println!("{:?}", cash_to_coins(0.99));
    #println!("{:?}", cash_to_coins(100.75));
#}
```
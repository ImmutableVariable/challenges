# Answer

## Rust

```rust
fn is_perfect_number(n: i32) -> bool {
    let sum: i32 = (1..n).filter(|x| n % x == 0).sum();
    sum == n
}

#// no builtins  
#/*fn is_perfect_number(n: i32) -> bool {
    #let mut sum = 0;
    #for i in 1..n {
        #if n % i == 0 {
            #sum += i;
        #}
    #}
    #sum == n
#}*/
#fn main() {
println!("{}", is_perfect_number(6)); // true
println!("{}", is_perfect_number(28)); // true
println!("{}", is_perfect_number(7)); // false
#}
```
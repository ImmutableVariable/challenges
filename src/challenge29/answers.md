# Answer

## Rust

```rust
fn reverse_number(num: u128) -> u128 {
    num.to_string().chars().rev().collect::<String>().parse::<u128>().unwrap()
}

fn is_lychrel_number(n: u128) -> bool {
    let mut num = n;
    for _ in 0..50 {
        let rev_num = reverse_number(num);
        num += rev_num;
        if num == reverse_number(num) { 
            return false;
        }
    }
    true
}

#fn main() {
println!("{}", is_lychrel_number(196)); // true
println!("{}", is_lychrel_number(47)); // false
#}
```

## Python

```python
def lyc(num):
    rev = int("".join(reversed(str(num))))
    num += rev
    if "".join(reversed(str(num))) == str(num):
        return True
    else:
        try:
            lyc(num)
        except RecursionError:
            return False
```
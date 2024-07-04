# Answer

## Rust

```rust
#fn get_fibonacci(n: usize) -> Vec<i64> {
    # let mut numbers = vec![0i64, 1];
    # while numbers.len() < n {
        # let next_number = numbers[numbers.len() - 1] + numbers[numbers.len() - 2];
        # numbers.push(next_number);
    # }
    # numbers
# }
fn zeckendorf_representation(mut n: i64) -> Vec<i64> {
    let numbers = get_fibonacci(50); // 50 is basically enough, otherwise it will be too slow/overflow
    let mut result = Vec::new();
    let mut i = numbers.len() - 1;
    while n > 0 && i > 0 {
        if numbers[i] <= n {
            n -= numbers[i];
            result.push(numbers[i]);
        }
        if i > 0 { i -= 1; }
    }

    result
}

#fn main() {
println!("{:?}", zeckendorf_representation(64));
println!("{:?}", zeckendorf_representation(4));
#}
```

### Python Equivalent

```python
~from typing import List

~def get_fibonacci(n: int) -> List[int]:
    ~numbers = [0, 1]
    ~while len(numbers) < n:
        ~next_number = numbers[-1] + numbers[-2]
        ~numbers.append(next_number)
    ~return numbers
def zeckendorf_representation(n: int) -> List[int]:
    numbers = get_fibonacci(50) 
    result = []
    i = len(numbers) - 1
    while n > 0 and i > 0:
        if numbers[i] <= n:
            n -= numbers[i]
            result.append(numbers[i])
        if i > 0: i -= 1

    return result
~print(zeckendorf_representation(64))
```
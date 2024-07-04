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

## Python

```python
def fib(n):
    l = []
    a, b = 0, 1
    while b < n:
        a, b = b, a+b
        l.append(a)
    return l

def zec(n):
    l = []
    nums = fib(n)
    while len(nums) > 0:
        if max(nums) <= n - sum(l):
            l.append(max(nums))
            nums.pop()
        else:
            nums.pop()
    return l
```

You could also do it in a single line using Lambdas

```python
zr = lambda n, fibs=[0, 1]: fibs.append(fibs[-1] + fibs[-2]) or zr(n, fibs) if fibs[-1] < n else [x for x in fibs[::-1] if n >= x and (n := n - x) >= 0 and x != 0]
```

## Haskell

```haskell
f=0:1:zipWith(+)f(tail f)
z n|n>0=let a=last$takeWhile(<=n)f in a:z(n-a)|0<1=[]
```

But since that is not that good to read here is the cleaner and better to read version:

```haskell
fibonacci :: [Int]
fibonacci = 0 : 1 : zipWith (+) fibonacci (tail fibonacci)

zeckendorf :: Int -> [Int]
zeckendorf n 
    | n > 0     = let largestFib = last $ takeWhile (<= n) fibonacci
                  in largestFib : zeckendorf (n - largestFib)
    | otherwise = []
```
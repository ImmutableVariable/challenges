# Answer

## Rust

```rust
fn pascals_triangle(depth: usize) -> Vec<Vec<usize>> {
    let mut triangle = vec![vec![0; depth]; depth];
    for i in 0..depth {
        triangle[i][0] = 1;
        triangle[i][i] = 1; // the edge bits...
        for j in 1..i {
            triangle[i][j] = triangle[i - 1][j - 1] + triangle[i - 1][j];
        }
    }
    triangle
}
#fn main() {
    #let depth = 5;
    #let triangle = pascals_triangle(depth);
    #for row in triangle {
    #   for num in row {
            #if num == 0 { // as the triangle is a square initialized with 0s
               #break;
            #}
    #       print!("{} ", num);
    #   }
    #   println!();
    #}
#}
```
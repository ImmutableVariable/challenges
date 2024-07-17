# Answer

## Rust

```rust
#use std::collections::HashMap;
fn merge_intervals(mut intervals: Vec<Vec<i32>>) -> Vec<Vec<i32>> {
    if intervals.is_empty() {
        return vec![];
    }

    intervals.sort_unstable_by(|a, b| a[0].cmp(&b[0]));
    let mut result = Vec::new();
    let mut current_interval = intervals[0].clone();

    for interval in intervals.into_iter().skip(1) {
        if interval[0] <= current_interval[1] {
            current_interval[1] = current_interval[1].max(interval[1]);
        } else {
            result.push(current_interval);
            current_interval = interval;
        }
    }

    result.push(current_interval);
    result
}
#fn main() {
    #let intervals = vec![vec![1, 3], vec![2, 6], vec![8, 10], vec![15, 18]];
    #let result = merge_intervals(intervals.clone()); // just clone them rn bc im lazy
    #println!("{:?} === {:?}", intervals, result);
#}
```
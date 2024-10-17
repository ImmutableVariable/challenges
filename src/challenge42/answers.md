# Answer


### Rust - Insertion Sort
```rust
#fn main() {
    #let mut arr = [5, 3, 2, 4, 1];
    #sort(&mut arr);
    #println!("{:?}", arr);
#}
fn sort<T: Ord>(arr: &mut [T]) {
    for i in 1..arr.len() {
        let mut j = i;
        while j > 0 && arr[j] < arr[j - 1] {
            arr.swap(j, j - 1);
            j -= 1;
        }
    }
}
```

### Zig

```rust
pub fn main() void {
    var arr = [_]u32{5, 3, 2, 4, 1};
    sort(&arr);
}

pub fn sort(arr: []u32) void {
    const len = arr.len;
    for (1..len) |i| {
        var j = i;
        while (j > 0 and arr[j] < arr[j - 1]) {
            const temp = arr[j];
            arr[j] = arr[j - 1];
            arr[j - 1] = temp;
            j -= 1;
        }
    }
}
```
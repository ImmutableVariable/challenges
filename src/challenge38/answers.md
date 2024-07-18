# Answer

## Rust

```rust
fn hamming_encode(data: [i32; 4]) -> [i32; 7] {
    let p = [
        data[0] ^ data[1] ^ data[3],
        data[0] ^ data[2] ^ data[3],
        data[1] ^ data[2] ^ data[3],
    ];
    [p[0], p[1], data[0], p[2], data[1], data[2], data[3]]
}

fn hamming_decode(mut encoded: [i32; 7]) -> [i32; 4] {
    let s = [
        encoded[0] ^ encoded[2] ^ encoded[4] ^ encoded[6],
        encoded[1] ^ encoded[2] ^ encoded[5] ^ encoded[6],
        encoded[3] ^ encoded[4] ^ encoded[5] ^ encoded[6],
    ];
    let error_position = s[0] + (s[1] << 1) + (s[2] << 2);

    if error_position != 0 {
        encoded[(error_position - 1) as usize] ^= 1;
    }

    [encoded[2], encoded[4], encoded[5], encoded[6]]
}
#fn main() {
    #let data = [1, 0, 1, 0];
    #println!("Inputed Data: {:?}", data);
    #let encoded = hamming_encode(data);
    #println!("Encoded Data: {:?}", encoded);
    #let mut encoded = encoded;
    #encoded[3] = encoded[3] ^ 1;
    #println!("Corrupt Data: {:?}", encoded);
    #let decoded = hamming_decode(encoded);
    #println!("Decoded Data: {:?}", decoded);
    #assert_eq!(decoded, data, "Data is not the same");
#}
```
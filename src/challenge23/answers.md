# Answer

## JavaScript

```javascript
function longest_word(str) {
    let words = str.split(' ');
    let longest = '';
    for (let word of words) {
        if (word.length > longest.length) {
            longest = word;
        }
    }
    return longest;
}
```

## Rust

```rust
fn longest_word(s: &str) -> String {
    let words: Vec<&str> = s.split_whitespace().collect()
    let mut longest = String::new();
    for word in words {
        if word.len() > longest.len() {
            longest = word.to_string();
        }
    }
    longest
}

# fn main() {
println!("{}", longest_word("Hello there")); // Hello
println!("{}", longest_word("My name is")); // name
println!("{}", longest_word("What is the longest word in this sentence")); // sentence
# }
```

### Python Equivalent

```python
def longest_word(s: str) -> str:
    words = s.split()
    longest = ''
    for word in words:
        if len(word) > len(longest):
            longest = word
    return longest

print(longest_word("Hello there")) # Hello
print(longest_word("My name is")) # name
print(longest_word("What is the longest word in this sentence")) # sentence
```
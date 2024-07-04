# Answer

## JavaScript

```javascript
function RLEEncode(str) {
  let encoded = '';
  let count = 1;
  for (let i = 0; i < str.length; i++) {
      if (str[i] === str[i + 1]) {
          count++;
      } else {
          encoded += count + str[i];
          count = 1;
      }
  }

  return encoded;
}

function RLEDecode(str) {
  let decoded = '';
  let count = 0;
  for (let i = 0; i < str.length; i++) {
      if (str[i] >= '0' && str[i] <= '9') {
          count += str[i];
      } else {
          decoded += str[i].repeat(Number(count));
          count = '';
      }
  }
  return decoded;
}
```

### Python Equivalent

```python
def rle_encode(s: str) -> str:
    encoded = ''
    count = 1
    for i in range(len(s)):
        if i + 1 < len(s) and s[i] == s[i + 1]:
            count += 1
        else:
            encoded += str(count) + s[i]
            count = 1
    return encoded

def rle_decode(s: str) -> str:
    decoded = ''
    count = ''
    for i in range(len(s)):
        if s[i].isdigit():
            count += s[i]
        else:
            decoded += s[i] * int(count)
            count = ''
    return decoded
```
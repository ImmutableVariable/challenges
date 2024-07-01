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
# Answers

## JavaScript

```js
function generatePassword(length) {
  const charset = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789";
  let password = "";
  for (let i = 0; i < length; i++) {
    const randomIndex = Math.floor(Math.random() * charset.length);
    password += charset[randomIndex];
  }
  return password;
}

// secure
function genreateSecurePassword(length) {
    return require('crypto').randomBytes(length).toString('base64')
}

console.log(generatePassword(10));
console.log(genreateSecurePassword(10));
```
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

console.log(generatePassword(10));
```

## Lua

```lua
function generate_random_password(length)
    local characters = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789!@#$%^&*()_+{}[]|:;<>,.?/~"
    local password = ""
    for i = 1, length do
        local random_index = math.random(1, #characters)
        password = password .. string.sub(characters, random_index, random_index)
    end
    return password
end
```



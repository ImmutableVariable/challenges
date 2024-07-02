# Random Password Generator

Create a simple (it doesn’t have to be cryptographically secure) random password generator. DO NOT USE IT AS A REAL ONE

# Basic Lua Example

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

local random_password = generate_random_password(12)
print("Random password:", random_password)
```

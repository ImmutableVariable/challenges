# Answers

These are my solutions, and probably wont be the most efficient, but they work.

## Javascript

```js
function isAlphabet(char) {
    return /\w+/.test(char);
}

function reverseStringWithPunctuationRecursive(str) {
    if (typeof str === "string") str = str.split(""); // Ensure str is split into an array of characters
    if (!str.length) return "";
    if (!isAlphabet(str[0])) return str[0] + reverseStringWithPunctuation(str.slice(1));
    if (!isAlphabet(str[str.length - 1])) return reverseStringWithPunctuation(str.slice(0, -1)) + str[str.length - 1];
    return str[str.length - 1] + reverseStringWithPunctuation(str.slice(1, str.length - 1)) + str[0];
}

// or 

function reverseStringWithPunctuation(str) {
    const chars = str.split('');

    const reversedAlphabets = chars.filter(c => isAlphabet(c)).reverse();

    let alphaIndex = 0;

    const result = chars.map(c => isAlphabet(c) ?  reversedAlphabets[alphaIndex++] : c);

    return result.join('');
}
```

## Go

```go
func isAlphanumeric(c rune) bool {
	return c >= 'a' && c <= 'z' || c >= 'A' && c <= 'Z' || c >= '0' && c <= '9'
}

func reverseStringPreservePunctuation(s string) string {
	r := []rune(s)
	for i, j := 0, len(r)-1; i < j; i, j = i+1, j-1 {
		for !isAlphanumeric(r[i]) && i < j { 
			i++ 
		}
		for !isAlphanumeric(r[j]) && i < j { 
			j--
		}

		r[i], r[j] = r[j], r[i]
	}
	return string(r)
}
```

## Python

```python
def reverse_string_preserve_punctuation(s):
    characters = list(s)
    left_index = 0
    right_index = len(characters) - 1

    while left_index < right_index:
        if not characters[left_index].isalnum():
            left_index += 1
        elif not characters[right_index].isalnum():
            right_index -= 1
        else:
            characters[left_index], characters[right_index] = characters[right_index], characters[left_index]
            left_index += 1
            right_index -= 1

    return ''.join(characters)
```
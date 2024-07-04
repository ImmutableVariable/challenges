# Answers

## Javascript

```javascript
function reverseOddWords(string) {
    const words = string.split(' ');
    words.map((word, index) => {
        if (word.length % 2 !== 0) {
            words[index] = word.split('').reverse().join('');
        }
    });

    return words.join(' ');
}
```

## Haskell

```hs
reverseOddWords :: String -> String 
reverseOddWords = unwords . map (\x -> if odd (length x) then reverse x else x) . words
```

## Python

```python
def reverse_odd_words(s: str) -> str:
    return ' '.join([word[::-1] if len(word) % 2 != 0 else word for word in s.split()])
```
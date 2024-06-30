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
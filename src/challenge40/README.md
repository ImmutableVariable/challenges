# Morse Code Translator

Write two functions, one to encode a string to Morse code, and another to decode Morse code back to a string. The Morse code table is provided below as a dictionary.

```javascript
morse_code = {
  'A': '.-', 'B': '-...', 'C': '-.-.', 'D': '-..', 'E': '.', 'F': '..-.',
  'G': '--.', 'H': '....', 'I': '..', 'J': '.---', 'K': '-.-', 'L': '.-..',
  'M': '--', 'N': '-.', 'O': '---', 'P': '.--.', 'Q': '--.-', 'R': '.-.',
  'S': '...', 'T': '-', 'U': '..-', 'V': '...-', 'W': '.--', 'X': '-..-',
  'Y': '-.--', 'Z': '--..', ' ': ' ', '0': '-----',
  '1': '.----', '2': '..---', '3': '...--', '4': '....-', '5': '.....',
  '6': '-....', '7': '--...', '8': '---..', '9': '----.',
  '&': '.-...', "'": '.----.', '@': '.--.-.', ')': '-.--.-', '(': '-.--.',
  ':': '---...', ',': '--..--', '=': '-...-', '!': '-.-.--', '.': '.-.-.-',
  '-': '-....-', '+': '.-.-.', '"': '.-..-.', '?': '..--..', '/': '-..-.'
}

encodeMorse('Hello World!'); // .... . .-.. .-.. ---   .-- --- .-. .-.. -.. -.-.--
decodeMorse('.... . .-.. .-.. ---   .-- --- .-. .-.. -.. -.-.--'); // HELLO WORLD!
```

## Idea from:
[Edabit](https://edabit.com/challenge/5bYXQfpyoithnQisa)
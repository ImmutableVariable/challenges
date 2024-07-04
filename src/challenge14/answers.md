# Answer

## Javascript

```js
function getRomanNumberalStringFromN(n) {
    const romanNumerals = [
        ['M', 1000],
        ['CM', 900],
        ['D', 500],
        ['CD', 400],
        ['C', 100],
        ['XC', 90],
        ['L', 50],
        ['XL', 40],
        ['X', 10],
        ['IX', 9],
        ['V', 5],
        ['IV', 4],
        ['I', 1]
    ];

    let result = '';

    for (const [numeral, value] of romanNumerals) {
        while (n >= value) {
            result += numeral;
            n -= value;
        }
    }

    return result;
}
```

### Python Equivalent

```python
def get_roman_numberal_string_from_n(n: int) -> str:
    roman_numerals = [
        ['M', 1000],
        ['CM', 900],
        ['D', 500],
        ['CD', 400],
        ['C', 100],
        ['XC', 90],
        ['L', 50],
        ['XL', 40],
        ['X', 10],
        ['IX', 9],
        ['V', 5],
        ['IV', 4],
        ['I', 1]
    ]

    result = ''

    for numeral, value in roman_numerals:
        while n >= value:
            result += numeral
            n -= value

    return result
```
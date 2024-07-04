# Answer

## Javascript 

```js
function isAnagramWithSorting(str1, str2) {
    str1 = str1.toLowerCase()
    str2 = str2.toLowerCase()
    if (str1 === str2) return true
    if (str1.length !== str2.length) return false
    return str1.split('').sort().join('') === str2.split('').sort().join('')
}

function isAnagram(str1, str2) {
    str1 = str1.toLowerCase()
    str2 = str2.toLowerCase()
    if (str1 === str2) return true
    if (str1.length !== str2.length) return false
    const frequency = new Map()
    for (let i = 0; i < str1.length; i++) {
        frequency.set(str1[i], (frequency.get(str1[i]) || 0) + 1)
        frequency.set(str2[i], (frequency.get(str2[i]) || 0) - 1)
    }
    return [...frequency.values()].every(freq => freq === 0)
}
```

### Python Equivalent

```python
def is_anagram(str1: str, str2: str) -> bool:
    str1 = str1.lower()
    str2 = str2.lower()
    if str1 == str2:
        return True
    if len(str1) != len(str2):
        return False
    frequency = {}
    for i in range(len(str1)):
        frequency[str1[i]] = frequency.get(str1[i], 0) + 1
        frequency[str2[i]] = frequency.get(str2[i], 0) - 1
    return all(freq == 0 for freq in frequency.values())
```
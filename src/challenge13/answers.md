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


# Answer

## Javascript

```js
function getPrimeNumbersUpToN(n) {
    const primes = [];
    for (let i = 2; i < n; i++) {
        let isPrime = true;
        for (let j = 2; j <= Math.sqrt(i); j++) {
            if (i % j === 0) {
                isPrime = false;
                break;
            }
        }
        if (isPrime) {
            primes.push(i);
        }
    }
    
    return primes;
}

function isPandigital(number) {
    const splitNumber = number.toString().split("");
    const splitNumberLength = splitNumber.length;
    const uniqueDigits = new Set(splitNumber);

    if (splitNumberLength > 10) return false; // it cannot have more than 10 because that would repeat 
    if (uniqueDigits.size !== splitNumberLength) return false;

    return true;
}

function longestPandigitalPrimeToN(n) {
    const pandigitalPrimes = getPrimeNumbersUpToN(n).filter((value) => {
        return isPandigital(value);
    })

    return pandigitalPrimes[pandigitalPrimes.length - 1]
}
```
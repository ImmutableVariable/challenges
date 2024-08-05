# Answer

## Javascript 

```js
function prime_factor(n) {
    let factors = [];
    
    if (n <= 1) {
        return factors;
    }

    // while the factor is even, 
    // 2 is always the smallest prime number
    while (n % 2 === 0) {
        factors.push(2);
        n /= 2;
    }

    for (let i = 3; i <= Math.sqrt(n); i += 2) {
        while (n % i === 0) {
            factors.push(i);
            n /= i;
        }
    }

    // the remaining number is prime if it is greater than 2
    if (n > 2) { 
        factors.push(n);
    }

    return factors;
}
```
# Answer

## JavaScript (basic)

```javascript
function isAPrimeNumberRecursive(n, i = 2) {
    if (n <= 2) return n === 2;
    if (n % i === 0) return false;
    if (i * i > n) return true;
    return isAPrimeNumberRecursive(n, i + 1);
}
```

## JavaScript (Solovay–Strassen primality test)

```javascript
function modPow(base, exponent, modulus) {
    let result = 1;
    base = base % modulus;
    while (exponent > 0) {
        if (exponent % 2 === 1) result = (result * base) % modulus;
        exponent = Math.floor(exponent / 2);
        base = (base * base) % modulus;
    }
    return result;
}

function jacobi(a, n) {
        if (n <= 0 || n % 2 === 0) return 0;
        a = a % n;
        let t = 1;
        while (a !== 0) {
            while (a % 2 === 0) {
                a = a / 2;
                let r = n % 8;
                if (r === 3 || r === 5) t = -t;
            }
            let temp = a;
            a = n;
            n = temp;
            if (a % 4 === 3 && n % 4 === 3) t = -t;
            a = a % n;
        }
        if (n === 1) return t;
        return 0;
}

function isAPrimeNumber(n, k = 10) {
    for (let i = 0; i < k; i++) {
        let a = Math.floor(Math.random() * (n - 2)) + 2;
        let x = jacobi(a, n);
        if (x === 0 || modPow(a, (n - 1) / 2, n) !== ((x % n) + n) % n) {
            return false;
        }
    }
    return true;
}
```
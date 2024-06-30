# Answer

## JavaScript

```javascript
class RSA {
    constructor(p = 61n, q = 53n) {
        this.p = p;
        this.q = q;
        this.n = this.p * this.q;
        this.λ = this.lcm((this.p - 1n), (this.q - 1n));
        this.e = 17n; // 1 < e < λ and coprime with λ
        this.d = this.modInverse(this.e, this.λ); 
    }

    lcm(a, b) {
        return (a * b) / this.gcdExtended(a, b)[0];
    }

    getPublicKey() {
        return [this.n, this.e];
    }

    getPrivateKey() {
        return [this.n, this.d];
    }

    gcdExtended(a, b) {
        if (a === 0n) {
            return [b, 0n, 1n];
        }
        const [g, x1, y1] = this.gcdExtended(b % a, a);
        const x = y1 - (b / a) * x1;
        const y = x1;
        return [g, x, y];
    }

    modInverse(a, b) {
        let [g, x] = this.gcdExtended(a, b);
        if (g !== 1n) {
            throw 'Modular inverse does not exist';
        }
        else {
            return (x % b + b) % b;
        }
    }

    encrypt(m, publicKey) {
        return (m ** publicKey[1]) % publicKey[0];
    }

    decrypt(c, privateKey) {
        return (c ** privateKey[1]) % privateKey[0];
    }
}

const rsa = new RSA();
const publicKey = rsa.getPublicKey();
const privateKey = rsa.getPrivateKey();

const message = 54n;
const encryptedMessage = rsa.encrypt(message, publicKey);
const decryptedMessage = rsa.decrypt(encryptedMessage, privateKey);

console.log('Message:', message);
console.log('Encrypted Message:', encryptedMessage);
console.log('Decrypted Message:', decryptedMessage);
```

# Answer

## Javascript - Node.js

```javascript
const crypto = require('crypto');
const assert = require('node:assert');

const message = 'Hello World!'

// Generate a ECDH key pair
// these would be different for each transmission or reception
const transmitterEncryptionKeyPair = crypto.generateKeyPairSync('x25519')
const receiverEncryptionKeyPair = crypto.generateKeyPairSync('x25519')

// Diffie-Hellman key exchange to compute their shared secret
// this would then be ran through a KDF to generate a longer key for encryption
const transmitterSecret = crypto.diffieHellman({
    privateKey: transmitterEncryptionKeyPair.privateKey,
    publicKey: receiverEncryptionKeyPair.publicKey
})

const receiverSecret = crypto.diffieHellman({
    privateKey: receiverEncryptionKeyPair.privateKey,
    publicKey: transmitterEncryptionKeyPair.publicKey
})

// they should both equal the same...
assert.strictEqual(transmitterSecret.toString('hex'), receiverSecret.toString('hex'))

/// 
/// Generating the shared keys to the specified length
///
const transmitterEncryptionDerivedKey = crypto.createHash("BLAKE2s256").update(transmitterSecret).digest()
const recieverDecryptionDerivedKey = crypto.createHash("BLAKE2s256").update(receiverSecret).digest()

assert.strictEqual(transmitterEncryptionDerivedKey.toString('hex'), recieverDecryptionDerivedKey.toString('hex'))

/// 
/// Shared Initialization Vector
///
const iv = crypto.randomBytes(12)

///
/// ENCRYPTION
///
const cipher = crypto.createCipheriv('aes-256-gcm', transmitterEncryptionDerivedKey, iv)

let encrypted = cipher.update(message, 'utf8', 'hex') + cipher.final('hex')

const authTag = cipher.getAuthTag()

///
/// DECRYPTION
///
const decipher = crypto.createDecipheriv('aes-256-gcm', recieverDecryptionDerivedKey, iv)

decipher.setAuthTag(authTag)

let decrypted = decipher.update(encrypted, 'hex', 'utf8') + decipher.final('utf8')

assert.strictEqual(message, decrypted) // these now should equal

console.log('Message:', message)
console.log('Decrypted:', decrypted)
```
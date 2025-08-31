While creating a web and mobile application, whenever we design a feature the main thing to be kept in mind must to have a golistic approach, that means the feature must be designed in such a manner so that it will work on all platforms.

Architecture of encryption -
1. generate the AES that is Advanced encryption Standard encryption key in frontend that is -> React , React native
2. Geneate RSA i.e. Rivest-Shamir-Adleman public key and private key in backend
3. Share the RSA public key with frontend
4. Encrpt the AES key with RSA public key
5. Encrpt data to send with AES key
6. Send the encrypted data and encrypted AES key to backend
7. Backend will use RSA private key to decrypt the encrypted AES key to retrieve the AES key
8. Use retrieved AES key to decrypt encrypted request data

Problem
For generating the AES keys and generating the RSA keys and encrypting the AES key using RSA keys, there is a default crypto module available as part of core node js module. Since React has dependency of node under the hood there is no much problem to generate and encrypt the keys and also there is no need for additional package as well. But when it comes to React native there is no support for node core modules. So upon various explorations nothing seem to workout like replacing packages like react-native-rsa-native, crypto-browserify, react-native-fast-crypto, react-native-quick-crypto which are indeed good for standalone encryption but trying to make it compatible with crypto it became a tedious process.
So here node-forge package is used

Advanced Encryption Standard (AES)
It is a highly trusted encryption algorithm used to secure the data converting it into the unreadable form without the proper key. Developed by NIST in 2001. Uses various key lengths to provide the security against the unauthorized access
1. AES is block cipher
2. It has various length of key i.e 128/192/256
3. Encrypts data in blocks of 128 bits each


Encryption algorithm are divided into 2 categories -->
Block and stream cipher
A block cipher is an encryption algorithm that takes a fixed size input, and produces. a cipher text of b bits. If the input is larger than b bits, it can be divided further.

✅ 1. Generate AES Key (React / React Native)import forge from 'node-forge';

export const generateAesKey = () => {
  const aesSalt = forge.random.getBytesSync(16); // 16 bytes salt
  const keyPassPhrase = forge.random.getBytesSync(16); // random key phrase

  const aesKey = forge.pkcs5.pbkdf2(
    keyPassPhrase,           // password or passphrase
    aesSalt,                 // salt
    ENCRYPTION_AES_ENC_KEY_OPTIONS.iterations, // e.g., 10000
    ENCRYPTION_AES_ENC_KEY_OPTIONS.keySize     // e.g., 32 for 256-bit AES
  );
  return aesKey;
};


What's happening?

AES (Advanced Encryption Standard) is symmetric — same key for encryption and decryption.

You're deriving an AES key using PBKDF2 (Password-Based Key Derivation Function 2):

This makes the key generation cryptographically secure by mixing a password and salt with multiple iterations.

This function is client-side, so both React and React Native need support for the forge library.

In React, this is okay.

In React Native, this often fails or behaves inconsistently due to lack of Node-like APIs (e.g., buffer, crypto core modules).


✅ 2. Generate RSA Key Pair (Server-side in Node.js)const forge = require('node-forge');

const rsaKeyPair = forge.pki.rsa.generateKeyPair({ bits: BITS }); // e.g., 2048 or 4096
const publicKeyPem = forge.pki.publicKeyToPem(rsaKeyPair.publicKey);
const privateKeyPem = forge.pki.privateKeyToPem(rsaKeyPair.privateKey);

What's happening?

RSA key pair is generated server-side using node-forge.

BITS defines the strength (2048-bit is secure for most cases).

PEM format = Base64-encoded string with header/footer, suitable for transport.

The public key is shared with the client.

The private key remains on the server.

✅ 3. Encrypt AES Key with RSA Public Key (Client-side React / React Native)
import forge from 'node-forge';

export const encryptAesKey = (receivedpublicKeyPem: string, aesKey: string) => {
  try {
    const publicKey = forge.pki.publicKeyFromPem(receivedpublicKeyPem);
    const encryptedAesKey = publicKey.encrypt(aesKey, 'RSA-OAEP'); // Encrypt AES key
    return forge.util.encode64(encryptedAesKey); // Encode to Base64 for safe transfer
  } catch (error) {
    console.error('Encryption error:', error);
    throw error;
  }
};

What's happening?

The AES key (a raw string of bytes) is encrypted with the public RSA key using RSA-OAEP (Optimal Asymmetric Encryption Padding) — more secure than PKCS#1 v1.5.

The encrypted data is Base64-encoded for transport (e.g., sending over network).

This function is client-side and depends on forge.

🟨 React: No major issues.

🟥 React Native: This is tricky. React Native doesn't support native crypto APIs out of the box. Even forge may not work well due to missing:

Buffer

Secure random bytes

Native CSPRNG

window.crypto (not available like in browsers)


✅ 4. Decrypt AES Key using RSA Private Key (Server-side in Node.js)const decryptedAesKey = rsaKeyPair.privateKey.decrypt(
  forge.util.decode64(encryptedAesKey),
  'RSA-OAEP'
);


Challenges in React Native

Node.js core module support is missing:

No crypto, Buffer, or native CSPRNG.

forge tries to polyfill but doesn't always succeed.

Incompatible libraries:

react-native-rsa-native – can generate keys and encrypt/decrypt, but doesn't work smoothly with forge.

crypto-browserify, react-native-fast-crypto, react-native-quick-crypto – are partial replacements but either too heavy, hard to install, or fail at runtime.

Workarounds:

Offload crypto-heavy operations (RSA key encryption/decryption) to server.

Use Web Crypto API via react-native-webview.

Use native modules via bridging (write custom native code).

Or move to fully server-managed encryption with minimal key handling on the client.

✅ Recommendations

Use RSA key encryption on the server only — clients just send AES keys unencrypted over a secure channel (HTTPS).

If client-side encryption is a must:

Use a lightweight, React Native-compatible crypto library (e.g., react-native-simple-crypto).

Or push RSA encryption to the server: client sends AES key over HTTPS, server encrypts it and stores.
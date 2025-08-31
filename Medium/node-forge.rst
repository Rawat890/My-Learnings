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
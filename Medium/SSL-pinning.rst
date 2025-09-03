Secure Socket Layer
SSL certificate creates a foundation of trust by establishing a secure connection between the web server and the client or browser
The connection ensures that all the data that is passed between the web server and the browsers remain private and integral. ssl certificates have a key pair, which is a public and private key.
These keys work together to establish the encrypted connection. The certificate also contains (Subject) which is the identity of the certificate/website owner

SSL certificate pinning is the process of associating the host with its certificate or public key. once you know the host certificate public key, you pin it to that host.

What is certificate ?
A certificate is a file that encapsulates the information about server that owns the certificate. It's similar to the identification card, such as passport. The structire uses X.509 standards. It holds many information -
1. Subject: provides name of the entity (computer, user, device etc.)
2. Serial Number: Provides a unique identifier for each certificate that a CA issues
3. Issuer: Provides a unique name for the CA that issued the certificate.
4. Valid From: Provides the date and time when the certificate becomes valid.
5. Valid To: Provides the date and time when the certificate is no longer considered valid.
6. Public Key: Contains the public key of the key pair that goes with the certificate.
7. Algorithm Identifier: Indicates the algorithm used to sign the certificate.
8. Digital Signature: A bit string used to verify the authenticity of the certificate.
9. Version: Version number of certificate
10. TimeStamp: This shows the time when certificate was created

There are several commonly used filename extensions foe digital certificates -
(a) PEM (Privacy enchanced mail)
A Base-64 encoding, whose file extension is .pem. The certificate information is enclosed between “ — — -BEGIN CERTIFICATE — — -” and “ — — -END CERTIFICATE — — -”
(b) PKCS (Public-key-cryptography standards)
Used to exchange public and private objects in a single file. Its extensions are .p7b, .p7c, .p12 etc.
(c) DER(Distinguished Encoding Rules): A binary encoding, whose file extensions are .cer, .der and .crt.


Why do we need ssl pinning ?
SSL pinning allows the application to trust only the valid or pre-defined certificate or public key. The app developer uses SSL pinning technique as an additional security layer fir app traffic. 
As normally, the application trusts custom certificate and allows the application to intercept the traffic.


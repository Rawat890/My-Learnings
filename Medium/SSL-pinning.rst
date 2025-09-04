Secure Socket Layer
SSL certificate creates a foundation of trust by establishing a secure connection between the web server and the client or browser
The connection ensures that all the data that is passed between the web server and the browsers remain private and integral. ssl certificates have a key pair, which is a public and private key.
These keys work together to establish the encrypted connection. The certificate also contains (Subject) which is the identity of the certificate/website owner

SSL certificate pinning is the process of associating the host with its certificate or public key. once you know the host certificate public key, you pin it to that host.
It helps prevent man-in-the-middle (MITM) attacks by ensuring that the app only communicates with servers that possess a specific certificate or public key, thereby thwarting attempts to intercept or tamper with the communication.

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
SSL pinning allows the application to trust only the valid or pre-defined certificate or public key. The app developer uses SSL pinning technique as an additional security layer for app traffic. 
As normally, the application trusts custom certificate and allows the application to intercept the traffic.

Restricting the set of trusted certificates through pinning prevents the attackers from analyzing the functionality of the app and the way it communicates with the server.

HOW SSL WORKS ?

How SSL works?
1. Client machine sends a connection request to server, server listens the request.
2. Server gives response including public key and certificate.
3. Client checks the certificate and sends a encrypted key to server.
4. Server decrypt the key and sends encrypted data back to the client machine.
5. Client receives and decrypt the encrypted data.

Types of SSL Pinning(What to Pin)?
* Pin the certificate: You can download the server’s certificate and put this in your app bundle. At runtime, the app compares the server’s certificate to the one you’ve embedded.
* Pin the public key: You can retrieve the certificate’s public key and include it in your code as a string. At runtime, the app compares the certificate’s public key to the one hard-coded hash string in your code.

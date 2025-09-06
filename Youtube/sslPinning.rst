

Computer ---------------------->Internet------------------>Website
example.com                                                example.com
email: a@gmail.com ---->        Hacker can hack            (server)
passowrd: ******. ----->        while data flows

So to Avoid Them, SSL/TLS is used
Secure Socket Layer / Transport Layer Security
Cryptographic protocols that is designed to provide secure communication over a computer network
TLS is successor to SSL

Why to use SSL Pinning ?
It maintains the 
confidentiality - only accessible at endpoint -----> uses encryption method
integrity - not modified ----> uses Hashing method
authentication - verifying identity of the parties ----> uses certificates method

ENCRYPTION METHOD --> converting data to unreadable form i.e. cipher text
Types-
Symmetric - same key are used for encryption and decryption
Asymmetric - keys are different

Real world flow 

Computer ---------------------->Internet------------------>Website
                                                             | (public and private key)
  public key <-----------------------------------------------     
  Key = 3                                                    decrypt (key = 3).   
                                                             | DEF -> ABC
  ABC -> DEF  ----------------------------------------------> 
  (encrypted)                                           


Difference between Symmetric and Asymmetric key -
Symmetric - fast and more elefficient , suitable for large data, challenging key distribution
Asymmetric -  slower and suitable for small data, More secure

Hybrid Encrytion - use both

Asymmetric algorithms - DSA, RSA ECC
Asymmetric algorithms - AES, RC4

HASHING - is the process of converting the data into fixed-size string of characters as a sequemce of numbers and letters
DEMO (37) = 4 + 5 + 13 + 15

Computer ---------------------->Internet------------------>Website
example.com                                                example.com
                                Hacker                     DEMO (37) (VERIFY using hashing)
                                                        (what if hacker also chnaged the key 37)
So, we cn apply high security standard -> MAC (Message Auth Code)
                                          Message + Code
                                            DEMO  + KEY123 ---> DEMOKEY123 (84)



Computer ----------------------> CA (Cerificate authority)------------------>Website
example.com                                      Cerificate provided         example.com
    |                                      ^ ----------------------------------|   ^
    |                                      |___________________________________|   | 
    |                                               provides public key            |
    |                                                                              |
    |                                                                              |
    ________________________________________________________________________________
                         sends certificates to browser 
                         browser checks from its list if i's a va;id certificate


Who provides digital certificates -> various organzation like GoDaddy, GlobalSign Atlas
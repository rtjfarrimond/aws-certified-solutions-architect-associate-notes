SSL and SSL Certificates
------------------------
Notes from [this article](http://www.steves-internet-guide.com/ssl-certificates-explained/)

Intro
-----
- Secure Sockets Layer (SSL)
- Transport Layer Security (TLS)
    - Transport layer is layer 4 in OSI model
- SSL and TLS are protocols that procide secure communications over a network
    - Commonly used in web browsing and email

What is TLS?
------------
- Based on SSL
- Developed as a replacement in response to vulnerabilities in SSLv3
- SSL is still the commonly used term, but generally used in reference to
  TLS today

Security Provided
-----------------
- SSL/TLS provides data encryption, data integrity, and authentication
- When using SSL/TLS, we can be confident that:
    - Nobody has read your message
    - Nobody has changed your message
    - You are communicating with the intended person (server)
- When sending a message between two parties:
    - How do we know that nobody has read the message?
    - How do we know that nobody has altered the message?
- Solutions to above problems:
    - Encrypt it - any thrid arty viewing the message will just see gibberish
    - Sign it - allows recipient to have confidence in the sender's identity
                and therefore that the original contents have not been changed
    - Both of these processes require the use of *keys*
- Keys are simply numbers
    - 128 bit is common
    - Combined with message using algorithm such as RSA to encrypt or sign

Symmetrical Keys and Public and Private Keys
--------------------------------------------
- Today most encryption methods employ public and private keys
- The public and private key arrangement replaced *symmetrical keys*, which
  were in commmon use previously
- Symmetrical keys
    - Used to both encrypt and decrypt, just like a physical key that locks and
      opens a door.
    - Anybody who manages to obtain a copy of your key can use it to decrypt
      your messages.
- Public and private keys
    - Seperate keys used to encrypt (public) and decrypt (private) messages
    - The two keys are mathematically related
    - If the same kind of arrangement were used in the physical world, you
      could lock your door and safely leave the keys in the lock, since the
      same key could not then be used to unlock the door.
    - Very secure arrangement used in all modern encryption / signature systems

Keys and SSL Certificates
-------------------------
- SSL/TLS uses public and private key system for data encryption and integrity
- Public keys can me made available to anyone.
    - How do you know that a public key belongs to the entity that it claims?
    - The answer is to use a digital certificate
- Certificates serve the same purpose that a passport does
    - Passport - provide a link between person and photo verified by a trusted
                 authority (passport office)
    - Certificate - provide a link between a public key and an entity such as
                    a business or domain name, verified (signed) by a trusted
                    third party (certificate authority)
    - Provides a convenient way of distributing trusted public encryption keys

Obtaining a Digital Certificate
-------------------------------
- You get a digital certificate from a recognised *certificate authority (CA)*
- Fill out appropriate forms, add public keys, send to the CA
- CA does some checks (depends on authority) and sends back your keys enclosed
  in a certificate.
    - Certificate is signed by the CA, which is what guarantees the keys
- Now when somebody wants your public keys you send them the certificate
    - They verify the signature, and if it succeeds they can trust your keys

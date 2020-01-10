Object Encryption
=================
- *Exam LOVES questions about S3 security*
- There are 4 methods of encrypting objects in S3
    - SSE-S3: encrypts objects using keys handled and managed by AWS
    - SSE-KMS: leverages AWS Key Management Service to manage encryption keys
    - SSE-C: when you want to manage your own encryption keys
    - Client side encryption
- *Super important* to understand which ones are adapted to which situation for the exam

SSE-S3
------
- Keys handled and managed by AWS S3
- Object encrpyted server side
- AES-256 encryption type
- HTTP or HTTPS accepted
- Must send header `"x-amz-server-side-encryption":"AES256"` in PUT requests
- S3 creates a `Managed Data Key` used to encrypt incoming objects
- Object stored in bucket after encyption

SSE-KMS
-------
- Keys handled and managed by AWS KMS
- KMS advantages:
    - User control
    - Audit trail
- Server side encryption
- HTTP or HTTPS accepted
- Must send header `"x-amz-server-side-encryption":"aws:kms"` in PUT requests
- S3 uses a KMS Customer Master Key (CMK) to encrypt incoming objects
- Object stored in bucket after encyption

SSE-C
-----
- Server side encryption
- Keys fully managed by the customer outside of AWS
- S3 does not store the provided encryption key
- HTTPS must be used
- Encryption key (client side data key) must be provided in the HTTPS headers for every HTTPS request made
    - Exam does not ask what the header is
- S3 uses the provided client side data key to encrypt incoming objects
- Object stored in bucket after encyption
- Client provided data key is discarded after used for encryption

Client side encryption
----------------------
- Must use client library such as Amazon S3 Encryption Client
- Clients must encrypt the data themselves before sending to S3
- Clients must decrypt the data themselves when retrieving from S3
- Customer fully manages the keys and encryption cycle

Encryption in transit (SSL)
---------------------------
- AWS S3 exposes:
    - HTTP endpoint (non-encrypted)
    - HTTPS endpoint (encrypted in flight)
- HTTPS is recommended (mandatory for SSE-C)
- Encrytion in flight also referred to as SSL / TLS in the exam

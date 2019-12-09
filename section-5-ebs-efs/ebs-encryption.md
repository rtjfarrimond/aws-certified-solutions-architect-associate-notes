EBS Encryption
--------------
- When you crea an dencrypted EBS volume, you get:
    - Data at rest inside the volume is encrypted
    - Data in flight between the instance and volume encrypted
    - All snapshots are encrypted
    - All volumes created from the snapshot are encrypted
- Encryption all handled behind the scenes, nothing to do
- Has a very minimal impact on latency
- Leverages keys from KMS (AES-265)
- Copying an unencrypted snapshot allows encryption

Encrypt an unencrypted EBS volume
---------------------------------
- Create an EBS snapshot of the volume
- Encrypt the EBS volume (using the `copy` function)
- Create a new volume from the snapshot
    - The volume will also be encrypted
- Now the encrypted volume can be attaached to the original insstance



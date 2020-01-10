Buckets and Objects
===================

Buckets
-------
- Allows to store objects (files) in buckets (directories)
- Buckets must have a globally unique name (across all AWS accounts)
- Defined at the region level
- Naming convention
    - Lowercase
    - No underscores
    - 3-63 chars long
    - Not an IP
    - Must start with alphanumeric

Objects
-------
- Objects (files) have a key, which is the FULL path
    - my-bucket/my_file.txt
    - my-bucket/folder/my_file.txt
- No concept of 'directories' within buckets, just long key names that contain slashes ('/')
- Object values are the content of the body
    - Max size is 5TB
    - Have to use 'multi-part upload' for files > 5GB in size
        - *Popular exam question!*
- Objects have metadata, list of text k:v pairs - whatever you want, system or user metadata
- Objects have Tags, list of unicode k:v pairs
    - Can have up to 10
    - Userful for security / lifecycle
- Version ID (if versioning is enabled)

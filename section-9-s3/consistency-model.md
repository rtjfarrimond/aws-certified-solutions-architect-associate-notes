S3 Consistency Model
====================
- Read after write consistency for PUTs of new objects
    - As soon as the object is written, we can retrieve it
    - This is true *only if* there was no previous GET to check if the object existed.
        - In this case it would be eventually consistent
- Eventual consistency for DELETEs and PUTs of existing objects
    - If we read an object after updating, we might get the old version
    - If we read an object after deleting, we may get the object successfully for a short time afterwards

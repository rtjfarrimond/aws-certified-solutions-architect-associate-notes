RDS Security
------------
*Super important, know this by heart for the exam!*
- Encryption at rest
    - Can only be enabled at RDS instance creation
    - If you need to make an unencrypted instance encrypted, same process as
      for EBS volume:
        - snapshot -> copy snapshot as encrypted -> create db from snapshot
- Your responsibility:
    - Ensure the ports / IP / security group inbound rules are configured
    - In-database user creation and permissions
    - Creating a db with or without public access
    - Ensuring parameter groups or db configured to only allow SSL connections
- AWS responsibility
    - Prevent SSH access
    - Patch the DB
    - Patch the OS
    - Prevent audit underlying instance

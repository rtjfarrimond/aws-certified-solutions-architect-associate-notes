IAM Introduction
----------------
- IAM stands for 'Identity access management'
- Whole AWS security is there:
    - Users
    - Groups
    - Roles
- Root account should NEVER BE USED!
- Users must be created with proper permissions
    - 'Policies' define these permissions, specified in JSON
- IAM is at the heart of AWS

- Users
    - Usually a physical person
- Groups
    - Contain users
    - Usually specified by function (admin, devops, ...), or team (eng, product, ...)
- Roles
    - Internal usage within AWS resources
    - Roles are given to machines, not people
- Policies
    - JSON documents
    - Define what users, groups, and roles can do.

- IAM has a Global view, it applies accross all regions
- MFA can be set up
- There are some predefined 'managed' policies available from AWS
- Principal of least priviledge applies for users, groups, and roles

- IAM Federation
    - Enterprises can integrate their own repo of users with IAM
    - Allows users to login to AWS using their company credentials
    - Identity Federation uses the SAML standard

- IAM 101 Braindump
    - One user per physical person
    - One role per application
    - Credentials should never be shared
    - Never write credentials in code EVER!
    - NEVER use the root account except in initial account set up.

S3 Security
===========
- Two types:
    - User based
        - IAM policies
    - Resource based
        - Bucket policies - allows cross account
        - Object access control list (ACL) - finer grain
        - Bucket access control list (ACL) - less common

Bucket Policies
---------------
- JSON based policies with four main elements
    - Resources - buckets and objects
    - Action - Set of APIs (e.g. put, get)
    - Effect - Allow or Deny
    - Principal - Account or user to apply policy to
- Use bucket policy to
    - Grant public acces
    - Force encryption at upload
    - Grant access to another account (cross account)
- The AWS policy generator web tool can be used to generate JSON S3 Buckey policies (as well as policies for other resources)
    - https://awspolicygen.s3.amazonaws.com/policygen.html

IAM Policies
------------
- Take precedence over bucket policies, so can be used to grant / revoke permissions to specific users

Other security
--------------
- Networking
    - Supports VPC endpoints for instances in VPC without www internet
- Logging and audit
    - S3 access logs can be stored in another S3 bucket
    - API calls can be logged in CloudTrail
- User security
    - MFA can be required in versioned buckets to delete objects
    - Signed URLS - only valid for a limited time (ex. premium video service for logged in users)
        - *Popular in the exam*

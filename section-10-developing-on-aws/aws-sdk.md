AWS SDK
=======
- Perform actions on AWS from application code
- SDK available in many languages
    - The AWS cli is a wrapper around the python SDK (botocore / boto3)
- If a default region is not configured, value will be us-east-1

Credentials Security
--------------------
- Recommended to use *default credential provider chain*
    - Works seamlessly with:
        - Local development, uses credentials from ~/.aws
        - Instance profile credentials using IAM roles
        - Environment variables (AWS_ACCESS_KEY_ID, AWS_SECRET_ACCESS_KEY_ID)
    - Obviosuly, never store credentials in code

Exponential backoff
-------------------
- Applies to rate limited APIs
- Any API call that fails because of too many calls will need to be retried
    - Wait some initial time n, then double between fails
    - E.g. n = 2: 2, 4, 8, 16, ...
- Retry mechanism included in SDK API calls

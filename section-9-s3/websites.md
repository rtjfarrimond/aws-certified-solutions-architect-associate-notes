S3 Websites
===========
- S3 can host static websites and have them accessible on the web
- The website URL will be:
    - <bucket-name>.s3-website-<AWS-region>.amazonaws.com
    - OR
    - <bucket-name>.s3-website.<AWS-region>.amazonaws.com
- If you get a 403 Forbidden response, make sure the bucket policy allows public reads
- UI has an option to enable static website hosting
- Must ensure that the block public access options for policies is disabled

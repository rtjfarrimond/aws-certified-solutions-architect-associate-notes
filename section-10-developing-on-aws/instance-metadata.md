EC2 Instance Metadata
=================
- Powerful, but not well known
- Allows instances to know about themselves without using an IAM role for that purpose
- Accessed by an instance on the followung URL:
    - http://169.254.169.254/latest/meta-data
- Can retrieve the IAM Role name from metadata, but not the IAM policy

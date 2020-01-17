AWS CLI on EC2
==============

The BAD way!
------------
- Could just run `aws configure` on EC2 same way as when configuring on development machine.
- This will work, but is *super insecure*!
- *NEVER EVER put personal credentials on EC2*
  - These should only ever be on your personal machine
  - If the instance is compromised, then so is your personal account (IAM user)
  - If the EC2 is shared, other people may perform AWS actions whilt impersonating you

The Correct Way
---------------
- Use AWS IAM roles attached to EC2 instances
- IAM roles come with a policy defining what the instance should be allowed to do
- Instances use these profiles automatically without additional config
- This is AWS best pracctice, and 100% should be the way this is done

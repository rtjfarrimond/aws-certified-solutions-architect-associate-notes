Cross-account AMI Copy
----------------------
- *This is a frequent exam question!*
- You can share an AMI with another AWS account.
- Sharing an AMI does not affect the ownership
    - If the AMI is copied, then the copier is the owner of the new AMI
- To copy an AMI shared with you by another account, the owner of the
  source AMI must grant read permission for the storage that backs the
  AMI (either EBS snapshot, or S3 bucket)

- Limits:
    - You can't copy an encrypted AMI that was shared with you. If the
      underlying snapshot and encryption key were shared with you, you
      can copy the snapshot while re-encrypting with your own key.You
      now own the copied snapshot and can register it as a new AMI.
    - You can't copy an AMI with an associated `billingProduct` code that
      was shared with you from another account. This includes Windows
      AMIs and AMIs from the AWS Marketplace. To copy a shared AMI with
      a `billingProduct` code, launch an EC2 instance using the shared
      AMI, and then create an AMI from the instance.

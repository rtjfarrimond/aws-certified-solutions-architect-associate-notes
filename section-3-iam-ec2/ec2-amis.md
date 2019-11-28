EC2 AMIs
--------
- We've seen AWS comes with base images avaiable in various Linux
  and even windows flavours.
- What if we want to create our own? That's an AMI, an image to use to
  create our instances.
- N.B. AMIs are region specific, not Global!

Why create custom AMI?
----------------------
- Pre-install package dependencies
    - Faster boot time (no need to run user data script)
- Configure with monitoring / enterprise software
- Security concerns - control over machines in network
- Control of maintenance and updates of AMIs over time
- Active Directory integration out of the box
- Install your app ahead of time for faster deploys when auto-scaling
- Use a third party AMI optimised for an app, db, etc.

Using public AMIs
-----------------
- Can leverage freely available AMIs
- Can pay for other people's AMIs by the hour
    - These people have optimised the software
    - The machine is easy to run / configure
    - You rent 'expertise' from AMI creator
- AMIs can be found and published on the Amazon Marketplace

Warning!
--------
- Do not use an AMI you do not trust!
- AMIs can come with malware or not be secure for enterprise
- Do due dilligence.

AMI Storage
-----------
- AMIs take space. They are stored in S3.
- AMIs are private by default and locked for account / region
- Can make them publicly avaialable on the AMI Marketplace

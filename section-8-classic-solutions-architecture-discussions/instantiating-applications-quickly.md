Instantiating Applications Quickly
==================================
- When launching a full stack (EC2, EBS, RDS) it takes time to:
    - Install applications
    - Insert initial (or recovery data)
    - Configure everything
    - Launch the application
- Can take advantage of cloud to speed this up

EC2 Instances
-------------
- Use a *Golden AMI*
    - Install apps, OS dependencies, etc beforehand and launch instance from golden AMI
- Bootstrap using User Data
    - For dynamic config (DB urls, etc), use User Data scripts
- Hybrid
    - mix Golden AMI and User Data (Elastic Beanstalk)

RDS Databases
-------------
- Restore from snapshot - db will have schemas and data ready!

EBS Volumes
-----------
- Restore from snapshot - disk will be formatted and have data!

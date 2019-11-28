EC2 User Data
-------------
- It is possible to bootstrap instances using an EC2 User Data script.
- 'Bootstrapping' means leaunching commands when a machine starts.
- The script is only run once, at the instance first start
- EC2 user data is used to automate boot tasks, such as:
    - Installing updates
    - Installing software
    - Downloading common files from internet
    - Anything else you can think of
- The EC2 user data script runs with the root user.


EC2 User Data - Hands-on
------------------------
- We are going to write an EC2 user data script to automate the steps
  performed in the last hands on session:
    - Use yum to install system updates
    - Use yum to install Apache web server
    - Configure a hello world index.html page to serve

- In the EC2 console, click 'Luanch instance' and select Amazon Linux 2 AMI
- Click through to configure instance, and scroll down to Advanced Details
- Select the 'as text' radio button and paste the script at
  `aws-solutions-architect-associate/resources/code/ec2-fundamentals/ec2-basics.sh` in here
- Select the same security group as used in the last hands-on
- Select the same key pair as used in the last hands-on and launch
- Once the instance has launched, the hello world example should be
  viewable by accessing the instance via DNS or public ip in browser.

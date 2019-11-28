EC2 Introduction
----------------
- EC2 one of AWS most popular offerings
- Mainly consists of
    - Renting virtual machines (EC2)
    - Storing data in virtual drives (EBS)
    - Distributing load across machines (ELB)
    - Scaling services using auto-scaling groups (ASG)
- Knowing EC2 is fundamental to understanding how cloud works
    - This ability to start a machine straight away and scale proportional
      to load is where the revolution began.
    - Need to start here to understand later on, how Serverless
      makes a difference.

EC2 Hands-on
------------
- Launching an EC2 instance running Linux
    - We will launch a virtual server using the console
    - We'll get a high level approach to the various parameters
    - We'll learn how to start / stop /terminate the instance.

- Parameters
    - The 'subnet' allows you to choose in which availability zone to
      launch the instance, or select 'no preference' to leave this
      at AWS discretion.
    - Tags - sets of key value pairs that you can add to an instance
      to help keep track of resources.
        - If you add the 'Name' tag, value will be visible in the console

Connecting to EC2 instances with SSH
------------------------------------
- Requires that port 22 is open in the security group.
- Using the `.pem` key file that the instance was initialised with
- COMMON EXAM QUESTION: When a `.pem` file is first downloaded, it has
  0644 permissions. This needs to be reduced to 0400 permissions
  (root read only) before the remote host allows you to connect using it.
- Once `.pem` file permissions have been appropriately set, connect using:

        ssh -i <.pem file path> ec2-user@<host-name-or-public-ip>

    - The `-i` ssh flag allows you to pass an 'identity fille', in this
      case our `.pem` key.


Connecting to EC2 using EC2 Instance Connect
--------------------------------------------
- Requires that port 22 is open in the security group.
- This only works with Amazon Linux 2 AMI instances.
- In the console, select your instance and click the 'Connect' button.
- In the modal, select 'EC2 Instance Connect' and click 'Connect'
- A new tab will open with a virtual terminal connected to the instance.

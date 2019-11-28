Introduction to Security Groups
-------------------------------
- Fundamental of AWS network security
- Control how traffic is allowed into or out of our EC2 machines.
- It is the most fundamental skill to learn to troubleshoot
  AWS networking issues.
- In this lecture we learn how to use them to allow inbound
  and outbound ports.

- In the EC2 hands-on, we:
    - created an EC2 instance and security group
    - created a security group and attached it to our EC2 instance
    - configured an inbound rule to allow ssh over tcp on port 22
- We can view all of this in the AWS console.
- If we remove the inbound rule, we will not be able to ssh into
  the instance, our request will time out.

Security Groups Deeper Dive
---------------------------
- Security groups act as a firewall on Ec2 instances
- They regulate:
    - access to ports
    - authorised IP ranges (v4 and v6)
    - control of inbound network traffic
    - control of outbound network traffic
        - Defaults to allow instance to connect to any IP on any port
- Security groups good to know
    - Can be attached to multiple instances
    - Locked down to a region / VPC combination
    - They are logically outside the instance, if a security group
      blocks traffic, the instance will never see it.
    - *It is good practice to maintain one seperate security group
      for ssh access*
    - If the instance is not accessible (i.e. ssh time out), then this
      is probably an issue with the security group inbound rules.
    - If the instance gives a connection refused error, then it is an
      appliaction error, or an error with the instance (i.e. not launched)
    - All inbound traffic is blocked by default.
    - All outbound traffic is authorised by default.

Referencing other security groups
---------------------------------
- It is possible to add inbound rules that reference other security groups.
- This has the effect of allowing inbound traffic from other instances
  that have this security group attached.
- We will cover this in more detail when we look at load balancers.

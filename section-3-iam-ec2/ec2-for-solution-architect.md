EC2 for Solutions Architects
----------------------------
- Instances billed by the second (after first minute)
    - t2.micro is free tier
- Connect to instances using ssh
- Configure security group to lock down access to your own IP
    - Timeout issues => security group issues. Is the port open?
- Permission issue on the ssh key => chmod 0400 <pem-file>
- Security groups can reference other security groups instead of IP
  ranges (*very popular exam question!*)
- Know the difference between public, private, and elastic IP addresses
- Can customize an EC2 instance at boot using EC2 User Data

- Know the 4 EC2 launch modes
    - On demand
    - Reserved
    - Spot instances
    - Dedicated hosts

- Know the basic instance types
    - R for RAM optimised
    - C for CPU optimised
    - M for a medium between R and C
    - I for I/O optimised
    - G for GPU instances
    - T2/T3 for burstable CPU

- You can create AMIs to pre-install software on EC2
    - Faster boot as does not rely on user data script running
    - Can be copied accross regions and accounts

- EC2 instances can be started in placement groups:
    - Cluster - fast and dangerous, instances on same hardware
    - Spread - spread instances over hardware for fault tolerance
    - Partition - like spread, but more instances and partitioned over
                  different racks in each AZ.

Autoscaling Groups
------------------
- Goals of ASGs:
    - scale out and back in, adding and removing instances to match load
    - ensure we have a min and mac number of instances running
    - automatically register new instances to a load balancer

- ASGs have the following attributes
    - Launch configuration
        - AMI + instance type
        - EC2 user data
        - EBS volumes
        - Security groups
        - SSH key pair
    - Min size / max size / initial capacity
    - Netwrok and subnet info
    - LB info
    - Scaling policies - what will cause the group to scale?

- Auto scaling alarms
    - Possible to scale an ASG based on CloudWatch alarms
    - Alarms triggered by monitoring metrics, e.g. average CPU
    - *Metrics are computed for the overall ASG instances*

- Auto scaling new rules
    - now possible to define 'better' autoscaling rules directly managed by EC2
    - Target average cpu usage
    - Number requests on the ELB per instance
    - Average network in
    - Average network out
    - These rules are easier to est up and can make more sense

- Autoscaling custom metrics
    - Can create custom metrics, e.g. number of connected users:
        - Create metric in application on EC2 and send to CloudWatch PutMetric API
        - Create CloudWatch alarm to react to high / low values
        - Use the alarm as the ASG scaling policy

- ASG brain dump
    - scaling policies can be on CPU, network, etc and also on custom metrics or schedules (i.e. when usage patterns are known)
    - ASGs use launch configurations and tou update an ASG by proviging a new launch configuration
    - IAM roles attached to an ASG will get assigned to EC2 instances
    - ASGs are free, just pay for instances created
    - If an instances is terminated for any reason, ASG will spin up again. Extra safety.
    - ASG can terminate instances an LB marks as unhealthy and hence replace them

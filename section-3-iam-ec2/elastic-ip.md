Elastic IP
----------
- EC2 instances by default have a dynamic public IP that can change
  when an instance is restarted.
- If for some reason you need a fixed public IP, Elastic IP provides
  a static public IP v4 address that can be associated with an instance.
- This is generally a poor architectural decision however, as DNS names
  and load balancers are both preferable to provide a fixed means to
  connect to an instance.

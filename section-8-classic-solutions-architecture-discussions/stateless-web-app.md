Stateless Web App - WhatIsTheTime.com
=====================================
- Allows people to know what time it is
- Don't need a DB because it is so simple
- Want to start small and accept downtime
- Want to fully scale vertically and horizontally, no downtime

Starting Simple
---------------
- Public T2 micro EC2 instance with an Elastic IP address
- User makes request, instance responds with the server time

Scaling Vertically
------------------
- As we get more users, we want to increase the capacity of the instance to deal with the load.
- We decide to upgrade to an M5 instance, which is a downtime operation
    - Take down T2 micro
    - Redeploy app on M5 instance which now has the Elastic IP attached

Scaling Horizontally
--------------------
- We are getting more popular and need to scale again
- We spin up 2 more M5 instances each with their own Elastic IP
- Our users need to be aware of all 3 public IP addresses in order to access the instances
- This is not great, so instead we set up Route 53 and remove Elastic IPs
    - Set up A record for `api.whatisthetime.com` with a TTL of 1 hour
    - Route 53 will return a list of our instances' IPs for the client to choose from

- Adding and removing instances
    - We have a TTL of 1 hour, so if an instance goes offline a user may not be able to access the application until after the TTL expires

- Adding a load balancer
    - Make EC2 instances private now
    - All instances in same AZ (because we do not know better)
    - ELB + healthchecks in same AZ
    - Security groups configured so that ELB can access instances
    - Route 53 updated: Alias record sends `api.whatisthetime.com` to the ELB
    - Manually adding and removing instances to the ELB is still difficult, so we decide to create an ASG to deal with load

- Making our app multi-AZ
    - We need to be robust to AZ outages so that our users enjoy high availability
    - Configure ELB to span all AZs in region
    - Configure ASG to deploy instances across all AZs

- Reserving Capacity
    - We now have a stable and robust architecture, but we would like to optimise costs
    - We want to have a minimum of one instance in two AZs at all times
    - We can reserve capacity to meet this need and reduce cost
    - Additional instances created in the ASG can be ephemeral, so on demand instances are fine

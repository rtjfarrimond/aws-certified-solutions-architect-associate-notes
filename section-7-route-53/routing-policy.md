Routing Policies
================

Simple Routing Policy
---------------------
- Maps a domain to one URL
- Use when need to redirect to a single resource
- Cannot attach healthchecks
- If multiple values are returned, a random one is chosen by the client
    - Client side load balancing

Weighted Routing Policy
-----------------------
- Controls percentage of requests that go to a specific endpoint
- If we have two endpoints specified and weighted 80/20, then traffic will be directed to the first host 80% of the time, and to the second 20% of the time.
- Useful for A/B testing deployments
- Helpful to split traffic between regions
- Can be associated with health checks
- One record per weight
- From cleint's perspective, unaware that there are multiple possible IPs that could resolve in the backend.

Latency Routing Policy
----------------------
- Redirect to server with least latency wrt client
- Super useful when latency for user is priority
- Latency evaluated in terms of user to designated AWS region

Failover Routing Policy (Example scenario)
------------------------------------------
- Have 2 EC2 instances; primary, secondary (disaster recovery)
- Route 53 record directs traffic to the primary and has a health check on it
- If the primary instance is marked as unhealthy, then Route 53 will failover to the secondary instance.

Geolocation Routing Policy
--------------------------
- Different from latency based
- Routes based on traffic origin location, e.g. all traffic from the UK directs to some IP
- Should create a 'default' policy, in case the origin location cannot be determined
- Can use continent or country level granularity

Multi Value Routing Policy
--------------------------
- Use when routing traffic to multiple resources and want to associate healtch checks with records
- Up to 8 healthy records are returned for each multi-value query
- NOT a substitute for an ELB
- If an instance starts failing health checks, its IP will not be returned in the multi-value response.

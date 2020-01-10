Route 53 Overview
-----------------
<<<<<<< HEAD
- Managed domain name system (DNS)
- DNS is a collection of rules and records, w
=======
- Managed Domain Name System (DNS)
- Global service, does not require region selection
- DNS - collection of rules and records that allow a client to reach a server via URLs
- Most common records in AWS are:
    - A - URL -> IPv4
    - AAAA - URL -> IPv6
    - CNAME - URL -> URL
    - Alias - URL -> AWS resource

- Route 53 can use:
    - public domain names that you own or buy
    - private domain names that can be resolved by instances in your VPC

- Advanced features include:
    - Load balancing via DNS (aka 'client load balancing')
    - Health checks (though limited)
    - Routing policy: Simple, failover, geolocation, latency, weighted, multi-value

- You pay $0.50 / month / hosted zone
>>>>>>> c8b2cae7a3018eaf6926fe3352d44d44cf23d910

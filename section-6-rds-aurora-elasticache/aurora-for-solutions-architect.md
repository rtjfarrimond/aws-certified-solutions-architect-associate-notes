Aurora for the Solutions Architect
----------------------------------
- Can user IAM aut for Aurora
- Aurora Global databases span multiple regions and enable disaster recovery
    - One primary region
    - One DR region
        - Can be used for lower latency reads
        - < 1 second replication lag on average
        - Can failover to DR if primary region fails
- If not using Global Databases, can create cross-region read replicas
    - Will still help with latency, but not DR


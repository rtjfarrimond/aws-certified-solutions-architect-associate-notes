Aurora Overview
---------------
- Proprietary DB from AWS
- Compatilble with MySQL and Postgres
    - Drivers work as if they were one of these
- AWS cloud optimized
    - 5x performance over mysql on rds
    - 3x performance over postgres on rds
- Storage grows automatically - starts at 10GB up to 64TB
- Can have up to 15 read replicas (sub 10ms replication lag)
- Failover is instantaneous
- 20% more expensive than other options, but more efficient

Aurora High Availability and Read Scaling
-----------------------------------------
- 6 copies of your data across 3 AZ
    - Only needs 4/6 copies available for writes
    - Only needs 3/6 copies available for reads
    - Self-healing with peer-to-peer replication
    - Storage striped across 100s of volumes
- One instance takes writes (master)
    - Automatic failover in less than 30 seconds if master unavailable
- Master + up to 15 read replicas serve reads
    - Can failover to master if needed
- Support for cross region replication

Aurora DB Cluster
-----------------
- Shared storage volume across all instances
- Master instance is only one that writes to the volume
- Aurora provides a 'Writer Endpoint' - DNS name that points to master
- Can have up to 15 read replicas and can configure auto-scaling
- A 'Reader Endpoint' also exists - provides connection load balancing over all of the read replicas
    - Load balancing happens at the *connection* level, not at the statement level.
    - *Need to know this for the exam!*

Features of Aurora
------------------
- Automatic failover
- Backup and recovery
- Isolation and security
- Industry compliance
- Auto-scaling
- Automated patching with zero downtime
- Advanced monitoring
- Routine maintenance
- Backtrack - restore data to any point in time without using backups

Aurora Security
---------------
- Very similar to RDS
- Encryption at rest using KMS
- Automated backups, snapshots and replicas are encrypted
- Encryption in flight using SSL (same process as MySQL or Postgres)
- Auth using IAM
- You are responsible for protecting the instance with security groups
- You can't SSH into the instance

Aurora Serverless
-----------------
- No need to choose an instance size
- Only supports MySQL and Postgres
- Helpful for unpredictable workloads
- DB cluster starts, shutsdown, and scales based on CPU / connections
- Can migrate from Aurora Cluster to Aurora Serverless and vice versa
- Usage measured in Aurora Capacity Units (ACU)
- Billed in 5 minute increments of ACU
- Some features not supported in serverless mode, be sure to check docs.

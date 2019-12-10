RDS Overview
------------
- relational database service
- AWS managed database service
- Supports:
    - PostgreSQL
    - Oracle
    - MySQL
    - MariaDB
    - Microsoft SQL Server
    - Aurora (AWS proprietary database)
- Advantage over just deploying a database on EC2
    - Fully managed service
    - OS patching
    - Continuous backup and restore
    - Monitoring dashboards
    - Read replicas for improved read performance
    - Multi AZ setup for disaster recovery (DR)
    - Maintenance windows for upgrades
    - Vertical and horizontabl scaling capability
    - Drawback: Cannot SSH directly into your instances

Read Replicas
-------------
- Provide read scalability
- Can create up to 5 read replicas
- Can be cross AZ and even cross region
- *Asynchronous* replication provides eventual consistency
- Replicas can be promoted to their own database
    - Very quick and easy way to replicate a database
- Applications must update the connection string to leverage read replicas
    - *Sometimes asked in the exam*
    - So need to properly configure the app to use read replicas as needed

RDS Multi AZ (Disaster Recovery)
--------------------------------
- App still talks to master instance for all reads and writes
    - Only this DNS name exposed
- Master *synchronously* replicates to a *standby* instance in another AZ
- DNS name has automatic failover to standby incase of master failure
    - Standby instance promoted to the master
- No manual intervention needed in apps, as the switch happens at the DNS
- Not used for scaling!
    - But can be combined with Read Replicas

RDS Backups
-----------
- Automatically enabled in RDS
- Automated backups
    - Daily full snapshot
    - Capture transaction logs in real time
        - PRovides ability to restore to any point in time
    - 7 day retention by default, can increase up to 35
- DB Snapshots
    - Manually triggered
    - Retain the backup indefinitely

RDS Encryption
--------------
- *The exam loves to ask security questions!*
- Encryption at rest with AWS KMS - AES-256 encryption
- SSL certs to encrypt data to RDS in flight
- To enforce SSL:
    - PostgreSQL: `rds.force_ssl=1` in the AWS RDS Console (Parameter Groups)
    - MySQL: Within the db `GRANT USAGE ON *.* TO 'mysqluser'@'%' REQUIRE SSL;`
    - *Quite a popular exam question*
- To connect using SSL:
    - Provide the SSL Trust certificate (can be downloaded from AWS)
    - Provide SSL oprions when connecting to database
    - Can connect with SSL even if SSL not enforced

RDS Security
------------
- RDS databases are usually deployed within a private subnet
- Works by leveraging security groups controlling who can communicate
    - Same concept as EC2
- IAM policies help control who can *manage* AWS RDS
- Username and password can be used to login to the database
    - IAM users can now be used too (for MySQL / Aurora)

Aurora
------
- Aurora is a proprietary technology from AWS
- PostgreSQL and MySQL both supported as AuroraDB
    - Means that drivers will work as if Aurora was a PostgreSQL or MySQL db
- AWS cloud optimised
    - Claims 5x performance improvement over MySQL on RDS
    - Claims 3x performance improvement over PostgreSQL on RDS
- Storage automatically grows in 10GB increments up to 64TB
- Can have 15 replicas, with faster replication process (sub 10ms lag)
- Multi-AZ by default with instantaneous failovers
    - High availability native
- Costs 20% more than RDS, but is more efficient, so should cost less overall

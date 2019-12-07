EBS volumes
-----------
- What is an EBS volume
    - An EC2 instance loses its root volume (main drive) when it is terminated
    - Sometimes need a way to store data past the life of the instance
    - An EBS (Elastic Block Store) Volume is a *network drive* you can attach to instances while they run
    - Allows instances to persist data
    - Databases would be an example use case

- EBS Volume
    - It is a network drive (i.e. not physical)
        - Uses network to communicate with instance, can be some latency
        - Can be detached from an instance and quickly reattached to another
    - Locked to an AZ
        - To move a volume across, first need to snapshot it
    - Have a provisioned capacity (size in GBs and IOPS)
        - Billed for *provisioned capacity*, not for used
        - Can increase over time

- EBS volumes come in 4 types
    - GP2 (SSD): General purpose, balance price and performance
    - IO1 (SSD): Highest performance, for mission-critical low-latency or high-throughput workloads
    - ST1 (HDD): Low cost for frequently accessed throughput intensive loads
    - SC1 (HDD): Lowest cost, designed for less frequently accessed workloads

    - Volumes characterised by size, throughput, and IOPS (I/O ops per second)
    - Only GP2 and IO1 can be used as boot volumes

EBS Volume Type Use Cases
-------------------------
- GP2
    - Recommended for most workloads
    - System boot volumes
    - Virtual desktops
    - Low-latency interactive apps
    - Dev and test environments
    - 1 GiB - 16 TiB
    - Small GP2 can burst IOPS to 3000
    - Max IOPS is 16000
    - Rule: 3 IOPS per GB, so at 5334GB already maxed out IOPS

- IO1
    - Critical apps the need sustained IOPS performance
        - or > 16,000 per volume (GP2 limit)
    - Large database workloads
        - i.e. Cassandra, SQL server, PostgreSQL, Oracle
        - 4 Gib - 16Tib
        - IOPS is provisioned (PIOPS) - min 100, max 32,000
            - Nitro instances max at 64,000
        - Max ration provisioned IOPS to volume size in Gib is 50:1

- ST1
    - Streaming workloads requiring fast thruput at low cost
    - Big data, data warehouse, log processing
    - Apache Kafka
    - Cannot be a boot volume
    - 500 GiB - 16 TiB
    - Max IOPS 500
    - Max thruput of 500MiB/s - can burst

- SC1
    - Thruput-oriented storage for large volumes of infrequently accessed data
    - Scenarios where lowest cost is important
    - Cannot be a boot volume
    - 500 GiB - 16 TiB
    - Mac thruput 250MiB/s - can burst
    - Like  less good ST1

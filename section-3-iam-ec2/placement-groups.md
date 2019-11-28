EC2 Placement Groups
--------------------
- Can control the EC2 instance placement strategy using placement groups.
- When creating a placement group, specify one of the following strategies:
    - Cluster - clusters instances into low-latency group in a single AZ
        - High performance, high risk
    - Spread - spreads instances across underlying hardware
        - Max 7 instances per group per AZ
        - Critical applications
    - Partition - Spreads instances across many partitions within an AZ
        - Partitions rely on different set of hardware racks
        - Scales to 100s of EC2 instances per group (Hadoop, Cassandra, Kafka)

Cluster
-------
- All instances on same rack in single AZ
- Pros: Great network (10Gbps between instances)
- Cons: If the rack fails, all instances fail
- Use case:
    - Big data job that needs to finish fast
    - App that needs very low latency and high network thruput

Spread
------
- Pros:
    - Can spread across multiple AZs
    - Reduce risk of similtaneous failure
- Cons:
    - Limited to 7 instances per AZ per placement group
- Use case:
    - Applicaion that needs high availablilty
    - Critical applications where instance failures must be isolated

Partition
---------
- Partitions are sets of racks
- Up to 7 partitions per AZ
- Up to 100s of instances
- Instances in partitions do not share racks with other partitions
- A partition failure may affect many instances, but isolated from
  other partitions.
- Instances can access partition metadata
- Use cases: HDFS, HBase, Cassandra, Kafka

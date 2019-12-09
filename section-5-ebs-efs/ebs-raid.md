EBS RAID Options
----------------
- EBS already has redundancy, replicated within AZ
- But mounting volumes in parllel using RAID settings will allow you to:
    - Increase IOPS to 100,000 IOPS
    - Mirror EBS volumes
- RAID possible so long as OS supports it
- Some RAID options are:
    - RAID 0
    - RAID 1
    - RAID 5 (not recommended for EBS - see AWS docs)
    - RAID 6 (not recommended for EBS - see AWS docs)
- We will epxlore RAID 0 & 1

RAID 0
------
- *Need to know about this*
- Icrease performance
- One logical volume is backed by two EBS volumes
- Writes to disk will go to either one volume or the other
- Combining 2+ volumes in this way gives you the total available disk space and I/O
- This also increases the risk, since if one disk fails then all of the data is failed
- Use cases:
    - App that needs lots of IOPS but does not need fault tolerance
    - A database that already has replication built in
- Using RAID 0 we can have a very big disk with lots of IOPS
- Example:
    - Two 500 GiB EBS io1 volumes w/ 4k PIOPS each creates...
    - 1000 GiB RAID 0 array with 8k PIOPS and

RAID 1
------
- Increase fault tolerance
- One logical volume backed by two EBS volumes
- Write to both volumes at the same time
- Mirroring one valume to another
    - If one disk fails, logical volume still working
- We have to send all of the data to two EBS volumes at the same time
  so this uses 2x network throughput since EBS volumes are network drives

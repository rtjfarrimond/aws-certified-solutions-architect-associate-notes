EBS RAID Configuration
----------------------

RAID 1
------
- Increase fault tolerance
- One logical volume backed by two EBS volumes
- Write to both volumes at the same time
- Mirroring one valume to another
    - If one disk fails, logical volume still working
- We have to send all of the data to two EBS volumes at the same time
  so this uses 2x network throughput since EBS volumes are network drives



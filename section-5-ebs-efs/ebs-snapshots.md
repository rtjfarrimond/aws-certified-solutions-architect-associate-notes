EBS Snapshots
-------------
## Very important exam topic!

- Incremental - only backup changed blocks
- Uses IO of the volums, so shouldn't run whilst application is handling lots of traffic
- Snapshots stored in S3, but won't directly see them (like Elasticsearch service)
    - Billed for this
- Not necessary to detach volume to snapshot, but recommended
- Max 100,000 snapshots per account
- Can copy across AZ and / or region
- Can make AMI from snapshot
- EBS volumes restored from snapshots need to be pre-warmed
    - Using `fio` or `dd` command to read entire volume
- Snapshots can be automated with amazon lifecycle manager

EBS Migration
-------------
- EBS volumes locked to specific AZ
    - Need to snapshot and copy if needed in different AZ

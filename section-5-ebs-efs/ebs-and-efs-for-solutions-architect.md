EBS and EFS for the Solutions Architect
---------------------------------------
- EBS volumes can be attached to only one instance at a time
- They are AZ local
- Can snapshot an existing volume and recreate it in another AZ
    - This process is called 'migration'
- EBS backups use IO and should not be run while application is serving a
  lot of traffic
- Root EBS volumes of instances are deleted when an instance is terminated
  by default, thought this can be disabled
- If disk IO is high => increase the EBS volume size (for GP2)
    - If you have IO1 volume, can directly increase IOPS right away

- EFS allows mounting 100s of instances
- Instances can be mounted across all AZs
- EFS share website files
- EBS gp2, optimise cost for local instance storage

- Can use a snapshot of EBS volume in a custom AMI for faster deploy on ASG

- *Need to understand for the exam* what the difference is between EFS vs EBS vs instance store
    - EFS
        - network file system
        - share across instances and AZs
        - More expensive
    - EBS
        - local storage
        - like a virtual USB drive over network, can be detached
          and reattached to other instances
    - Instance store
        - Volume on an instance itself
        - Ephemeral storage
        - Cannot be reattached to other instances
        - Higher performance than EBS

Stateful Web App - MyWordpress.com
==================================
- Fully scalabe WP site
- Want to acces site and display picture uploads
- User data, blog content stored in MySQL DB scaled globally

Architecture
------------
- As before, 3 tier with Route 53 -> Multi-AZ ELB -> Multi-AZ ASG -> Multi-AZ RDS
- Can also replace RDS with Aurora MySQL to take advantage of
    - More read replicas, multi-AZ
    - Global databases
    - Disaster recovery

Storing images with EBS
-----------------------
- If we had only one EC2 instance we could back this with an EBS volume and store uploaded images here.
- When we have more than one image this becomes an issue, since EBS volumes cannot be shared by multiple images.
    - Following upload via one instance, subsequent requests to retrieve may fail if directed to another instance.


Storing images with EFS
-----------------------
- We can use the same architecture as the previous section, but use EFS network drives instead of EBS volumes.
- This would allow the same file system to be shared by all of our instances.
- EFS creates ENIs (Elastic Network Interfaces), which allow all of our instances to access the network drive.

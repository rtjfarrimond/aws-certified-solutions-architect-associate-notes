Stateful Web App - MyClothes.com
================================
- Allows people to buy clothes online
- Has a shopping cart
- Hundreds of users at the same time
- Need to scale, maintain horizontal scalability and keep application as stateless as possible
- Users should not lose their shopping cart
- Store user details in a database

Architecture
------------
- Like stateless web app from last lecture
- Route 53 directs traffic to an ELB, which backs on to instances in a multi-AZ ASG
- Application running on instances is stateless, so user can lose cart contents following a request that is routed to a different instance than a previous request

Stickiness
----------
- Aka, Session Affinity
- ELB feature, requests from the same origin are always routed to same instance.
- However, if the instance is terminated for some reason, then the user still loses their shopping cart contents

User Cookies
------------
- State is maintained in client browser as cookie
- Cookie sent in requests, so server always knows the content of the cart
- Out HTTP requests are now heavier, as we send more data each time we add to cart
- Security concerns, cookie could be intercepted and modified
    - Need to ensure validation of cookies
- Cookies can only be up to 4kb, so we are limited here.

Server Session
--------------
- Client sends a `session_id` in web cookie
- ElastiCache cluster backs instances in ASG
- Store / retrieve data from ElastiCache using session_id

Storing user data
-----------------
- Instances in ASG backed by RDS
- RDS used to store and retrieve user data

Scaling Reads
-------------
- Most common access pattern for our users is browsing the website
- We want to scale reads in order to optimise for this use case
- Have a master RDS instance for writes
- Enable read replicas for RDS and read from these
    - Can have up to 5 of these or 15 for Aurora

Scaling Reads (Alternative) - Write Through
-------------------------------------------
- Instances in ASG backed by Elasticache and RDS
- App first checks Elasticache for data it needs
    - Cache hit: serve the cached data
    - Cache miss: read data from RDS, add to cache, serve the data
- This reduces load on RDS, but now we have to manage cache invalidation

Surviving Disasters
-------------------
- Ensure all of the following are multi-AZ
    - ELB
    - ASG
    - Elasticache
    - RDS

Security Groups
---------------
- ELB open HTTP/HTTPS from anywhere
- Restrict traffic to instances in ASG from ELB only
- Restrict traffic to Elasticache from ASG instances only
- Restrict traffic to RDS from ASG instances only

EC2 Instance Launch Types
-------------------------
- NEED TO KNOW FOR EXAM!
- On demand instances: short work loads, predicatble pricing
- Reserved instances: long workloads, 1 year +
- Convertible reserved instances: long workloads with flexible instances
- Scheduled reserved instances: launch within time window you reserve
- Spot instances: short workloads. Cheap, can lose instances.
- Dedicated instaces: no other customers share the hardware
- Dedicated hosts: book entire physical server, control instance placement

On demand
---------
- Pay for what you use (billing per second after first minute)
- Highest cost, but no upfront payment.
- No long term commitment.
- Recommended for short-term, uninterrupted workloads, where you
  cannot predict how the application will behave.
  - Great for auto-scaling applications.

Reserved instances
------------------
- Up to 75% discount compared to on demand
- Pay upfront for what you use with long term commitment
- Reservation can be 1-3years
- Reserve specific instance type
- Recommneded for steady state usage applications (i.e. database)

Convertible reserved instance
-----------------------------
- As above, but can change the instance type
- Up to 54% discount wrt on demand

Scheduled reserved instances
----------------------------
- Launch within a specific time window, i.e. for predictable peaks

Spot instances
--------------
- Up to 90% discount
- You bid and get the instances as long it is under that bid
- Price varies based on demand from other bidders
- Instances are reclaimed with 2 min notification warning when spot
  price rises above your bid.
- Used for Batch jobs, big data analysis, or workloads that are resiliant
  to failures.
- Not for critical workloads or available applications.

Dedicated hosts
---------------
- Physical dedicated EC2 server for your use
- Full control of EC2 instance placement
- Visibility into underlying sokets / physical cores of hardware
- Allocated to your account for a 3 year period reservation
- More expensive than on demand
- Useful for software with complicated licensing models (BYOL)
- Useful for companoes with strong complience needs.

Dedicated instances
-------------------
- Instances running on hardware dedicated to you
- May share hardware with other instances in the same account
- No control over instance placement (can move hardware after stop / start)


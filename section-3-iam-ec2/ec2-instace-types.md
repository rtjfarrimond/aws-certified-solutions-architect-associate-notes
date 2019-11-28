EC2 Lauch Types - Main ones
---------------
- There are lots of types available, but these ones we need to know
  for the exam.
- R: applications that need a lot of RAM - in memory caches
- C: applications that need good CPU - compute / databases
- M: applications that are balanced (think 'medium') - general / web app
- I: applications that need good I/O (instance storate) - databases
- G: applications that need a GPU - video rendering / machine learning

- T2/T3: burstable instances (up to a capacity)
- T2/T3 unlimited: unlimited burst

- Real world tip, use https://ec2instances.info/

Burstable Instances
-------------------
- Burst means that overall the instance has ok CPU performance
- When the machine has a spike in load for example, it can 'burst' and
  CPU can be VERY good.
- If machine bursts, it spends burst credits
- If all credits are spent, the CPU becomes BAD
- Credits are accumulated over time when a machine is not bursting.

- Burstable instances can be great for handling unexpected traffic and
  getting assurance that it will be handled.
- If you consistently run low on credits, you man need a different,
  non-burstable instance such as an M or C type.
    - Monitor e.g. using cloudwatch

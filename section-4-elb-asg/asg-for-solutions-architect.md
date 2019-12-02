Autoscaling Groups for the Solutions Architect
----------------------------------------------
- ASG default termination policy
    - Find the AZ with the most instances
    - If there are multiple instances, delete the one with oldest launch configuration
- ASG tries to balance the number of instances across AZ by default

- Scaling cooldowns
    - Ensures that ASG does not launch or terminate additional instances before previous scaling activity takes effect
    - In addition to default cooldowns, we can create cooldowns that apply to a specific 'simple scaling policy'
        - Common use case: scale in based on a specific criteria or metric
        - Because this terminates instances autoscaling needs less time to determine whether to terminate additional instances
    - If app is scaling up and down multiple times per hour, modify the ASG cool-down timers and CW alarm period that defines the scale in

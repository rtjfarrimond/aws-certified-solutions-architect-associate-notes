Beanstalk Overview
==================

Developer problems on AWS
-------------------------
- Managing infrastructure
- Deploying code
- Configuring DB, LB, etc
- Scaling concerns

- Most web apps have the same 3 tier architecture (ALB + ASG + DB)
- Developers want code to run consistently across instances and environments

AWS ElasticBeanStalk
--------------------
- Developer centric view of application deployment on AWS
- Uses all components we've seen before
- All in one view that is easy to make sense of
- Still have full control over config
- BeanStalk is free, just pay for underlying instances

- Managed service
    - Instance config / OS handled by BeanStalk
    - Deployment strategy is configurable but performed by BeanStalk
    - Just application code is the developer's responsibility

- Three architecture models
    - Single instance deployment - good for dev environment
    - LB + ASG - good for prod and preprod web apps
    - ASG only - good for non-web apps in production (workers etc)

- Has three components:
    - Application
    - Application version: each deployment gets assigned a version
    - Environment name

- Deploy application versions to environments and can promote application versions to the next environment
- Feature to rollback an environment to previous appliction version
- Full control over lifecycle of environments

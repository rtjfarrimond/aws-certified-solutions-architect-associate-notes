Elasticache for the Solutions Architect
---------------------------------------
- Security
    - Redis supports 'Redis AUTH' (username / password)
        - Required SSL in-flight encryption to be enabled and used
    - Memcached supports SASL authetication (advanced)
    - Does not support IAM authentication
    - IAM policies on ElastiCache only used for AWS API-level security
        - i.e. creats / delete cahce etc

- Patterns
    - Lazy loading - all read data is cached, data can become stale
    - Write through - application adds or updates cache when writtent to DB
    - Session store - store temporary session data in a cache (using TTL)

- "There are only two hard problems in computer science: cache invalidation
   and naming things." - Phil Karton
    - Luckily, we do not need to know about invalidation for the exam!

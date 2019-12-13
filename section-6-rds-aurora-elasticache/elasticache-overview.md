Elasticache Overview
--------------------
- Managed cache service with support for
    - Redis
    - Memcached
- Caches are in memory databases with really high performance, low-latency
- Helps to reduce load off databases for read intensive workloads
- Helps to make application stateless by storing the state in a common cache
- Write scaling using sharding
- Read scaling using replicas
- Multi AZ with failover
- AWS takes care of OS maintenance / patching, optimisations, setup, config,
  monitoring, failure recovery, and backups.
- Looks a lot like RDS because it is pretty much the same thing only for caches

Solution Architecture - DB Cache
--------------------------------
- App first queries Elasticache
    - Cache hit: Elasticache returns data
    - Cache miss: application queries RDS, then writes data back to cache
- Helps to relieve READ load on RDS
- Cache must have an invalidation strategy to ensure only most current data
  is in there.

Solution Architecture - User session store
------------------------------------------
- We have several instances of a stateless application running on > 1 hosts
- The user logs into the application, but because it is a stateless app, writes  need a mechanism by which the other hosts can know that the user is already
  logged in so they do not have to re-authenticate for each new request.
- We achieve this by backing the app with an Elasticache
    - When user logs in, the app writes the session to the cache
    - When the user next makes a request, the application instance that
      receivers the request retrieves the session from the cache and can see
      that the user is already logged in.
        - Presumably the user has a cookie or something to enable this?

Redis Overview
--------------
- Redis is an in-memory key-value store
- Sub-millisecond latency
- Cache is persistent (survives reboot) by default
- Great to host:
    - User sessions
    - Leaderboards
    - Distributed state
    - Relief pressure for databases
    - Pub / sub capability for messaging
- Multi-AZ with automated failover for disaster recovery
- Support for read replicas

Memcached Overview
------------------
- In memory object store
- Cache is not persistent, does not survive reboots
- Use cases:
    - Quick retrieval of objects from memory
    - Cache frequently accessed objects

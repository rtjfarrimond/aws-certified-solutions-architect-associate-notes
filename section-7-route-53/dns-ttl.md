DNS Records Time to Live
------------------------
- Time to Live (TTL) is a way for clients to cache response of a DNS query so as not to overload the DNS server
- Server sends TTL with response, client can cache for this long
- After cache expires, client will again query the server for an IP
    - If the IP associated with the URL changes before the TTL expires, the client will not be able to connect to the new host until TTL expired.
- TTL is configurable in Route 53

- High TTL (e.g. 24 hour)
    - Less DNS server traffic
    - Possibly outdated records
- Low TTL (e.g. 60 seconds)
    - More DNS server traffic
    - Records outdated for less time
    - Easy to change records

- TTL is *mandatory* for each DNS record

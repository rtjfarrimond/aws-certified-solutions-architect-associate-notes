Health Checks
-------------
- If `n` checks have failed then mark as unhealthy (`n` default 3)
- If `n` checks have passed then mark as healthy (`n` default 3)
- Default healthcheck interval is 30s (can set to 10s at higher cost)
- About 15 health checkers will check health
- => one request every 2 seconds on average for 30s interval
- Can have HTTP, TCP, HTTPS (no SSL cert verification) checks
- Can integrate with CloudWatch
- Can be linked to Route53 DNS queries to change behaviour

Load Balancers for the Solutions Architect
------------------------------------------
- CLB: questions on security groups, stickiness
- ALB (Layer 7 OSI)
    - Routing based on host and path
    - Support for redirect, i.e. http -> https
    - Support dynamic host port mapping with ECS
- NLB (Layer 4 of OSI)
    - Gets static IP per AZ
    - Public facing must attach Elastic IP - can help whitelist by client
    - Private facing: random private IP
    - Cross zone balancing
    - Has SSL termination

- LB security groups
    - *Very popular exam question!*
    - Use security group source filtering to allow only traffic from LB into instances

- LB SSL certs
    - Users acces LB over HTTPS -> LB access instance over HTTP in private VPC
    - LB can use X.509 cert (SSL/TLS server certificate)
        - Allows users to access over HTTPS
    - Can manage certs using ACM (AWS Certificate Manager)
        - Can create and upload on certs as alternative
    - HTTPS listener
        - Must specifiy default cert
        - Can add optional list of certs to support multiple domains
        - Clients can use SNI (Server Name Identification) to specify the hostname they reach
            - *Very popular exam question!*
        - Ability to specify a security policy to support older versions of SSL / TLS (legacy clients)

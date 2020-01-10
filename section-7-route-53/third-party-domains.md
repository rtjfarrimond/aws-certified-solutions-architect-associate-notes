Third Party Domains and Route 53
--------------------------------
- Route 53 as a registrar
    - A domain name registrar is an organisation that manages the reservation of Internet domain names
    - Domain Registrar != DNS, but Route 53 does both
- It is possible to use domains from a 3rd party registrar wiht Route 53
    - Create a Hosted Zone in Rout 53
    - Update Name Server (NS) records at 3rd party to use Route 53

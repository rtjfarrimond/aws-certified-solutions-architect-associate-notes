Load Balaner Stickiness
-----------------------
- Stickiness means same clinet always redirected to same instance behind LB
- Works with cookies which have a configurable expiration date
- Works for CLB and ALB
- Used to store user session state
- Enabling stickiness may bring imbalance to the load over backend services
- Enabled in the target group via the UI

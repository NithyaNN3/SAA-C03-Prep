### WhatIsTheTime.com
-Just tells you time

Start simple: hosted on ec2 with elastic IP
> starts getting more traffic
Scale vertically and horizontally - setup route 53 with TTL, DNS name, A record (of IPv4s), non root domain
> Instance disappears
We add load balancer with health checks
Alias record
> adding and removing instances is annoying
ASGs with rules and AZs
Upgrade to multi AZ
> we want to diminish costs
Upgrade to reserved instances instead of spot instances based on trends



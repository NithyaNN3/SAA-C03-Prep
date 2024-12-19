### WhatIsTheTime.com
Just tells you time

Start simple: hosted on ec2 with elastic IP
- starts getting more traffic
Scale vertically and horizontally - setup route 53 with TTL, DNS name, A record (of IPv4s), non root domain
- Instance disappears
We add load balancer with health checks
Alias record
- adding and removing instances is annoying
ASGs with rules and AZs
Upgrade to multi AZ
- we want to diminish costs
Upgrade to reserved instances instead of spot instances based on trends


### MyClothes.com
platform to buy clothes

Multi AZ instances with ASG and route 53
Introduce session stickiness (user goes to same instance)
User is made to store web cookies which holds shopping cart state - makes it stateless but http requests are heavier and cookies must be validated
Web cookies have a session id which is used to retrieve session data on ElastiCache
Store user data in RDS like name, address, etc
> All that users do is read content on the website
Increase RDS reads with RDS read replicas.
Lazy loading where info is stored in cache on Elasticache but you need to do cache management now.
RDS, elasticache is Multie AZ to survive disasters
> Restrict traffic
introduce security groups


### 

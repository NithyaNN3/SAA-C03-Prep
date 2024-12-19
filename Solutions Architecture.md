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


### mywordpess.com
website should access and display pictures
user data, content, available across world

same initial setup as above
We use Aurora here as RDS
Images stored on EBS volumes but we chnge to EFS with ENIs which have images of the app files.
EBS for single instance apps and EFS for distributed applications.


### Instantiating apps quickly
For ec2 use golden AMI - startup is quick as all dependencies are installed already
bootstrap user data using Beanstalk

RDS databases: restore from snapshots
EBS volumes: restore from snapshots

## Beanstalk
- complicated to manage infra, deploy code, configuration and scaling
- most apps have same architecture

Beanstalk has a developer centric view of apps
Web server tier - for making websites, etc
worker tier - to deploy workers
You can create multiple environments (like dev, stage) on it

Deployment modes: single instance vs high availability with load balancer (greater for prod)

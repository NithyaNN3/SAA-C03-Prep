## Relational database service 
- allows to create databases on the cloud

**Why RDS over deploying database on EC2?** - managed service, multiple AZ for disaster recovery, scaling capabilities, backups, monitoring dashboards, etc
RDS detects storage space automatically and scales. You have to set max storage threshold though supported by all database engines on RDS.

**RDS read replicas for read scalability** - helps scale reads on apps from dbs
- ASYNC replication - same region, multiple AZ
- SYNC replication - multi AZ - same DNS name - increased availability > no manual replication in apps needed and not used for scaling; failover
- can setup read replicas as multi AZ for disaster recovery

How to go from single AZ to multi AZ? it's a zero downtime operation, click 'modify' on db

## Amazon Aurora
IMP!
1. Proprietary technology and supports postgres and mysql
2. AWS cloud optimised so provides x perf improvement over RDS
3. grows in increments of 10gb upto 128TB
4. can have 15 read replicas and is fast
5. failovers are instantaneous
6. costs 20% more than RDS but much more efficient
7. 6 copies of your data across 3 AZ regions
8. support for cross region replication

## RDS Security:
1. At rest encryption
- Database master and replicas encryption using AWS KMS must be defined at launch time
- master is not encrypted then read replicas cant be either
- to encrypt unencrypted DB, go through DB snapshot and restore are encrypted

2. In flight
- TLS ready by default, use AWS TLS root certs on client side

3. IAM Authentication - IAM roles to connect to database
4. SGs
5. No SSH available
6. Audit logs can be enabled and sent to CloudWatch

**Proxy**
- can deploy a fully managed database proxy for RDS
- allows apps to pool and share DB connections before being sent to the DB instance to reduce stress on db resources
- enforce IAM authentication for DB

## ElastiCache
- acts as a cache - high perf, low latency - session data is written stored in this cache
- helps reduce loads off of dbs
- makes apps stateless
- elasticache involves heavy app code changes
- can use redis or memcached

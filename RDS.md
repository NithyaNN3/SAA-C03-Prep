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


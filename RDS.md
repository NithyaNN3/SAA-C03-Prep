## Relational database service 
- allows to create databases on the cloud

**Why RDS over deploying database on EC2?** - managed service, multiple AZ for disaster recovery, scaling capabilities, backups, monitoring dashboards, etc
RDS detects storage space automatically and scales. You have to set max storage threshold though supported by all database engines on RDS.

**RDS read replicas for read scalability** - helps scale reads on apps from dbs
- ASYNC replication - same region, multiple AZ
- SYNC replication - multi AZ - same DNS name - increased availability > no manual replication in apps needed and not used for scaling; failover
- can setup read replicas as multi AZ for disaster recovery

How to go from single AZ to multi AZ? it's a zero downtime operation, click 'modify' on db

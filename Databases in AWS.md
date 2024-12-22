*Throughput - amount of data transferred in a given time frame
*Latency - the time delay between user action/data request and system response
*Strong schema - a db schema that strictly enforces data integrity, validation and consistency by defining precise rules for structure and data types

## RDS
Managed PostreSQL, etc
supports read replics and multi AZ
autoscaling
provisioned RDS instance size
security through IAM, SGs, KMS, SSL intransit
managed and scheduled maintences from Amazon so downtime on db
RDS custom to customise underlying instance

USE CASES - SQL queries and transactions

## Aurora
POstgres/MySQL
data in 6 replics, 3 AZs - highly available, self healing, autoscaling
Aurora global - 16 DB instances in each region
Aurora Serverless
Aurora ML
Aurora database cloning - new cluster from existing db

## ElastiCache
managed redis/memcached
in-memory data store, subsecond latency
support for clustering and sharding
**not a good choice if you need a caching option for ongoing code changed**

USE CASES-KV store, frequent reads and less writes, cache results for DB queries, store session data for websites, cannot use SQL

## DynamoDB
proprietay tech
provisioned or on-demand capacity
can replace elasticache as kv store (use as session store for websites)
highly available, multi AZ, read & writes decoupled, transaction capability
DAX for read cache, microsecond read latency
IAM
event processing using Streams with Kineses or Lambda
Global table feature - can read/write from any region
automated backups upto 35 days
can export/import data to S3
rapidly evolve schemas on it

USE CASES- serverless app dev (small docs 100s kb), serverless cache

## S3
KV store for big objects
max size 5TB, serverless
batch operations using S3 batch

## DocumentDB
NoSQL db
compatible with MongoDB
fully managed, highly available
grows in increments of 10GB

## Neptune
full managed graph database
3 AZ repl, 15 read replicas
Streams - real time ordered seq of changes 
strict order, no duplicates
accessible in an HTTP REST API
USE CASES - send notifs when changes are made, maintain your graph data synced in another data store, replicate data across regions

## Amazon Keyspaces for Cassandra
open source nosql distributed db
store IoT devices info, time series data

## QLDB
quantum ledger db
records finance txns
fully mgd, highly avlble, repl across 3 AZ
immutable system - crypto verifiable changes
2-3x perf improvements
decentralization component

## Timestream
fully mgd, scalable, serverless time series db
store and analyse trillion events per day
encryption in transit

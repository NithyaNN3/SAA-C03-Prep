## Athena
- serverless query services to analyze data in S3
- 5$ per TB scanned
- perf improvement - columnar data
- compress data
- partitioning on s3 for easy querying
- larger files on s3 are easy to scan
- can query data on any data source using data source connectors on Lambda > results can be stored on s3

## Redshift
- OLAP - online analytical processing
- 10x perf improvement
- columnar data store
- provisioned and serverless
- leader node for query planning, compute node for performig the query and sending results
- snapshots, multi AZ for some clusters
- can restore snapshot on new cluster
- **Spectrum** - spectrum nodes perform a query from redshift on s3 without loading it

## OpenSearch
- can search any field, even partial matches
- doesnt natively support SQL
- managed or serverless clusters

## EMR
Elastic mapreduce
helps create hadoop clusters to analyze big data 
master node - manage cluster, manage health
Core node - run tasks and store data
Task node - to run tasks
On demand, reserved and spot instances available

## QuickSight
serverless ML powered biz services
fast, scablable
UC - biz analytics
in memory computation
Column level security on enterprise level

## Glue
ETL service, fully serverless

## Lake formation
for data lakes - simplify data ingestio, cataloging, access control and analytics

## Kinesis data analytics 
for SQL apps - real time analyics

Amazon managed service for Apache Flink - process and analyse data streams

## Amazon MSK for apache kafka
- holds hore memory per msg


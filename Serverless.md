Means remote managing without manual provisioning basically

## Overview
Virtual functions, dont need code - let's you run code without provisioning servers and executes code only when triggered automatically

### Limits to know
Compressed 50MB, uncompressed (code + dependencies) - 250mb, use /tmp directory to load other files at startup, size of env variables - 4kb

Execution - 
Memory allocation - 128mb - 10gb
Max execution time - 900 seconds
Env vars - 4kb
Disc capacity in function container - 512 mb to 10gb
concurrency executions - 1000

Deployment - 
Compressed 50MB, uncompressed (code + dependencies) - 250mb
env vars - 4kbs

### SnapStart
- improves lambda functions for java 11 and above
- function starts from a preinitialization point

### Customization at Edge
- edge functions - run close to users to minimize latency
- customize CDN content
- can use for SEO, website security, A/B testing
- CloudFront - CDN that accelerates delivery of static and dynamic content by caching it at edge locations
- Lambda@Edge - serverless compute feature of cloudfront that lets you run custom code close to the users

### Lambda at VPC
- lambda func run outside VPC, cant access inside
- Use case: lambda + RDS proxy


## DynamoDB
- fully managed, highly available, replicable across AZs
- NoSQL database
- scales massively
- made of tables; has PKs; infinite rows, columns - add whenever you want; max size of item - 400kb; use case - rapidly evolving schema
- provisioned mode - plan capacity before hand and pay per no. of reads/writes; possible to add auto scaling
- on demand mode - automatic scaling; pay for what you use; great for unpredictable workloads

### DynamoDB Accelerator
in memory cache; helps solve read congestion; 
stream processing
Global tables - same table at multiple regions - replication available > have to enable dynamodb streams for this

# Amazon SQS
### Messaging
Apps need to communicate between themselves
1. Sync comms - app to app
2. Async - app to queue to app

## SQS
Basically a queued message processor - **decouples** producers and consumers
- oldest offering
- no limit on no. of messages in queue
- retention of messages: 4-14 days
- low latency
- limitation of msg size
- can have duplicate and out of order msgs
- Scales automatically

**Producers** - SDK > message > SQS 
**Consumers** - apps on ec2, servers or lambda - **polls** sqs for messages then process and delete them

- encryption on flight
- at rest encryption using KMS
- access controls using IAM policies

Message visibility - time after a consumer receives a message where it can read and process - this has a timeout 
Visibility timeout - SQS Visibility Timeout is a period of time during which Amazon SQS prevents other consumers from receiving and processing the message again. In Visibility Timeout, a message is hidden only after it is consumed from the queue.
Long polling - ??
FIFO queues - first in first out

## SNS - simple notification service
- one message to many receivers
- producer sends message to one SNS topic using SDK; consumers listen to SNS topic notifs


SNS + SQS fan out - publish SNS topic and SQS queues are subs which allows for data persistence.
This is a common pattern where only one message is sent to the SNS topic and then "fan-out" to multiple SQS queues. This approach has the following features: it's fully decoupled, no data loss, and you have the ability to add more SQS queues (more applications) over time.

JSON policy that filters messages according to SQS queues

## Kinesis
- collect, analyze and process data streams - basically realtime data

1. Kinesis data streams - streaming big data; data shards provisioned first; Kinesis Data Stream uses the partition key associated with each data record to determine which shard a given data record belongs to. When you use the identity of each user as the partition key, this ensures the data for each user is ordered hence sent to the same shard.
2. KInsesis data firehose - supports data transformations - takes data from sources and batch writes data to destinations (s3, redshift, opensearch, third party or custom destinations) and s3 backup buckets
Near relatime; data ingestion, nearly realtime, automatic scaling  

## Amazon MQ
- managed message broker for rabitmq and activemq
- doesnt scale as much as sqs/sns
- can run on multi AZ
- has queue feature and topic feature (~SNS)
- it uses EFS as storage for message data, persistent messages and durable subs

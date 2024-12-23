## CloudWatch metrics
- *Metric - variable to monitor
- *Dimensions - attribute of a metric (instance id for example)
- Metrics have timestamps
- Can stream these metrics through kinesis firehose or other places

### CW Logs
- collect, analyse and monitor log files
Log subscriptions - sends log events to different accounts
LIvetail - is a dashboard metric that records log events
Agents
Alarms - trigger notifs for any metric violations
EventBridge - cron jobs, react to event patterns, trigger lambda functions
Can intercept API calls
Container insights - collects and summarizes metrics and logs from containers to a dashboard
Lambda insights - troubleshooting solution for serverless apps on Lambda
Contributor insights - analyse logs and create time series data
Application insights - potential problems with monitored applications

## CloudTRail
- provides governance, compliance and audit for AWS accounts - enabled by default - can get history of events
- SDK, CLIs, Console, IAM roles and users can be inspected and audited using this by sending this to CW

## CloudTrail insights
analyse unusual activity, anomalies
Events retention - CT to s3 if you want to store them longer than 90 days then sent to Athena for analysis

## AWS Config
- helps audit and record compliance of AWS resources
- records changes
- Rules: managed/custom config rules

CW - performance metrics, alerting, log aggregation
CT - record API calls made within account by everyone, define trails for specific resources, global service
Config - record config changes, evaluate resources against compliance rules, get timeline of changes on config/compliance

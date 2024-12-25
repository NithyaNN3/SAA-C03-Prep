## Cloud Formation
- declarative way of outlining AWS infrastructure
- gets them running based on template declared
- automatically generates a diagram
- THINK **Infrastructure As Code**

Service role - IAM role given to CF to create/delete/modify resources

## Amazon Simple Email Service
- fully managed service to send emails regularly

## Amazon Pinpoint
- marketing emails, SMSes and 2-way comms (inbound/outbound)
- can do campaigns and templates which you cant do in SNS

## SSM Systems manager
- allows you to start a secure shell on your ec2 and on prem servers
- SSM agent in ec2 which is connected to Sessions manager

**System Manager Run command** - used to execute a document - can run on multiple instances
**System manager Patch manager** - automate patching/updates
**System manager Maintenance windows** - defines a schedule to perform actions on your instances
**SM Automation** - simplifies maintenance or deployment tasks
**Cost Explorer** - visualise, manage and understand AWS costs over time, can forecast too
**Cost Anomaly detection** - continuously monitor costs and usage using ML to detect unusual spends
**Outposts** - server racks basically that offer the same infra, tools, services to build your own apps on prem just as you do it on the cloud
**Batch** - batch processing service at any scale - basically a docker image that run on ECS to do these jobs
**AppFlow**- fully managed integration service that enables you to securely transfer data between SaaS and AWS
**Amplify** - web and mobile app tool > can connect code from git, etc
**Instance scheduler** - AWS solution through CF - automatically start/stop AWS services like when company is in out of biz hours

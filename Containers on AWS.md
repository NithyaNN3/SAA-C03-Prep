# Docker 
- way to run apps with OS
- docker images are stored in docker repositories
- resources are shared with host => many containers on one server
- Amazon ECR - container registry, ECS container service
- EKS - kubernetes services
- Fargate - serverless container platform

## Amazon ECS
- launch docker containers on AWS
- must provision and maintain the ec2 infra
- each EC2 instance must have an EC2 agent to register in the ECS cluster
- Can have IAM roles for ECS agents and ECS tasks
- ECS clusters support load balances
- data persistence using EFS
- Fargate + EFS -> serverless

**Auto Scaling** 
- AWS application auto scaling - CPU util, memory util, request per cout target
- target tracking, step scaling, scheduled scaling 

## Fargate 
- launch docker containers on AWS
- dont provision infra as it's all serverless
- create definitions > AWS runs the ECS tasks based on CPU/RAM
- increase tasks to increase scale

## Amazon ECR 
- ECS pulls images from here and runs in the clusters

## EKS
- Open source system for deployments
- EKS worker nodes run EKS nodes (EC2 instances) which have EKS pods (same as ECS but different names)

## AWS App Runner
fully managed service that makes it easy to deploy web apps with event logs, etc

## App2Container
migrating Java and .Net web apps to containers

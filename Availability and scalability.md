## Auto scaling groups
- load on an app or website can change quickly so you can create or get rid of servers quickly on the cloud
- Goal is to scale acc to load, ensure only the necessary amount instances are running at a time, automatically register new instances to LB, recreate an instance if one is unhealthy and terminated
- ASGs are free, you only pay for the EC2 instances
- can create a Launch template
- possible to scale based on CloudWatch alarm

**Scaling policies** 
1. Dynamic scaling - target tracking (eg. if you want ASG CPU to stay around 40%), simple/step scaling (CloudWatch is triggered)
2. Scheduled scaling - based on known usage patterns (Friday evenings have new users)
3. Predictive scaling - based on forecasts

Metrics:
- CPU utilisation
- RequestsCountPerTarget: requests on a instance for example
- avg network in/out
- custom metric

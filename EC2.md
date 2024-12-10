# Elastic Compute Cloud

- renting VMs (EC2)
- storing data on virtual drives (EBS)
- distributing load across machines (ELB)
- scaling services using auto scaling group (ASG)

### EC2 User data
- possible to bootstrap instances using EC2 user data
- bootstrapping means launching commands when a machine starts
- the script is run only during the first launch of the instance
- can update updates, softwares, download files
- runs with the root user
- example of instance - t2.micro, t2.xlarge

- instances are optimised for different use cases
  Sample name - m5.x2large

  m - instance class
  5 - generation
  2xlarge - size within instance class

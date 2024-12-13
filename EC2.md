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

### Security groups
- regulate access to ports
- authorise IP ranges
- control inbound and outbound traffic
- acts as a firewall
- maintain a separate SG for SSH
- app is not accessible, SG issue; app shows connection refused, SG has blocked

Important ports -
1. SSH - 22 - log into linux instance
2. 21 - FTP - upload files in file share
3. 22 - SFTP - Secure FTP - upload files using SSH
4. 80 - HTTP - unsecured websites
5. 443 - HTTPS - secured websites
6. 3389 - Remote desktop protocol - log into a windows instance

Update aws credentials to ec2 instances ONLY through IAM roles.

### EC2 purchasing types
1. On demand - short, pay by second
2. Reserved - 1 or 3 years - long and convertible
3. Savings plan - committed long term usage; 1 or 3 years
4. Spot instances - short term, less reliable; batch jobs, data analysis, etc
5. Dedicated host - book entire physical server; control instance placement; use if you have an app that needs licenses
6. Dedicated instances - reserved instances so that no other customer shares hardware
7. Capacity reserves - reserve capacity in specific AZ

### Spot requests
You can set price, instance limit, type of reserve, duration, which AZ you want to run it in

Public IP can be recognised across internet; Private IP only on certain network; Elastic IP  changes as per ec2 IP when it's restarted, they stay constant as opposed to public IPs as long as instance is running

### Placement groups
strategising how our ec2 placements are across aws
- cluster: in a low latency group in AZ; use case - low latency apps, high perf computing, distributed dbs or big data workloads needing high speed data exchange 
- spread: instances across different hardware; enhances fault tolerance and critical apps
- partition: across many partitions acc to groups; for large scale distributed systems

### Elastic networks interfaces
networking component - virtual network card attached to the ec2 instance - can use it to configure IP addresses, MAC addresses and security groups
Advantage is that you can move it from one IPv to another.
 -> Detach an ENI from a failed instance and reattach it to a standby instance for seamless recovery.
 -> Use multiple ENIs to separate application traffic, e.g., management traffic on one ENI and application traffic on another.
 -> Isolate monitoring or logging traffic on a separate ENI for better observability.

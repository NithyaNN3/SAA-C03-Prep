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

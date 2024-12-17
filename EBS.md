## Elastic Block Store
- attach to instances and allows for persisting data
- it's a network drive
- AZ wise
- Delete on Termination attribute

## EBS snapshots
- makes a backup of a volume at any point in time
- not necessary to detach volume to do a snapshot but recommended
- can copy snapshots across AZ or region
- you can also create a volume through a snapshot

**EBS snapshot archives** - move snapshot to archive tier which is 75% cheaper; takes 24-72 hours to restore the archive

**Recycle bin for EBS snapshots** - setup rules to retain deleted snapshots; specify retention

**Fast snapshot restore** - force full initialisation of snapshot to have no latency on first use but costs a lot of money

## AMI (Amazon machine image)
- customisation of ec2 - add your own software, OS
- faster boot since software is prepackaged

## EC2 Instance store
- network drives with good but limited perf
- high perf hardware disk
- better i/o perf
- once stopped, data lost
- hardware fail, data lost
- make sure to backup

## EBS volume types
6 types
1. gp2/gp3 (ssd) - general purpose ssd volume that balances price and perf - 1GB to 16TB 
- io1/io2 block express (ssd) - highest perf ssd for low latency or high throughput workloads - great for database workloads
- st1 (hdd) - low cost hdd volume for frequently accessed, throughput intensive workloads, sc1(hdd) - lowest cost hdd volume designed for less freq accessed workloads - big data warehousing, log processing

## EBS Multi attach - io1/io2 family
- same ebs volume to multiple ec2 instances
- each instance has full read and write permissions to high perf volume
- high application availability
- 16 instances at a time

## EBS Encryption
- data encrypted in volume
- data movement between volume and instance is encrypted
- snapshots encrypted
- volumes encrypted
- transparent encryption/decryption
- encryption has minimal impact on latency
- EBS encryption leverages keys from KMS key(AES256)
- copying unencrypted snapshot allows encryption

- create ebs snapshot > encrypt > create new ebs volume from snapshot > attach encrypted volume to original instance

## EFS Elastic File System
Managed NFS (network file system) mounted on ec2
works with ec2 instances in many AZ
highly available, scalable and expensive
Storage tiers - lifecycle policies can be set to move them across tiers

## Elastic load balancer
- servers that forward traffic to multiple servers (ec2 instances) downstream
- spreads loads to manage traffic
- exposes single points of access (DNS)
- provide SSL for websites
- LBs can run health checks on ec2 instances to know if traffic can be forwarded

## Application load balancer 
- layer 7 only (http)
- route requests based on target groups (based on endpoints), hostname in URL, based on query strings/headers
- great for microservices and container based apps
- port mapping feature to redirect to dynamic port

## Network load balancer
- forward TCP and UDP requests to instances
- handle multiple requests; super low latency
- one static IP per AZ and allows assignment of elastic IP
- extreme perf, tcp or udp use cases
- Target groups - EC2 instances, IP addresses, ALBs

## Gateway load balancer
- 3rd party network appliances
- FIrewalls, intrusion detection, deep packet inspection, etc
- basically filters and redirects traffic to app only when it's deemed to be safe

## Sticky sessions
- is a way to redirect a client to the same load balancer each time
- works with classic, application and network LBs
- cookies used here; have an expiry date
- used to make sure session data isnt lost
- 2 types of cookies - application based cookies and duration based cookies

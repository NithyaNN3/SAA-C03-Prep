## Snowcone
- device to collect and process data in an edge location
- offline devices to perform data migrations - offline data transfer
- Edge computing - process data when it's created on an edge location
- Use cases - ML, preprocessing data
- snowball to s3 then lifecycle policy to migrate to glacier

### FSx
- 3rd party high perf file systems
- OpenFS and Windows

### Hybrid cloud
AWS pushing for part of infra on cloud and part on-prem
AWS Storage gateway - bridge between on prem and cloud data - means you need on prem virtualisation; user comms through NFS/SMB > file gateway with local cache > storage gateway
S3 file gateway
FSx file gateway - SMB clients 

### AWS Transfer family
- FTP file transfers in/out of s3 or EFS but don't want to use NFS just FTP protocol- FTP, SFTP FTPS
- highly available, scalable, reliable

### DataSync
- synch large data to or from places - s3, efs, FSx
  - on prem to AWS - needs agent
  - AWS to AWS
- repl tasks can be scheduled
- file perms can be stored

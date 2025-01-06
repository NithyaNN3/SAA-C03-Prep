## Disaster Recovery in AWS
- Any event that has a negative impact on company
- DR is preparing for and recovering from the disaster

- Types:
    - on prem to on prem
    - on prem to cloud
    - cloud to cloud
- RPO: recovery pt objective - basically how often you run backups. Time b/n RPO and disaster is data loss.
- RTO - how much time to recover. Time b/n disaster and RTO is downtime

- Strategies
- 1. Backup and restore: high RPO
  2. Pilot Light: small version of app is always running in cloud. Useful for critical core. Faster than b&r as critical systems are running already. Low rpo, low rto
  3. Warm standby: full system up and running but min size.
  4. Multi site/hot site approach: very low rto, full prod scale app is running AWS and on prem.
 
  ## Database Migration Server
  - migrate database from on prem to cloud
  - continuous data repl
  - must create a ec2 instance to perform repl tasks
 
  - If source db and target db dont have same engine? **AWS schema conversion tool**
  - First we replicate schema to to convert schema from one engine to another on RDS, then we perform data migration using DMS

  RDS MySQL to Aurora MySQL
  Option 1: DB snapshots from RDS restored on Aurora
  Option 2: Create read replica from RDS and when repl lag is 0, promote it as its own DB cluster
  Option3: External: percona xtrabackup or use mysqldump utility
  Option4: if both are running, use DMS

  ## AWS Backup
  full managed service to automate backups
  - no need to create manual scripts/ manual processes
  - supports cross region/cross account backups
  - create **Backup plans** which has details of backups
  - Vault lock - backups cant be deleted even by root users
 
  ## AWS Application Discovery Service
  On prem to cloud migration, you need server utilisation data and dependency mapping which are important for migrations.
  Agentless discovery, agent-based discovery - can see on AWS migration hub
  **App Migration Service** - executes migrations to run natively on AWS


  

## Encryption
TLS/SSL - in flight encryption
Server side encryption
Client side encryption

## KMS - Key Mgmt Service 
manages encryption keys for us
- fully integrated with IAM
- able to audit KMS key usage using CloudTrail
- KMS keys - symmetric (AES -256), asymmetric keys (RSA & ECC key pairs)
- AWS owned keys (free), AWS managed keys (free), customer managed keys (paid)
- EBS volume encrypted with key has same key with snapshot but you cannot have same key in another region so you have to reencrypt it
- **Key Policies** - JSON based policy doc which defines perms for using a key - needs primary access control info of who can manage or use the key
- Multi region keys - identical KMS keys in different AWS regions
**Dynamodb global tables and KMS multi region client side encryption**
  - if we need to encrypt certain attributes on table so that it's accessed only by client
  - client encrypts an attribute using MRK
  - data will be replicated as it's a global table
  - once table is repl in another region, the local KMS can make an API call to the client app to decrypt it
  - can do this with Aurora also
 
## S3 replication encryption considerations
- unencrypted and objects encrypted with SSE-S3 are replicated by default
- objects encrypted with SSE-C can be repl
- for SSE-KMS, you need to enable the option
- can use multi region AWS KMS keys but they are treated as independent keys by S3

## Encrypted AMI sharing process
- AMI encrypted with KMS key
- must modify launch perm to the specified target AWS account
- share the KMS key with key policy
- target account needs IAM role with perms to encrypt, decrypt and describe key

## SSM parameter store
- secure storage for configs and secrets
- Eg: Apps can store plaintext configs so SSM checks IAM perms or encrypted configs which then checks with AWS KMS
- can use paths based on URL
- Parameter policies - assign TTL to a parameter

## AWS Secrets Manager
- newer service for storing secrets
- can replicate secrets across multiple regions

## AWS Certificate Manager
easy to provision and use TLS certs
inflight encryption for websites

## Web application firewall
- web app firewall basically against web exploits (layer 7)
- Web Access control lists - like which IPs are allowed, size constraints, geoblock, rate based rules
- WAF doesnt support for layer 4 exploits
- we can use Global accelerator to get fixed IP and then use WAF on the ALB

## Shield - DDoS protection
- DDoS attack - many reqs at once
- SHield protects against ddos
- Shield Advanced - against more sophisticated layer 4 attacks

## Firewall manager
- manage all rules across AWS accounts on the AWS Org
- WAF rules, security groups, DNS firewall, policies are at region level

**WAF, Shield and Firewall manager**
- used together for full protection
- ACL rules on WAF
- Firewall manager helps setup rules/configs on new resources
- Shield gives ddos attack protection

### Amazon GuardDuty 
What it is: A threat detection service that continuously monitors your AWS accounts and workloads for malicious or unauthorized activity. - Analyzes data sources such as VPC Flow Logs, CloudTrail Logs, and DNS logs.

### Inspector 
What it is: An automated security assessment service for applications hosted on AWS. Identify vulnerabilities and deviations from security best practices. Use Cases:
Assess EC2 instances for known vulnerabilities. 

### Macie
A data discovery and classification service that uses machine learning to protect sensitive data in S3 buckets. Purpose: Detect and secure sensitive information. Use Cases:
Ensure compliance with data protection regulations (e.g., GDPR, HIPAA),
Identify and secure sensitive data stored in S3.

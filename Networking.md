## CIDR, Public and private IP
classless interdomain routing - method for allocating IPs
- used in SGs and AWS networking generally
- CIDR has base IP and subnet mask (how many bits can change in the IP)
- Private IPs can allow only certain values
- IPs in the internet are public
  
  WW.XX.YY.ZZ/32 - only one IP but 0.0.0.0/0 -> all IPs but 192.168.0.0/26 -> 192.1688.0.0 to 192.168.0.63 (64 addresses)
  How does this work?
  - /8 means 255.0.0.0
  - /16 means 255.255.0.0
  - /24 means 255.255.255.0
  - /32 means 255.255.255.255
 
More samples - 
192.168.0.0/32 => allows for 1 IP change -> 192.168.0.0
192.168.0.0/31 => allows for 2 IP (2^1) -> 192.168.0.0, 192.168.0.1
192.168.0.0/30 => allows for 4 IP (2^2)
192.168.0.0/29 => allows for 8 IP(2^3)
192.168.0.0/28 => allows for 16 IP changes
192.168.0.0/27 => allows for 32 IP changes
and so on upto 
192.168.0.0/16 => allows upto 65,536 IP changes which is 192.168.0.0 to 192.168.255.255
and so on upto 
192.168.0.0/0 => allows for all IP changes -> 0.0.0.0/0 to 255.255.255.255

## VPC
VIrtual private cloud - can create instances and they can launch specific subnets
- 5 VPCs per region
- Subnets - range of private IPs
- 5 IP addresses are always reserved for network address, VPC router, mapping to DNS, future use, network broadcast address
- TIP: if you need 29 IP addresses, you cant choose a subnet of size /27 (32-5=27 < 29) but you can choose 26 (64-5 = 59 > 26)

## Internet gateway
- allow resources to connect to internet
- use a route table in subnet so that the router can access the internet

## Bastion hosts
-if us as users want to access instances in private subnets in a VPC
- we can use bastion hosts which is a ec2 instance with a public subnet
- USers > SSH into bastion host with SGs with restricted CIDR > SSH into private subnet

## NAT instances
Network Address Translation
- allows ec2 instances in private subnets to connect to internet - must have elastic IP
If we have a public server and we want to access it from a private subnet, there is a NAT instance in public subnet wth EIP. Private IP communicates to NAT instance which changes src IP before it enables comms to public server IP

## NAT Gateways
AWS managed NAT - pay per hour - created in specific AZ, uses EIP
- Requires IGW (private subnet => NATGW => IGW)
- enable multiple NAT gateways in multiple AZs for high availability

## NACL and SGs
NACL is extra level on subnet and SG outside of ec2 instance
- NACL inbound rules separate from SG inbound rules
- Default nACL: accepts everything inbound/outbound with subnets it's associated with
- clients connect to a defined port and get responses on ephemeral ports

- SG are instance level, NACL is subnet level
- SG is stateful (return traffic is automatically allowed), NACL is stateless (return traffic must be explicitly allowed by rules)
- SG allow rules only, NACL has allow/deny rules
- SG all rules are evald, NACL rules are evald in priority
- apples to a ec2 instance when specified by somebody, NACL applies to all ec2 instances in a subnet

## VPC Peering
- privately connect two VPCs to make them behave as if they're in the same network - for comms between them
- must NOT have overlapping CIDRs

## VPC endpoints
- to be able to access a service through the private AWS network instead of the public internet
- Types of endpoints: interface (provisions ENI as an entry point; costs money) and gateway (provisions a gateway ad must be used as a target in a route table; free)
- Gateway or interface? Prefer gateway as you only need to change route tables except some cases

## VPC Flow Logs
- capture IP traffic info
- monitor and troubleshoot connectivity
- make it using Athena on S3 or CW logs insights

Troubleshooting - look at the ACTION field - remember that NACL is stateless and SG is stateful

## Site to Site VPN
if we want comms between a data center and VPC > establish conn with customer gateway, VPN gateway and s2s conn
- virtual private gateway and customer gateway

## Direct Connect (DX)
- dedicated prvate conn from a remote network
- you need to setup virtual private gateway > access resources

## Transit gateway
- transitive peering between thousants of VOC on prem

## Egress gateway
An Egress Gateway is a specialized network component or proxy that manages and controls outbound traffic from a network, service mesh, or application. It acts as a controlled exit point for data leaving an internal environment to external systems.

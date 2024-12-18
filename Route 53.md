## DNS
**Domain Name System** - hostnames to IPs; backbone of internet
- Domain registrar that registers
- DNS records and zone files that have DNS records
- Name server that resolves DNS queries
- top level domain like .us, .au, etc
- Second level domain like google.com, amazon.com

## Route 53
- highly managed and authoritative DNS
- is a domain registrar
- ability to check health
- Records specify how you want to route traffic for a domain
- each record has - domain/subdomain name, record type, value, routing policy, etc

Record types -
A - maps to ipv4
AAAA - maps to ipv6
CNAME - maps hostname to another hostname
NS - name servers for hosted zones

Public hosted zones allow anybody on the internet to query my records but in a private hosted zone, we allow only queries from within a VPC

**Records TTL(Time To Live)** - amount of time that a record is cached before it queries the authoritative DNS again for updated info; can be high or low
Short is used when quicker propagation of changes is needed so frequent checks are also needed. (60s)
Long is for stable records that rarely change like static websites (1 day). Reduces DNS query traffic.

**Difference between CNAME and Alias**
CNAME points hostname to hostname and works on only non root domain
Alias oints hostname to AWS resource; works for root name and non root name; free of charge; have a native health check; cannot set TTL here; targets are ELBs, CLoudFront dist., API gateway, S3 websites, etc

**Route 53 Routing Policies** - routing here is a specific host with IP. If many are returned by a host, a random one is chosen
1. Simple
2. Weighted - can assign % of traffic
3. Latency based - redirect based on latency; based on traffic and proximity to AWS region

### Health Checks
health checkers from different regions check a resource's health; you can set which region's health checkers ping the resource and set how many need to be passed;
Health checks on private resources - can be done by creating a CloudWatch metric and associating a CW alarm then create a health check that checks the alarm itself.

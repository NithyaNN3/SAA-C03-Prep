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

A - maps to ipv4
AAAA - maps to ipv6
CNAME - maps hostname to another hostname
NS - name servers for hosted zones

Public hosted zones allow anybody on the internet to query my records but in a private hosted zone, we allow only queries from within a VPC

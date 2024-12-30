## CloudFront
- CDN
- content is cached for improving read perf
- DDoS protected, Shield protected, Firewall
- Edge location serves content from an origin (like s3 bucket)
- global edge network
- files cached for TTL
- improves perf for dynamic content + cache 

S3 cross origin repl - great for read only or dynamic content with low latency access

### ALB or EC2 as origin
- EC2, ALB need to be public
- Cloudfront access the public IPs

**CF geo restriction** - can mark which countries are to be allowed access
**Pricing:** - cost of data per edge location varies; can be separated by price classes
**Cache validations** - when you update a backend, you can refresh cache entirely so that TTL also has the updated content when main page is refreshed

### Global Accelerator
- is content access needed globally? content needs to hop between multiple servers increasing latency
- unicast IP - one server has one IP; anycast IP - all servers have same ip so content hops to the closest ip - GA uses anycast
- improves perf for tcp, udp; HTTP use cases with static IP; non-HTTP use cases like gaming or voice over IP

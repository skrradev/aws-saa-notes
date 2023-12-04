# ALB vs NLB vs GLB


| Feature                      | ALB (Application Load Balancer)   | NLB (Network Load Balancer)       | GLB (Gateway Load Balancer)           |
|------------------------------|-----------------------------------|-----------------------------------|---------------------------------------|
| OSI Layer                    | Layer 7 (Application Layer)       | Layer 4 (Transport Layer)         | Layer 3 (Network Layer)               |
| Protocols Supported          | HTTP, HTTPS                       | TCP, UDP, TLS                     | All protocols routed at IP level      |
| Routing                      | Content-based (path, host, header)| IP protocol data                  | IP protocol data                      |
| Load Balancing to            | EC2 Instances, IP Addresses, Lambda, Containers | EC2 Instances, IP Addresses, Containers | Virtual Appliances (e.g., Firewalls)  |
| SSL/TLS Termination          | Yes                               | Yes (TLS Listener)                | No (Handled by appliances)            |
| Static IP                    | No                                | Yes (Elastic IP)                  | Yes (Elastic IP)                      |
| Health Checks                | Advanced (HTTP/HTTPS)             | Basic (TCP, TLS)                  | Basic (TCP, UDP)                      |
| Stickiness                   | Yes (Session-based)               | No                                | No                                    |
| WebSockets                   | Yes                               | Yes                               | Not applicable                        |
| HTTP/2                       | Yes                               | No                                | Not applicable                        |
| Path-based Routing           | Yes                               | No                                | No                                    |
| Request Tracing              | Yes                               | Yes                               | Not typically used                    |
| Preserving Source IP         | No                                | Yes                               | Yes                                   |
| High Availability            | Across multiple AZs               | Across multiple AZs               | Across multiple AZs                   |
| Use Cases                    | Microservices, web applications   | High performance, static IP needed| Security appliances, traffic inspection|


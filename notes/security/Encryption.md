# Encryption

| Feature                       | Encryption in Transit (In Flight) | Server-Side Encryption at Rest | Client-Side Encryption |
|-------------------------------|-----------------------------------|--------------------------------|------------------------|
| **Where It Happens**          | Data is encrypted as it travels   | Data is encrypted on the server | Data is encrypted by   |
|                               | across the network                | before being stored on disk     | the client before      |
|                               |                                   |                                | being sent to the server|
| **Control**                   | Managed by network protocols like | Managed by the storage service  | Managed directly by    |
|                               | TLS/SSL                           | (e.g., Amazon S3)               | the client             |
| **Encryption Keys**           | Managed by the communicating      | Keys are managed by the service | Keys are managed by    |
|                               | parties, often transparently      | provider, with options for      | the client, increasing |
|                               |                                   | customer-provided keys          | control and            |
|                               |                                   |                                | responsibility         |
| **Common Protocols/Tools**    | HTTPS, FTPS, SSH, TLS             | AES-256, AWS KMS, AWS S3 SSE    | GPG, OpenSSL, custom   |
|                               |                                   |                                | client applications    |
| **Access to Unencrypted Data**| Only possible during transit,     | Data is encrypted until it is   | Data remains encrypted |
|                               | typically protected by secure     | accessed by an authorized       | until decrypted by the |
|                               | network channels                  | entity or service               | client                 |
| **Use Cases**                 | Protecting data as it moves       | Protecting data from unauthorized| Protecting sensitive   |
|                               | between clients and servers,      | access while stored on persistent| data before it ever   |
|                               | such as web browsing, file        | storage                          | leaves the client's    |
|                               | transfer, and email communication |                                  | environment            |
| **Key Management Complexity** | Moderate, handled by established  | Low to moderate, with encryption | High, requires client  |
|                               | network security protocols        | options provided by the service  | management of keys     |
|                               |                                   | provider                         | and encryption process |
| **Visibility**                | Transparent to the end-user       | Transparent to the end-user,     | Requires user          |
|                               |                                   | unless customer-managed keys are | involvement for       |
|                               |                                   | used                             | encryption/decryption  |
| **Performance Impact**        | Minimal, as modern systems are    | Minimal to moderate, depending   | Can be significant     |
|                               | optimized for in-transit encryption| on the service and encryption   | depending on the       |
|                               |                                   | type chosen                      | encryption method used |


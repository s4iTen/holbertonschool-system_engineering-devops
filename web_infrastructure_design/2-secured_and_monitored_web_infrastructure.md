# Three-Server Web Infrastructure Design

To meet the specified requirements, a three-server web infrastructure will be designed to host the website www.foobar.com. The infrastructure will be secured, serve encrypted traffic over HTTPS, and include monitoring capabilities. The components of the infrastructure include:

- 3 servers
- 3 firewalls
- 1 SSL certificate for serving www.foobar.com over HTTPS
- 3 monitoring clients (data collectors for Sumologic or other monitoring services)

## Infrastructure Design

The following design elements are incorporated to address the requirements and enhance the infrastructure:

### 1. Servers

Three servers are added to the infrastructure to provide redundancy, improve performance, and enable fault tolerance. By distributing the workload across multiple servers, the infrastructure becomes more resilient to single points of failure and ensures continuous availability of the website.

### 2. Firewalls

Firewalls are included to enhance the security of the infrastructure. They act as a barrier between the servers and external networks, allowing only authorized traffic to pass through and blocking potential threats. The firewalls monitor and control incoming and outgoing network traffic, protecting the servers from unauthorized access and potential attacks.

### 3. SSL Certificate

An SSL certificate is implemented to serve www.foobar.com over HTTPS. HTTPS encrypts the communication between the web server and the user's browser, ensuring the confidentiality and integrity of data transmitted over the network. The SSL certificate validates the authenticity of the website and establishes a secure connection, building trust with users and protecting sensitive information.

### 4. Monitoring Clients

Monitoring clients, such as data collectors for Sumologic or other monitoring services, are integrated into the infrastructure. These monitoring tools collect data related to server performance, resource utilization, error logs, and other metrics. Monitoring helps in identifying and resolving issues proactively, ensuring the availability, performance, and security of the infrastructure.

## Specifics of the Infrastructure

- **Terminating SSL at Load Balancer Level**: Terminating SSL at the load balancer level poses an issue because it requires the load balancer to decrypt and re-encrypt the traffic. This adds additional processing overhead to the load balancer and can impact its performance. It is advisable to offload SSL termination to dedicated servers or utilize SSL acceleration hardware for improved efficiency.

- **Single MySQL Server Accepting Writes**: Having only one MySQL server capable of accepting writes introduces a single point of failure for write operations. If the MySQL server fails or experiences downtime, write operations will be affected, leading to potential data inconsistency and service disruptions. Implementing a replication setup with a primary node for writes and replica nodes for reads can ensure better availability and fault tolerance.

- **Identical Components on Servers**: Deploying servers with all the same components, including the database, web server, and application server, can lead to a lack of redundancy and scalability. If a critical component fails on one server, it can impact the entire system. Introducing diversity in the infrastructure, such as separate database servers, load balancers, or cache servers, can improve fault tolerance, scalability, and overall resilience.

## Monitoring Web Server QPS

To monitor the web server's queries per second (QPS), the following steps can be taken:

1. Utilize a monitoring tool or software that provides QPS metrics for the web server.
2. Configure the monitoring tool to collect data specifically related to the web server's QPS.
3. Set up appropriate thresholds and alerts to notify administrators when the QPS exceeds or falls below predefined limits.
4. Regularly analyze and review the QPS data to identify patterns, anomalies, and potential performance issues.
5. Take necessary actions based on the analysis, such as optimizing server configurations, scaling resources, or implementing caching mechanisms to handle high QPS loads efficiently.

## Infrastructure Issues

1. **Terminating SSL

 at Load Balancer Level**: Terminating SSL at the load balancer level can impact the load balancer's performance due to additional processing overhead.

2. **Single MySQL Server Accepting Writes**: Having only one MySQL server capable of accepting writes introduces a single point of failure and can lead to potential data inconsistencies and service disruptions.

3. **Identical Components on Servers**: Deploying servers with all the same components can limit redundancy, scalability, and fault tolerance. A failure in a critical component on one server can affect the entire system.

Addressing these issues involves implementing solutions such as SSL offloading, database replication, and introducing diverse components in the infrastructure for improved reliability and performance.
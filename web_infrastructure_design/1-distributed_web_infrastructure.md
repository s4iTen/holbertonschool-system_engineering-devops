# Distributed Web Infrastructure

![Distributed Web Infrastructure](https://github.com/Soniabensaad/holbertonschool-system_engineering-devops/blob/main/web_infrastructure_design/1-1distributed_web_infrastructure.png)

## Requirements

This infrastructure requires the following components:

- 2 additional servers
- 1 web server (Nginx)
- 1 application server
- 1 load balancer (HAproxy)
- 1 set of application files (code base)
- 1 database (MySQL)

## Description of the Infrastructure

1. **Servers**

   Two additional servers are included in the infrastructure to distribute the workload and provide redundancy. These servers handle incoming requests, improving performance and reliability.

2. **Web Server (Nginx)**

   The web server, Nginx, receives HTTP requests from users' browsers. It listens on port 80 and handles the initial processing of the requests. It retrieves the requested resources and sends the response back to the users' browsers.

3. **Application Server**

   The application server runs the code base of the website. It processes dynamic content, executes server-side code, and interacts with the database. It communicates with the web server to generate the appropriate response.

4. **Load Balancer (HAproxy)**

   The load balancer, HAproxy, acts as an intermediary between users and the web/application servers. It distributes incoming requests across multiple servers using a specific distribution algorithm. The load balancer improves performance and scalability by evenly distributing the workload.

5. **Database (MySQL)**

   The database, MySQL, stores and manages the website's data. It persists and retrieves information for dynamic content. The application server communicates with the database to perform data operations.

## Specificities of the Infrastructure

- **Load Balancer Distribution Algorithm**: The HAproxy load balancer can be configured with different distribution algorithms, such as round-robin, minimum number of connections, or IP-hash. The chosen algorithm determines how requests are distributed among the available servers.

- **Load Balancer Configuration**: The load balancer is configured with a distribution algorithm, such as round-robin or least-connection. Round-robin distributes requests evenly in a cyclic manner among the available servers.

- **Primary-Replica Database Cluster**: The database cluster is set up using the Primary-Replica (Master-Slave) model. The primary node (master) handles write operations, while the replicated nodes (slaves) handle read operations. Data is asynchronously replicated from the primary node to the replicated nodes to ensure data consistency and availability.

- **Difference between Primary and Replica Nodes**: The primary node is responsible for writing and updating the database. It is used by the application for write requests. The replicated nodes are used for read operations and serve as a backup in case of primary node failure. They ensure high availability and improve performance by distributing read operations among the replicated nodes.

## Potential Infrastructure Problems

1. **Single Point of Failure (SPOF)**:

   Each component of the infrastructure can become a single point of failure. Failure of a server, load balancer, or database can lead to service interruption or unavailability of the website.

2. **Security Issues**:

   The current infrastructure lacks firewalls, making it vulnerable to attacks and intrusions. It is recommended to add a firewall to control network traffic and protect servers from potential threats.

   Additionally, the absence of HTTPS (secure HTTP) exposes communication between users and the web server to the risk of data breach. Implementing HTTPS is essential to secure exchanges and protect data confidentiality.

3. **Lack of Monitoring**:

   The infrastructure lacks a monitoring system. It is recommended to implement a monitoring system to track performance, detect problems and failures, and take preventive or corrective measures.

To

 address these issues, a new web infrastructure will be designed to host the website www.foobar.com. The new infrastructure will consist of:

- 2 servers
- 1 web server (Nginx)
- 1 application server
- 1 load balancer (HAproxy)
- 1 set of application files (code base)
- 1 database (MySQL)

The design will consider the following aspects:

- The purpose and rationale for each additional element
- The distribution algorithm used in the load balancer and its functioning
- The setup of the load balancer (Active-Active or Active-Passive) and an explanation of the difference between the two
- How the Primary-Replica (Master-Slave) cluster works for the database
- The distinction between the Primary node and the Replica node in relation to the application
- Identification of single points of failure, security issues, and lack of monitoring in the current infrastructure
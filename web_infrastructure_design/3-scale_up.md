# Single Server Web Infrastructure Design

To meet the specified requirements, a single server web infrastructure will be designed. The infrastructure will include the following components:

- 1 server
- 1 load balancer (HAproxy) configured as a cluster
- Split components (web server, application server, database) with their own server

## Infrastructure Design

The design of the infrastructure is as follows:

### 1. Server

A single server is added to the infrastructure to host the web application. It will serve as the primary server for handling incoming requests, running the web server, application server, and database components.

### 2. Load Balancer (HAproxy)

A load balancer (HAproxy) is incorporated into the infrastructure. It is configured as a cluster with the other load balancer, providing redundancy and fault tolerance. The load balancer distributes incoming requests across multiple servers to ensure efficient load handling and improve performance.

### 3. Split Components

The components of the web infrastructure (web server, application server, database) are split into separate servers. This separation enhances modularity, scalability, and fault tolerance. Each component can be individually scaled or modified without affecting the other components.

- Web Server: A dedicated server is assigned to host the web server, which handles the initial processing of HTTP requests, retrieves resources, and sends responses back to users' browsers.

- Application Server: Another dedicated server is allocated to run the application server. It processes dynamic content, executes server-side code, and interacts with the database. It communicates with the web server to generate appropriate responses.

- Database: The database is hosted on its own server. It stores and manages the website's data, persisting and retrieving information for dynamic content. The application server communicates with the database to perform data operations.

## Additional Element Justification

- Load Balancer: The load balancer is added to ensure efficient distribution of incoming requests across multiple servers, improving performance and handling scalability.

- Split Components: Separating the web server, application server, and database into their own servers allows for modularity, scalability, and fault tolerance. It enables independent scaling and modification of each component without affecting the others.

## Conclusion

The single server web infrastructure, with a load balancer configured as a cluster and split components, provides the necessary foundation for a scalable and resilient system. The inclusion of a load balancer ensures even distribution of requests, while separate servers for each component allow for independent scaling and fault tolerance.
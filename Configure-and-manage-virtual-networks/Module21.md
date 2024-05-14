# Module:21 Configure Azure Application Gateway

## Azure Application Gateway

- Layer 7 load balancer.
-  a load balancer for web traffic.
-  used to manage traffic to the web apps.
-  listens for incoming traffic to web apps and checks for messages sent via protocols like HTTP.
-  Gateway rules direct the traffic to resources in a back-end pool.
-  can redirect traffic received at one listener to another listener, or to an external site. This approach is commonly used by web apps to automatically redirect HTTP requests to communicate via HTTPS to ensure the communication occurs over an encrypted path.
-  can rewrite HTTP headers.HTTP headers allow the client and server to pass parameter information with the request or the response.  URLs or query string parameters can be translated, and  request and response headers can be modified.
-  allows to create custom error pages instead of displaying default error pages

### Benefits of application Gateway

- Application layer Routing: direct traffic to a back-end pool of web servers based on the URL of a request.
- Session stickiness: ensure client requests in the same session are routed to the same back-end server.
- Round robin load balancing: Client requests are forwarded in a cycle through a group of servers to create an effective balance for the server load.
- Supported protocols: support the HTTP, HTTPS, HTTP/2, or WebSocket protocols.
- encryption: end-to-end request encryption for the web applications.
- load autoscaling: Dynamically adjust capacity as the web traffic load changes.
- firewall protection: can implement web application firewall to protect against web application vulnerabilities.

Two primary methods for routing traffic:

1. __Path-based routing__ sends requests with different URL paths to different pools of back-end servers.

![path-based-routing-15bcef5f](https://github.com/anuja2015/AZ-104/assets/16287330/34fa6c7c-2279-4e89-9c13-4e8735ebb5e8)

2. __Multi-site routing__ configures more than one web application on the same application gateway instance.
Register multiple DNS names (CNAMEs) for the IP address of the application gateway and specify the name of each site. Application Gateway uses separate listeners to wait for requests for each site. Each listener passes the request to a different rule, which can route the requests to servers in a different back-end pool.

![site-based-routing-e686b605](https://github.com/anuja2015/AZ-104/assets/16287330/08700851-bf01-4a18-a556-6993cfb0a4ae)

## Application Gateway components

__Front-end IP address__ : receives the client requests.

__Web Application Firewall__(Optional) : checks incoming traffic for common threats before the requests reach the listeners.

__Listeners__ : one or nore to receive the traffic and route the requests to the back-end pool.

__Routing rules__ : define how to analyze the request to direct the request to the appropriate back-end pool.

__Back-end pool__ : contains web servers for resources like virtual machines or Virtual Machine Scale Sets. Each pool has a load balancer to distribute the workload across the resources.

__Health probes__ : determine which back-end pool servers are available for load-balancing.


![configure-app-gateway-0193dbd6](https://github.com/anuja2015/AZ-104/assets/16287330/8dafc1f4-5795-46bf-b069-8c2e5f0b6896)






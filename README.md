# Load Balancer in AWS
Load Balancer | ALB/NLB/GLB | 
## Load Balancing in AWS
Load balancing is the method of distributing network traffic equally across a pool of resources that support an application. Modern applications must process millions of users simultaneously and return the correct text, videos, images, and other data to each user in a fast and reliable manner. To handle such high volumes of traffic, most applications have many resource servers with duplicate data between them. A load balancer is a device that sits between the user and the server group and acts as an invisible facilitator, ensuring that all resource servers are used equally.
## There are three types of Load balancers used in the cloud:
1.	Application load balancer (ALB) - Operates at Layer 7 (Application layer) of the OSI model.
2.	Network load balancer (NLB) - Operates at Layer 4 (Transport layer) of the OSI model.
3.	Gateway load balancer (GLB) - Operates at Layer 3 (Network layer) of the OSI model.


## Benefits of load balancing:
1. Application availability.
2. Application scalability.
3. Application security.
4. Application performance.

## 1.	Application load balancer (ALB):
Ideal for HTTP/HTTPS traffic, microservices, and container-based applications.
•	ALB uses a round-robin algorithm by default, routing traffic one after another. Suppose there are three servers S1, S2, S3 then the first request goes to S1, the second request goes to S2, the third request goes to S3, the fourth request goes back to S1 and so on.

How it works:

An Application Load Balancer (ALB) distributes incoming application traffic across multiple targets, such as EC2 instances, containers, or IP addresses, within one or more Availability Zones.
<img width="940" height="431" alt="image" src="https://github.com/user-attachments/assets/feffba56-05c1-4908-a6be-93272a340961" />


### **Scenario: Suppose there is an eCommerce company having its own application**

- **Client Request:** A user sends a request (e.g., opening a website).  
- **Listener:** The ALB listener checks the incoming request on a specific port.  
- **Rule Evaluation:** The listener applies routing rules to decide where to send the request.  
- **Target Group:** The ALB forwards the request to a target group — a set of registered targets (EC2 instances, containers, etc.).  
- **Health Checks:** ALB continuously checks the health of each target and sends traffic only to healthy ones.  
- **Response:** The selected target processes the request and sends the response back through the ALB to the client.  

ALB intelligently routes client requests to healthy targets based on rules, ensuring high availability, scalability, and efficient traffic management.


## 2.	Network load balancer (NLB):
Handles TCP, TLS, UDP, and TCP_UDP traffic.

NLB uses a flow hash algorithm so that traffic is routed to specific targets in a predetermined manner.

How it works:

NLBs distribute traffic based on network conditions. For example, if you have multiple database servers with duplicate data, the NLB routes traffic based on predetermined server IP addresses or server availability.
The NLB monitors the health of its registered targets and routes traffic only to the healthy targets. After the load balancer receives a connection request, it selects a target from the target group for the default rule. It attempts to open a TCP connection to the selected target on the port specified in the listener configuration. Each individual TCP connection is routed to a single target for the life of the connection. Similarly, you can also route a UDP flow consistently to a single target throughout its lifetime. 

## 3.	Gateway load balancer (GLB):
GLB uses routing table look-ups to determine where to route the traffic. 

With a GLB, you can deploy, manage, and scale virtual appliances, such as intrusion detection and prevention, firewalls, and deep packet inspection systems. It creates a single entry and exit point for all appliance traffic and scales your virtual appliances with demand. You can also use it to exchange traffic across virtual private cloud (VPC) boundaries. 
In the GLB, you establish rules using route tables. Depending on the rules that you set up, it selects different target groups to forward traffic to. It receives IP packets and forwards traffic to specific target groups.

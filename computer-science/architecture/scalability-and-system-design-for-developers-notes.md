# Scalability and system design for developers' notes

## Web architecture

**HTTP protocol:** Stateless request-response protocol. [Overview if needed.](https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview)

**REST API:** Software architectural style for implementing web services. Acts as an interface. REST also enables servers to cache the response which improves the app's performance. Allows decoupling clients and the backend service.

An example of coupling of backend and client code is JSP.

**HTTP PULL:** Default mode. Client pulls data from the server whenever required. The request needs to be done again for updates. Two ways of pulling/fetching data:

* Single HTTP GET request
*   Pulling data dynamically at regular intervals using AJAX.(polling)

    <figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

    TTL: Time To Live for every request. If the client does not receive a response from the server within the TTL, the browser kills the connection.

**HTTP PUSH:** Client sends a request for certain information to the server just once. After the first request, the server keeps pushing the new updates to the client whenever they are available. Also called _callback_. Common example: User notifications.

* Persistent connection
* Heartbeat interceptors: Blank request responses between the client and the server to prevent the browser from killing the connection. This is resource-intensive.
* Techniques:
  * Web sockets: Persistent bi-directional low latency data flow. E.g: Messaging, social streams, browser-based massive multiplayer games. Don't work over HTTP but TCP. [More info](https://developer.mozilla.org/en-US/docs/Web/API/WebSockets\_API)
  * AJAX  - long polling: Instead of immediately returning the empty response, server holds the response until an update occurs. Fewer requests than regular polling.&#x20;
  * HTML5 Event-source API and Server-sent events: Server automatically pushes the data to the client when updates are available. Incoming messages from the server are treated as events after an initial request. After initial request, communication is unidirectional, server to client. Use cases: Real-time Twitter feed, displaying stock quotes, real-time notifications. [More info.](https://developer.mozilla.org/en-US/docs/Web/API/Server-sent\_events)
  * Streaming over HTTP: When is needed to stream extensive data by breaking it into smaller chunks. Works using HTML5 and JS Stream API. Primarily for multimedia content. [More info.](https://developer.mozilla.org/en-US/docs/Web/API/Streams\_API/Concepts)

## Scalability

Scalability is the application's ability to handle and withstand increased workload without sacrificing performance.

**Latency:** The time a system takes to respond to a user request. If the latency remains the same, we can say that the application scaled well with the increased load and is highly scalable.

Latency can be divided in:

* Network latency (to optimize, use a CDN)
* Application latency

### Types of scalability

#### Vertical (or scaling up)

More power to the server.

Simpler, takes much less administrative, monitoring, and management efforts. Downside: availability risk. If a server goes down the entire site crashes.

#### Horizontal (or scaling out)

More servers. Also allows us to scale dynamically in real-time as the traffic on our website climbs and drops over a period of time. High availability option.

The code needs to be stateless. No static instances on the class. Functional programming.

For consisting state application-wide, redis and memcache are the solution.

The process of adding and removing servers, stretching and returning to the original infrastructural computational capacity, on the fly is popularly known as _cloud elasticity_.

### Scalability bottlenecks

* **Database:** Solutions? database patitioning, sharding.
* **Application design:** Not using asynchronous processes and modules.
* **Not using caching in the application wisely**
* **Inefficient configuration and setup of load balancers**
* **Adding business logic to the database**
* **Not picking the right database:** Relational, NoSQL
* **At the code level**

_DENTTAL_ (Documentation, Exception Handling, Null pointers, Time complexity, Test coverage, Analysis of code complexity, Logging)

### Test the scalability

**How to test:** Stress and load tests.

**System parameters to take into account:**

* CPU usage
* Network bandwidth consumption
* Throughput
* Number of requests processed within a stipulated time
* Latency
* Memory usage of the program
* End-user experience when the system is under heavy load and so on.

Monitor it: cAdvisor, Prometheus, Grafana

### Tuning the performance of the application

* Profiling
* Caching
* CDN
* Data compression
* Avoid unnecessary request-response cycles

## High availability

is the ability of the system to stay online despite having failures at the infrastructural level in real time. Ensures minimum downtime.

**Reasons for downtimes?**

* Software crashes
* Hardware failures
* Human errors
* Planned downtime

**Fault tolerance:** System’s ability to stay up despite taking hits.

For high availability use microservices (granular loosely coupled services).

Upsides of microservices over monolith?

* Easy management and maintenance
* Ease of development
* Ease of adding new features to a service without affecting other services
* Scalability and high availability of the system

### Redundancy

Duplicating the server instances and keeping them on standby to take over in case any of the active server instances go down. It is the fail-safe backup mechanism in the deployment infrastructure. This eliminates single points of failure.

### Replication

Having a number of similar nodes running the workload together. There are no standby or passive instances.

### High available cluster

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption><p>All the possible components having a single point of failure are made redundant to ensure the availability of the service</p></figcaption></figure>

**RAID:** Redundant array of independent disks

## Load balancing

Load balancers enable our service to scale well and stay highly available when the traffic load increases. Load balancers distribute heavy traffic load across the servers running in the cluster based on several different algorithms.

While processing a user request, if a server goes down, the load balancer automatically routes the future requests to other up-and-running server nodes in the cluster.

Can be used as a single point of contact for all client requests or at the application component level to efficiently manage traffic directed towards any application component.

Load balancers perform regular health checks of the servers to ensure availability.

## DNSs

Every online machine has a unique IP address that enables it to be contacted by other machines. DNSs are systems that translate domain names to IPs.

### Components of a DNS

* DNS Recursive nameserver aka DNS Resolver (generally managed by the ISP)
* Root nameserver
* Top-Level Domain nameserver
* Authoritative nameserver

### DNS query lookup process

1. Browser sends a request to the _DNS Recursive nameserver._
2. _DNS Recursive nameserver_ forwards it to the _Root nameserver_
3. _Root nameserver_ gest the address of the _Top-level domain nameserver._ Top-level domain addresses like _.com_.
4. _DNS Recursive nameserver_ (aka _DNS Resolver_) sends a request to the top-level domain nameserver to fetch the details of the domain name.
5. _Top-level domain nameserver_ returns IP address of the domain name server (aka _Authoritative nameserver_).
6. DNS resolver queries Authoritative nameserver and it returns the IP address of the website.
7. DNS resolver caches the data and sends it to the browser.

Cache at almost every layer (local machines, DNS resolver)

### DNS load balancing

Is set up at the DNS level on the _authoritative server_. Enables the authoritative server to return a list of IP addresses of a particular domain to the client. With every request, the server the server changes the order of the IP addresses in the list using round-robin.

DNS load balancing is used by companies to distribute traffic across multiple data centers.

Limitations:

* Does not take into account the current load on the servers, content, request processing time, in-service status, and so on.
* IP addresses are cached by the client's machine and the DNS resolver, there's always a possibility of a request being routed to a machine that is out of service.

### Load balancing methods

* **DNS Load Balancing**
* **Hardware-based Load Balancing:** Sit in front of the application servers and distribute the load based on the number of currently open connections to a server, compute utilization, and several other parameters. More expensive than the software ones, have to be overprovisioned upfront to deal with peak traffic, harder and more expensive to maintain but with better performance overall.
* **Software-based Load Balancing:** Can be installed on commodity hardware and VMs. More cost-effective and flexible, easier to maintain. Consider many parameters such as data hosted by the servers, cookies, HTTP headers, CPU and memory utilization, network load, etc. Also, perform regular health checks. Can use Round robin (sequential), weighted round robin (sequential taking into account compute and traffic handling capacity), least connections (weighting or not the requests), random, hash (using the same server per client) algorithms

## Monolith vs Microservices

* **Monolith:**
  * **Pros:** Simplicity
  * **Cons**: CD is hard, regression testing is often necessary, is a single point of failure, scalability is a challenge, cannot leverage heterogeneous technologies, not cloud-ready.
* **Microservices:**
  * **Pros:** Single responsibility and separation of concerns,&#x20;
  * **Cons:**

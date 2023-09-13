# Scalability and system design for developers' notes

## Web architecture

**HTTP protocol:** Stateless request-response protocol. [Overview if needed.](https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview)

**REST API:** Software architectural style for implementing web services. Acts as an interface. REST also enables servers to cache the response which improves the app's performance. Allows decoupling clients and the backend service.

An example of coupling of backend and client code is JSP.

**HTTP PULL:** Default mode. Client pulls data from the server whenever required. The request needs to be done again for updates. Two ways of pulling/fetching data:

* Single HTTP GET request
*   Pulling data dynamically at regular intervals using AJAX.(polling)

    <figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

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


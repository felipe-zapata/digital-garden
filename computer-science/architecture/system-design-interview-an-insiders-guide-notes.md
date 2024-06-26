# System design interview: An insiders guide notes

## Chapter 1: Scale from zero to millions of users

* Databases:
  * Relational db:&#x20;
    * Stores data on tables and rows
    * Join operations using SQL
  * Non-relational db (NoSQL):
    * Four categories
      * Key-value stores
      * Graph stores
      * Column stores
      * Document stores
  * For most applications relational is better and would be the default option. When choosing NoSQL?
    * Required super-low latency
    * Unstructured data
    * You only need to serialize and deserialize data
    * Massive amount of data
  * Vertical scaling vs horizontal scaling:
    * Vertical: Add more power. Simpler. No failover/redundancy.
    * Horizontal: Add more servers
  * DB  replication:
    * Master/slave relationship. A master for writing, a slave for reading. Slave DB gets copies from master DB.
    * Better performance
    * Reliability
    * High availability
    * If slave fails, traffic is redirected to other slaves
    * If master fails, a slave is promoted to master
* Load balancer (web tier):
  * Communicates with servers inside its network with private IPs for security reasons.
  * Redirects traffic to the servers connected.
  * Solves no-failover issues and improves availability
  * If traffic grows, just add more servers
* Cache
  * Temporary data store layer
    * Gets data from DB and stores it on memory
    * On request, if data exists serves, if not requests to db and serves (read-through cache)
  * Considerations:
    * Data is read frequently but modified infrequently
    * Expiration policy
    * Consistency
    * Mitigate failures, have multiple cache servers
    * Eviction policy. Least-recently used or least-frequently used, or first in first out, is removed if full.
* CDN
  * Deliver static content (images, js, videos, css, ...)
  * Servers closer to the client
  * TTL (time to live)
  * "Cache on the edge"
  * Considerations:
    * Cost
    * Setting an appropriate cache expiration time (TTL)
    * CDN fallback
    * Invalidating files
      * Remove with API
    * Versioning
* Stateless (review)
* \




* Single server setup (web app, database, cache, etc.)
* Web tier server, data tier (database) server



## Chapter 2: Back-of-the-envelope estimation

Latency and availability numbers

## Chapter 3: A framework for system design interviews

1. Understand the problem and establish the design scope
   * What specific features are we going to build?
   * How many users does the product have?
   * How fast does the company anticipate to scape up?
   * What is the company's technology stack?
2. Propose high-level design and get buy-in
3. Design deep dive
4. Wrap up

## Chapter 4: Design a rate limiter


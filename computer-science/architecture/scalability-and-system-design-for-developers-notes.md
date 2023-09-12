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
*   Techniques:

    * Web sockets: Persistent bi-directional low latency data flow. E.g: Messaging, social streams, browser-based massive multiplayer games. Don't work over HTTP but TCP. [More info](https://developer.mozilla.org/en-US/docs/Web/API/WebSockets\_API)
    * AJAX  - long polling: Instead of immediately returning the empty response, server holds the response until an update occurs. Fewer requests than regular polling.&#x20;
    * HTML5 Event-source API and Server-sent events: Server automatically pushes the data to the client when updates are available. Incoming messages from the server are treated as events after an initial request. After initial request, communication is unidirectional, server to client. Use cases: Real-time Twitter feed, displaying stock quotes, real-time notifications. [More info.](https://developer.mozilla.org/en-US/docs/Web/API/Server-sent\_events)
    * Streaming over HTTP: When is needed to stream extensive data by breaking it into smaller chunks. Works using HTML5 and JS Stream API. Primarily for multimedia content. [More info.](https://developer.mozilla.org/en-US/docs/Web/API/Streams\_API/Concepts)

